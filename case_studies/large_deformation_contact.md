# Case Study: Plasticity Succeeded, Contact Struggled — Lessons from a Multi-Framework Computational Mechanics Project

**How a bilayer scroll simulation pushed through four frameworks, five contact methods, and dozens of dead ends — and what it reveals about the limits of AI-assisted numerical research.**

---

## 📖 Table of Contents

- [Overview](#overview)

**Part I — The Scientific Journey**
- [1. The Problem: Bilayer Scroll Formation](#1-the-problem-bilayer-scroll-formation)
- [2. What Succeeded: Large-Deformation Plasticity](#2-what-succeeded-large-deformation-plasticity)
- [3. What Struggled: Contact Mechanics](#3-what-struggled-contact-mechanics)
- [4. The Framework Migration Path](#4-the-framework-migration-path)

**Part II — Technical Lessons**
- [5. The Eigendecomposition NaN Saga](#5-the-eigendecomposition-nan-saga)
- [6. Thermal Expansion: A Subtle Scaling Bug](#6-thermal-expansion-a-subtle-scaling-bug)
- [7. The Spatial Hash Detour](#7-the-spatial-hash-detour)
- [8. Force Limiters: Per-Pair Is Not Enough](#8-force-limiters-per-pair-is-not-enough)
- [9. Caching Contact Forces Injects Energy](#9-caching-contact-forces-injects-energy)
- [10. Implicit Contact Is Inherently Hard](#10-implicit-contact-is-inherently-hard)

**Part III — Collaboration Patterns**
- [11. Where AI Added Value](#11-where-ai-added-value)
- [12. Where AI Wasted Time](#12-where-ai-wasted-time)
- [13. The Human's Critical Contributions](#13-the-humans-critical-contributions)
- [14. Correcting a Common Misconception About AI-Proposed Ideas](#14-correcting-a-common-misconception-about-ai-proposed-ideas)

- [Summary](#summary)

---

## Overview

This project aimed to simulate a bilayer strip that curls into a multi-turn scroll through differential thermal expansion, developing self-contact between wrapped layers. The scroll formation involves large deformation hyperelasticity, self-contact, and frictional sliding. It sits at the intersection of constitutive modeling, contact mechanics, and GPU-accelerated scientific computing.

The project touched four computational frameworks (FEniCSx, JAX, Taichi, ABAQUS), attempted five different contact formulations, and generated working plasticity implementations in three of them. The plasticity work succeeded cleanly; the contact work was a prolonged struggle that eventually converged but required the human to force multiple paradigm shifts.

ABAQUS served as the reference throughout, reliably producing the expected scroll formation. The goal was to reproduce this in open-source frameworks suitable for GPU acceleration.

---

# Part I — The Scientific Journey

---

## 1. The Problem: Bilayer Scroll Formation

The bilayer scroll is deceptively simple to describe: a bilayer strip curls through differential thermal expansion, eventually forming self-contact as the layers wrap around each other. But the simulation is challenging because it combines large deformation, evolving self-contact with topology changes, frictional sliding between layers, and stiffness contrast between the two materials. These challenges interact — each one is manageable in isolation, but their combination pushes numerical methods to their limits.

---

## 2. What Succeeded: Large-Deformation Plasticity

The plasticity work — implementing large-deformation constitutive models in both FEniCSx and JAX — succeeded remarkably well. Three implementations were produced, each with different trade-offs.

### Implementation 1: FEniCSx + JAX Hybrid

The most successful approach combined FEniCSx for the global finite element problem (mesh, function spaces, assembly, boundary conditions, Newton solver) with JAX for the constitutive model (stress computation, consistent tangent via autodiff). The iterative matrix functions (Denman-Beavers for square root, scaling-and-squaring for logarithm) provide stable autodiff through the logarithmic strain computation.

**Key validation:** The JAX autodiff tangent matched the Richardson-extrapolated finite difference tangent to machine precision, confirming both the forward computation and the derivative.

### Implementation 2: FEniCSx + Numba

A parallel implementation used Numba-JIT-compiled kernels for the constitutive update, with finite difference tangent computation inside the compiled kernel. The FD tangent was more robust for edge cases near the identity matrix, but autodiff was significantly faster and scaled better.

### Implementation 3: Pure FEniCSx/UFL (Struggled)

An attempt to implement everything in UFL (FEniCSx's symbolic form language) using DG tensor fields for internal variables encountered persistent convergence failures. The staggered scheme diverged because the partial tangent — treating DG fields as constants during differentiation — pointed in the wrong direction.

**Lesson:** Implicit plasticity with history variables stored in DG fields requires the tangent to account for the dependence of stress on displacement through the constitutive update. UFL's `derivative()` cannot capture this dependency when the update is performed outside the form. The hybrid approach (FEniCSx for global, JAX/Numba for local) correctly separates these concerns.

---

## 3. What Struggled: Contact Mechanics

Contact was the project's persistent difficulty. Five different formulations were attempted across three frameworks before a working solution emerged.

### Attempt 1: Implicit IPC in FEniCSx (Failed)

The first approach integrated IPC barrier contact into FEniCSx's implicit Newton solver. The IPC barrier energy is smooth and differentiable, which should make it ideal for implicit methods.

**Why it failed:** The Newton solver could not converge when contact forces were comparable to elastic forces. The contact stiffness κ must be large enough to prevent penetration but not so large that it dominates the tangent matrix. Finding this balance was fragile — κ too large made the system ill-conditioned; κ too small allowed penetration. The lack of a good initial guess for the contact configuration compounded the problem.

### Attempt 2: IPCTK Library in FEniCSx (Failed)

The IPC Toolkit provides robust contact detection with CCD (continuous collision detection) and automatic barrier stiffness selection. Integration with FEniCSx was attempted but never reached stable multi-turn scrolling. The implicit solver's convergence difficulties persisted — better contact detection doesn't solve the fundamental convergence problem.

### Attempt 3: Mortar Contact in Taichi (Partial Success)

A segment-to-segment mortar contact formulation was implemented in Taichi. The contact detection and force computation were correct for simple test cases.

**Where it failed:** The thermal expansion implementation had a subtle bug — the material parameters must be properly scaled when using multiplicative decomposition of the deformation gradient. Without this scaling, the bending moment is too small and the scroll doesn't form properly. This bug was discovered only after comparing against ABAQUS.

### Attempt 4: Explicit IPC in JAX (Success — Eventually)

The working solution used explicit Verlet time integration with IPC barrier contact computed every step. The key ingredients:

- **Dense O(N²) contact detection.** All vertex-edge pairs are checked every step. This sounds expensive but runs efficiently on GPU because the dense broadcast fuses into a single high-throughput kernel.
- **Adaptive activation.** During the elastic-only phase (before surfaces approach), contact is skipped entirely. Contact switches on when the minimum distance drops below a threshold.
- **Per-node force clamping.** The maximum contact force per node per step is limited to prevent the barrier from producing forces that cause element inversion.
- **Friction from current velocity.** Coulomb friction is computed from the current relative velocity at each step, not cached from previous configurations.

### Attempt 5: Spatial Hash Contact in JAX (Failed, Then Reverted)

An optimization attempt replaced dense O(N²) contact with spatial hashing to reduce pair count. This was the AI's suggestion and consumed multiple days.

**Why it failed:** See Section 7 below.

---

## 4. The Framework Migration Path

The project's migration through frameworks is itself a lesson:

```
FEniCSx (implicit)  →  Failed on contact convergence
        ↓
Taichi (explicit)   →  Partial success, thermal expansion bug
        ↓
JAX (explicit)      →  Success after multiple contact iterations
        ↓
ABAQUS (reference)  →  Used throughout for validation
```

**Why JAX won over Taichi:** JAX's functional programming model (pure functions, immutable arrays, `lax.scan` for batched time stepping) produced more debuggable code than Taichi's imperative kernel model. When contact forces caused instability, JAX's deterministic execution made it possible to trace exactly which pair produced the problematic force. Taichi's atomic operations and mutable fields made this harder.

**Why explicit won over implicit:** For this problem class (large deformation, dynamic contact, topology changes), explicit time integration avoids the convergence difficulties that plagued every implicit attempt. The cost is small timesteps (CFL-limited), but the per-step cost is low and GPU parallelism keeps wall-clock time manageable.

---

# Part II — Technical Lessons

---

## 5. The Eigendecomposition NaN Saga

The most instructive debugging episode in the project. The JAX constitutive model needed matrix square roots and logarithms for the logarithmic strain tensor. The AI proposed eigendecomposition — mathematically correct, and the standard approach in textbooks.

**The failure:** Near the identity matrix (small deformation), eigenvalues are nearly repeated. The gradient of the eigendecomposition involves terms 1/(λ_i − λ_j) that produce NaN when eigenvalues coincide. The forward computation worked fine; only the gradient was broken.

**The AI's failed fixes:**
1. SVD instead of eigendecomposition → same problem (repeated singular values)
2. Regularization (perturb eigenvalues) → unreliable, problem-dependent
3. Custom JVP with implicit function theorem → didn't converge

**The working fix (human-forced pivot):** The human said: "Stop. Propose a fundamentally different method that avoids eigendecomposition entirely." The AI then proposed Denman-Beavers iteration for square root and scaling-and-squaring for logarithm — iterative methods that use only matrix multiplication, addition, and solve. These operations have universally stable derivatives. The NaN problem disappeared completely.

**Why the human had to force this:** The AI kept proposing variations within the eigendecomposition paradigm because each variant was "more robust" than the last. The human recognized that the paradigm itself was flawed for autodiff and forced a complete change of approach.

**The validation that proved it worked:** The human had a Richardson-extrapolated finite difference code that computed tangents independently. When the iterative-method tangent matched the FD tangent exactly, both the forward computation and the autodiff were validated simultaneously.

---

## 6. Thermal Expansion: A Subtle Scaling Bug

In the Taichi bilayer implementation, thermal expansion was initially implemented as a simple scaling of the deformation gradient using the standard multiplicative decomposition.

**The bug:** When using multiplicative decomposition for thermal expansion in hyperelasticity, the material parameters in the energy function must also be properly transformed — not just the deformation gradient. Without this scaling, the bending moment is too small and the scroll doesn't form properly.

**How it was caught:** Comparison against ABAQUS. The ABAQUS reference showed the expected scroll formation; the Taichi code significantly under-predicted the curling. After fixing the material parameter scaling, the results matched.

**Lesson:** Thermal expansion in multiplicative hyperelasticity is not just "divide F by the expansion factor." The energy function's material parameters must also be transformed. This is well-known in the continuum mechanics literature but easy to miss in implementation, and the AI got it wrong on the first attempt.

---

## 7. The Spatial Hash Detour

This is the clearest example of the AI wasting time on an optimization that made things worse.

**The setup:** Dense O(N²) contact detection ran at a reasonable speed on GPU. The AI proposed spatial hashing to reduce the pair count.

**The implementation:** A full spatial hash was built in JAX: hash grid construction via argsort, neighbor lookup via searchsorted, candidate pairs via vmap gather. The pair count dropped significantly.

**The result:** The spatial hash version was substantially *slower* than dense — roughly 7× slower despite evaluating far fewer pairs.

**Why:** GPU thrives on coalesced memory access. Dense broadcast achieves this perfectly: all threads read the same data. Spatial hash requires irregular memory operations (argsort, searchsorted, gather) that destroy coalescing. Fewer FLOPs didn't compensate for worse memory throughput.

**The honest accounting (from the AI after the failure):**

> "I should have flagged this uncertainty when I delivered the code instead of presenting it with confidence. Fast generation ≠ correctness."

> "What we should have done: taken the original dense code, added adaptive activation + force limiters, and stopped. That was a 2-hour task, not a multi-day detour."

**The lesson:** Spatial hash likely beats dense above a certain problem size, but at the scale we were working at, dense was faster. The AI presented the optimization with confidence despite having no empirical basis for the performance claim.

---

## 8. Force Limiters: Per-Pair Is Not Enough

An early stability fix limited the maximum force per contact pair to prevent the barrier from producing extreme forces at very small gaps. This seemed to work — until it didn't.

**The failure mode:** A single node could be involved in 14 active contact pairs simultaneously (when tightly wound). Each pair's force was within the per-pair limit, but the accumulated force on the node was 14× the limit. This produced accelerations large enough to invert elements.

**The fix:** Per-node force clamping in addition to per-pair. After accumulating all contact forces on each node, clamp the total to prevent any node from moving more than a fraction of the contact distance per step.

**Why the AI didn't catch this initially:** The AI implemented per-pair limiting because that's what the IPC literature describes. The per-node accumulation problem only appears with dense contact where many pairs can hit the same node — a geometry-dependent issue that requires running the simulation to observe.

---

## 9. Caching Contact Forces Injects Energy

To speed up the spatial hash approach, contact geometry (nearest edges, distances) was cached and reused for several steps, with only the velocity-dependent friction recomputed each step.

**The bug:** When a node's velocity reverses direction (e.g., bouncing off a contact surface), the cached friction force continues pushing in the old direction for several steps. This acts like a one-way pump: the friction adds energy when velocity reverses, but doesn't remove it when velocity continues. Over thousands of steps, this caused runaway kinetic energy growth.

**The fix:** Never cache contact forces across timesteps. Compute everything from the current configuration each step. The friction force must depend on the current velocity, and the normal force geometry must reflect the current positions.

**Lesson:** Any contact scheme that reuses previous-step information for force computation risks energy injection. This is a fundamental issue with explicit contact, not a bug in the specific implementation.

---

## 10. Implicit Contact Is Inherently Hard

Every implicit contact attempt in this project failed to achieve robust multi-turn scrolling. The pattern was consistent:

1. First contact activates → Newton converges (barely)
2. Contact zone grows → condition number deteriorates
3. Topology change (new layer wraps around) → Newton diverges
4. Reduce timestep → helps temporarily, then fails at next topology change

**Why explicit succeeded where implicit failed:** Explicit dynamics avoids the global nonlinear solve entirely. Contact forces are computed from the current configuration and applied as external forces. The stability condition (Δt < CFL limit) is restrictive but predictable. There are no convergence failures — only numerical stability, which is controlled by the timestep and force limiters.

**This is a well-known result** in the contact mechanics community, but the AI initially pushed implicit methods because they are "more efficient for quasi-static problems." For this problem class (large deformation, dynamic contact, topology changes), implicit methods' efficiency advantage is negated by convergence failures.

---

# Part III — Collaboration Patterns

---

## 11. Where AI Added Value

**Rapid framework prototyping.** The AI generated working FEniCSx, JAX, and Taichi implementations of the same constitutive model within days. This allowed rapid comparison of frameworks without the human needing to learn each one from scratch.

**Constitutive model derivation.** The Mandel stress, logarithmic strain, and consistent tangent derivations were produced correctly by the AI. The human verified them against textbook references (Chester UMAT notes, Simo computational inelasticity).

**Literature awareness.** The AI identified relevant contact methods (IPC from Li et al., mortar from Puso & Solberg, Ando 2024 cubic barrier) and could compare their trade-offs. This saved substantial literature search time.

**Systematic debugging.** When the eigendecomposition NaN appeared, the AI generated a sequence of diagnostic scripts that isolated the failure to repeated eigenvalues, tested each matrix operation independently, and verified the fix. The structured diagnostic approach was faster than the human debugging alone.

---

## 12. Where AI Wasted Time

**The spatial hash detour.** Multiple days spent implementing, debugging, and then reverting a spatial hash that was slower than the original dense code. The AI presented the optimization with confidence despite having no empirical basis for the performance claim at this problem size.

**Repeated attempts at implicit contact.** The AI proposed implicit IPC, then IPCTK, then implicit mortar contact — each time believing the new formulation would solve the convergence problem. The human eventually had to force the pivot to explicit dynamics.

**The pure UFL plasticity attempt.** Multiple sessions were spent trying to make the staggered UFL scheme converge, with the AI proposing increasingly complex tangent augmentation strategies (blending with Neo-Hookean, alpha-scaling). The fundamental issue — that UFL's `derivative()` cannot capture the dependency of stress on displacement through an external constitutive update — was architectural, not fixable by parameter tuning.

**API hallucination in FEniCSx.** Multiple sessions hit runtime errors from hallucinated API signatures: `from dolfinx.io import gmshio` (v0.8 syntax), `u.eval()` return shape assumptions, `create_vector(form)` instead of `create_vector(function_space)`. Each required a run-traceback-fix cycle.

---

## 13. The Human's Critical Contributions

**"The code is working. Please make corrections when you see real errors."** This instruction — given at the start of the Taichi contact integration — prevented the AI from rewriting working code. The human's insistence on minimal, targeted modifications preserved the validated elastic solver while adding contact.

**"The changes are too many at a time. Let's do incremental updates."** When the AI proposed wholesale code restructuring, the human redirected to incremental changes with testing between each. This caught the thermal expansion scaling bug early, before it was buried under layers of contact code.

**"Shall we use JAX for IPC?"** The human proposed the framework that ultimately worked. The AI had been generating FEniCSx implicit code; the human recognized that JAX's autodiff + explicit dynamics was a better fit for the contact problem.

**"You probably misunderstood the speed."** When the AI claimed the spatial hash was "5× faster," the human ran the benchmark and reported the actual numbers (7× slower). The AI then acknowledged the failure honestly and proposed reverting.

**Comparison against ABAQUS.** The human ran ABAQUS reference simulations throughout, providing ground truth for scroll turn count, displacement fields, and force magnitudes. Without this anchor, the AI-generated code could have produced plausible-looking but wrong results.

---

## 14. Correcting a Common Misconception About AI-Proposed Ideas

It is tempting to attribute scientific ideas to whichever agent first articulated them in the conversation. But the actual origin of an idea is often more nuanced.

**Example: Cross-field connection in computational mechanics.** A cross-field connection was initially described as an AI-proposed idea. In reality, the human already knew that two subfields could be connected — that's why both documents were shared in the same session. The AI's contribution was identifying the specific technical evidence that the connection was viable. The *connection* was human-initiated; the *evidence for feasibility* was AI-contributed.

**Example: Explicit dynamics for contact.** The human proposed using JAX for IPC after implicit methods repeatedly failed. The AI had been proposing increasingly sophisticated implicit methods. The *paradigm shift* was human-driven; the *implementation* was AI-generated.

**The accurate framing:** AI is most valuable not when it proposes ideas from scratch, but when it rapidly evaluates and develops ideas that the human initiates. The human provides the creative direction and constraints; the AI provides rapid feasibility analysis, implementation, and systematic comparison. Attributing the "idea" to the AI overstates its creative role; attributing only the "code" to the AI understates its analytical contribution.

---

## Summary

This project demonstrates two contrasting patterns in AI-assisted computational research:

**When it works well (plasticity):** The mathematical formulation is well-established, the implementation maps cleanly to the framework's strengths (JAX for autodiff, FEniCSx for FEM), and the validation is clear (FD tangent check, ABAQUS comparison). The AI generates correct code quickly, the human validates efficiently, and progress is steady.

**When it struggles (contact):** The problem requires integration of multiple subsystems (detection, force computation, friction, time integration), the correct approach is not obvious in advance (implicit vs. explicit, dense vs. sparse), and failures are subtle (energy injection from caching, per-node accumulation, thermal scaling). The AI generates plausible code that fails at scale, proposes optimizations that make things worse, and keeps trying variations within a failed paradigm. The human must force paradigm shifts, run benchmarks, and maintain a reference solution.

**The meta-lesson:** AI-assisted research is fastest when the problem decomposes into well-understood components with tractable numerics. It is slowest when the problem involves fundamental numerical difficulties that no implementation trick can bypass. For the contact problem, the working combination of methods was only discovered after trying and failing with several alternatives. The AI could not have predicted the correct combination in advance — it had to be found empirically through the human running simulations and evaluating competing approaches.

**Why contact was harder for AI than plasticity — beyond the numerics:** For plasticity, many high-quality open-source implementations exist (FEniCSx tutorials, UMAT examples, textbook codes). AI has seen good plasticity code and can anchor to it. For contact, the best implementations are locked inside commercial codes (ABAQUS, LS-DYNA). Open-source contact codes tend to be poorly documented or limited to simple cases. AI has far fewer high-quality contact examples to learn from, which compounds the already difficult numerical challenges. Sharing working contact code with AI during development — even a simple two-body penalty example — significantly improves the quality of AI-generated extensions, because AI can anchor to tested code rather than reconstructing from sparse training data. More broadly, the scarcity of high-quality open-source contact code affects both AI's training and its ability to help implement complicated contact algorithms. This is one area where open-source contributions have an outsized impact.

```
The progression that matters:

PLASTICITY:  Formulation known, convergence tractable
             → AI implements → Human validates → Done
             (weeks, smooth)

CONTACT:     Formulation known, but convergence is inherently hard
             → AI implements → Human tests → Doesn't converge
             → AI implements alternative → Still doesn't converge
             → Human forces framework pivot
             → AI implements → Human tests → Partially works
             → Iterate on details → Eventually works
             (months, painful)
```

The difference is not in the AI's capability — it generated equally competent code for both. The difference is in the problem's numerical difficulty: plasticity has well-behaved convergence that the AI can implement straightforwardly; contact with large deformation and topology changes pushes methods to their limits regardless of how fast they can be implemented and tested.

---

---

## Acknowledgements

The bilayer scroll project is a collaboration with Prof. Lining Yao's Morphing Matter Lab. The large-deformation plasticity work benefited from discussions with Prof. Lallit Anand (MIT), Prof. Shawn Chester (NJIT), and Prof. Eric M. Stewart (University of Cincinnati).

---

*This case study documents work on the bilayer scroll simulation during 2025–2026, spanning FEniCSx, JAX, Taichi, and ABAQUS. The contact mechanics remains an active area of development.*

**Version:** 1.1
**Last Updated:** March 2026
