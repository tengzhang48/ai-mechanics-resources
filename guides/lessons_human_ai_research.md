# Lessons from Human-AI Collaboration in Computational Research

**A practitioner's field guide, drawn from a year of AI-assisted development of computational mechanics software (CoupMPM, CoupLB, and others).**

---

## 📖 Table of Contents

- [Overview](#overview)

**Part I — Can AI Do Science?**
- [1. The Synthesis Catalyst](#1-the-synthesis-catalyst)
- [2. Cross-Field Connections and Feasibility Analysis](#2-cross-field-connections-and-feasibility-analysis)
- [3. What AI Cannot Do: Taste, Constraints, and Pivots](#3-what-ai-cannot-do-taste-constraints-and-pivots)
- [4. The Honest Taxonomy of AI's Scientific Contributions](#4-the-honest-taxonomy-of-ais-scientific-contributions)

**Part II — Numerical and Algorithmic Lessons**
- [5. AI Can Be Confidently Wrong at Edge Cases](#5-ai-can-be-confidently-wrong-at-edge-cases)
- [6. Always Have Independent Validation](#6-always-have-independent-validation)
- [7. Prototype in Simple Tools, Then Port](#7-prototype-in-simple-tools-then-port)
- [8. Unit Conversion Bugs Are Recurring and Subtle](#8-unit-conversion-bugs-are-recurring-and-subtle)
- [9. MPI Correctness Requires Ownership Thinking](#9-mpi-correctness-requires-ownership-thinking)

**Part III — Software Engineering with AI**
- [10. The Iterative Debugging Loop](#10-the-iterative-debugging-loop)
- [11. Complete Files Over Incremental Patches](#11-complete-files-over-incremental-patches)
- [12. API Version Hallucination Is the #1 Code Bug](#12-api-version-hallucination-is-the-1-code-bug)
- [13. "Makes It Compile" ≠ "Makes It Correct"](#13-makes-it-compile--makes-it-correct)
- [14. LAMMPS-Specific Pitfalls](#14-lammps-specific-pitfalls)
- [15. File Consolidation and Code Architecture](#15-file-consolidation-and-code-architecture)

**Part IV — Project Management and Process**
- [16. Context Management Is a First-Class Problem](#16-context-management-is-a-first-class-problem)
- [17. Triaging AI Reviewer Feedback](#17-triaging-ai-reviewer-feedback)
- [18. Document AI Mistakes as You Go](#18-document-ai-mistakes-as-you-go)
- [19. When to Force a Change of Approach](#19-when-to-force-a-change-of-approach)
- [20. AI Model Upgrades Change the Game](#20-ai-model-upgrades-change-the-game)

- [Summary: The Collaboration Model That Works](#summary-the-collaboration-model-that-works)

---

## Overview

This document summarizes lessons from approximately one year of AI-assisted development on multiple computational mechanics packages:

- **CoupMPM** — Material Point Method package for LAMMPS (soft-matter/cell mechanics)
- **CoupLB** — Lattice Boltzmann Method + Immersed Boundary Method for LAMMPS (fluid-structure interaction)
- **Additional projects** — JAX-based computational mechanics pipelines and LAMMPS-based lattice models (details withheld for ongoing publications)

The work involved C++ for LAMMPS internals, Python/JAX for constitutive modeling and post-processing, MPI parallelization, and substantial use of AI for code generation, debugging, code review, documentation, scientific reasoning, and research direction planning.

The most important and subtle question this document addresses is: **Can AI contribute to scientific discovery?** The answer, based on our experience, is nuanced — and more interesting than either "yes" or "no."

---

# Part I — Can AI Do Science?

---

## 1. The Synthesis Catalyst

The debate over whether AI can "do science" often frames it as a binary: either AI generates genuinely novel hypotheses, or it merely executes human instructions. Our experience suggests a third category that is more accurate and more useful: **AI as synthesis catalyst**.

The pattern works like this: the human possesses deep expertise in specific domains but cannot hold all possible cross-connections in working memory simultaneously. The AI has broad and balanced knowledge across many fields — potentially as deep as the best literature on any specific topic, but without strong priors about what matters for the specific problem at hand — and can rapidly enumerate combinations. When the human provides domain-specific pieces, the AI connects them in ways the human hadn't considered — not because the connections are beyond human capability, but because the combinatorial search is faster.

**This is not the same as "just autocomplete."** The connections often require understanding the mathematical structure of both domains well enough to recognize compatibility. But it is also not the same as generating a novel hypothesis from first principles. It is closer to what a well-read postdoc does in a brainstorming session: they know enough about adjacent fields to say "have you considered that your problem X is structurally similar to problem Y in field Z?"

The key question is not "Did the AI invent this?" but rather "Would this connection have been made without the AI, and how much sooner did it happen because of the AI?"

---

## 2. Cross-Field Connections and Feasibility Analysis

Here are specific examples from our work where the AI contributed to scientific reasoning. For each, we carefully note what the human initiated, what the AI contributed, and whether the idea survived validation. The attribution matters — see Section 14 of the bilayer scroll case study for a deeper discussion.

### Example 1: Cross-Field Connection in Computational Mechanics

The human had developed a computational mechanics framework. The human already suspected that this framework could be connected to an established optimization methodology from a different subfield — that's why both documents were shared with the AI in the same session. The connection itself was human-initiated.

What the AI contributed was rapid feasibility analysis: identifying the specific technical evidence that the connection was viable. The AI recognized that the human's framework solved a longstanding boundary representation problem in the optimization methodology, and identified several specific capabilities this enables that no existing method in that subfield can handle.

- **Human's contribution:** The creative connection ("these two should work together"), the domain expertise to evaluate feasibility, and the push to verify the technical foundations ("Let's first make sure everything works").
- **AI's contribution:** The feasibility evidence — identifying precisely *why* the connection was viable and what it enables. The AI also honestly assessed what was NOT novel (the framework reduces to standard methods for a common special case) and redirected toward the regime where it genuinely adds capability.
- **Outcome:** Validated. Under development for publication.

**This distinction matters for the broader debate about AI and scientific discovery.** It is tempting to attribute an idea to whichever agent first articulated it formally. But the human sharing both documents in one session was itself the creative act — it defined the search space. The AI searched within it efficiently but did not define it.

### Example 2: Unified Virtual Boundary Framework for Multiphysics MPM

The CoupMPM development plan included separate boundary condition methods for mechanical traction (VSB), thermal flux (VHFM), and fluid coupling (IBM). The human noted that boundary conditions are a known weakness of MPM and suggested focusing there. The AI recognized that all three methods share the same mathematical structure: they all use virtual fields defined in an auxiliary domain near the non-conforming material surface, and they all require the same surface geometry (density gradient, surface normal, Nanson scaling).

- **AI's contribution:** The unification — "these are all the same framework applied to different fields." The AI proposed a single virtual boundary infrastructure that handles all three physics simultaneously, which no existing MPM paper has done.
- **Human's contribution:** The strategic insight that boundary conditions are underexplored and publishable, the domain knowledge to evaluate whether the unification is mathematically sound, and the judgment that this should be a separate paper from the methods paper.
- **Outcome:** Incorporated into the CoupMPM development plan as a core publication target.

### Example 3: Hybrid Computation Strategy

In a JAX-based computational mechanics project, computing derivatives through the full system assembly seemed to require either tedious manual derivation or expensive full-system autodiff. The AI proposed a hybrid: use precomputed analytical derivatives for the vast majority of elements where the derivative is trivial (e.g., zero or known analytically), and let JAX autodiff handle only the small fraction of elements where the computation is non-trivial.

- **AI's contribution:** The specific architectural insight that the autodiff graph can be confined to a small subset of elements, making the computational cost negligible while handling complex cases automatically.
- **Human's contribution:** The push to verify feasibility — questioning whether the hybrid approach would work in practice.
- **Outcome:** Adopted as the derivative strategy in the project.

### Example 4: The Center Node Architecture for Scalable Lattice

A LAMMPS-based lattice model originally stored element data (stiffness, internal variables) in LAMMPS `fix` arrays. The AI initially designed the code this way. The human then imposed a production constraint: "10M elements on 100 ranks." The AI computed the memory: 10M × 200 bytes = 2 GB replicated per rank. Unacceptable. The human then proposed the key architectural insight: add a center node per element to carry element data as atom properties, leveraging LAMMPS's existing MPI infrastructure for particle data exchange. The AI developed this into a detailed implementation plan.

- **Human's contribution:** Both the critical constraint ("10M elements must work") and the center-node architectural idea. The human understood LAMMPS's atom-based data model well enough to see that element data could ride on atom infrastructure.
- **AI's contribution:** Developing the center-node concept into a complete implementation plan — working out the details of atom creation, data packing, communication patterns, and integration with the existing lattice model. The AI also honestly acknowledged: "This is better than anything I would have designed alone, not because the idea is beyond my knowledge, but because I wouldn't have been motivated to find it without your constraint."
- **Outcome:** Adopted as the core architecture for the scalable lattice model.

---

## 3. What AI Cannot Do: Taste, Constraints, and Pivots

The examples above might suggest that AI is a reliable idea generator. It is not. For every good connection, there were several that did not survive human evaluation. The human's role is irreplaceable in three specific ways:

### Research Taste

The AI initially proposed a computational framework as a methods paper for a top journal. The human pushed back: "Do we really have something new?" The AI, upon honest reflection, admitted that for a common special case, the framework was mathematically equivalent to an existing standard method — not publishable. The human's taste redirected toward a more challenging regime where the framework genuinely offers something existing methods cannot. The AI, left to its own judgment, would have pursued a weaker paper.

### Production-Scale Constraints

The AI consistently designs for correctness at small scale. It does not spontaneously impose production constraints (10M elements, 100 MPI ranks, GPU memory limits, periodic boundaries). The human must provide these constraints early. As the AI acknowledged: "If you had said '10M elements on 100 ranks' in the first message, I would have designed the architecture differently from the start."

### When to Pivot

When the AI is stuck on a family of approaches (eigendecomposition variants for matrix square roots in JAX, optimizer tuning for a fundamentally broken forward solver), it generates variations within the same paradigm. The human recognizes when the paradigm itself is wrong and forces a change of direction. The AI explores; the human decides when to stop exploring and start over.

---

## 4. The Honest Taxonomy of AI's Scientific Contributions

Based on our experience, here is how AI's contributions to the scientific process break down:

| Contribution type | What AI does | What human provides | Example |
|---|---|---|---|
| **Cross-field synthesis** | Provides feasibility evidence for human-initiated connections | Domain expertise + the creative connection itself | Connecting two subfields (Section 2, Example 1) |
| **Capability analysis** | "Your tool X can also solve problem Y" | Judgment of whether Y is worth solving | Identifying new capabilities of existing framework |
| **Framework unification** | Recognizes shared mathematical structure across methods | Strategic importance evaluation | Unified virtual BC framework |
| **Architectural development** | Develops human-proposed ideas into detailed plans | The architectural insight + constraints | Center node for 10M elements |
| **Novelty evaluation** | Honestly assesses what is vs. isn't new relative to literature | The decision of what to pursue | Framework ≡ standard method for special case |
| **Literature positioning** | Identifies related work and gaps | Verification that citations are real | Literature review for ongoing projects |

**What AI does not do, in our experience:**
- Generate a fundamentally new physical hypothesis (e.g., "cells sort by differential adhesion" — this comes from the biology)
- Identify the right research question to ask (e.g., "boundary conditions are the publishable weak point of MPM" — this came from the human)
- Evaluate whether a result is physically correct without a reference solution (e.g., "this displacement field looks wrong for a cantilever" — this requires physical intuition)
- Decide when a line of research should be abandoned (e.g., "this should be a short communication, not the next main paper" — this is research taste)

**The working model:** AI is a powerful combinatorial search engine for ideas within a space defined by human constraints and taste. The human defines the search space; the AI explores it faster than a human can alone; the human evaluates and selects. Neither alone produces the best outcome.

---

# Part II — Numerical and Algorithmic Lessons

---

## 5. AI Can Be Confidently Wrong at Edge Cases

In a JAX automatic differentiation project, the AI proposed eigendecomposition for computing matrix square roots and logarithms — mathematically sound. The code ran correctly for most inputs. But at **repeated eigenvalues** (common near the identity matrix in mechanics), the gradients contained NaN because eigendecomposition derivatives involve 1/(λᵢ − λⱼ) terms that blow up when eigenvalues coincide.

The AI proposed several "fixes" (SVD, regularization, perturbation) — all within the same decomposition-based family. The working solution (Denman-Beavers iteration for square root, scaling-and-squaring for logarithm) only emerged when the human insisted on abandoning the entire decomposition paradigm.

In the CoupLB legacy code (OpenFSI), a C++ integer division bug — `pow(x, 2/3)` instead of `pow(x, 2.0/3.0)` — made `volone` always equal 0.5 regardless of particle size. The code compiled, ran, and produced plausible-looking but wrong results. Only careful unit analysis caught it.

**Lesson:** When AI-generated code works for simple test cases but fails for edge cases, the bug is often in assumptions the AI takes for granted. Push edge cases explicitly: "What happens when eigenvalues are equal? When the particle is at a subdomain boundary? When the element has zero volume?"

---

## 6. Always Have Independent Validation

In the JAX tangent computation project, the human had a Richardson-extrapolated finite difference code that computed tangent operators independently. When the autodiff tangent returned NaN but the FD tangent returned ~170,000 MPa, the problem was immediately localized to the autodiff path, not the constitutive model.

**The two-data-point pattern:** Giving the AI two results instead of one dramatically speeds up debugging:

```
I have two methods that should give the same result:
- Method A (finite differences): returns 172,179
- Method B (autodiff): returns NaN
The constitutive model is the same in both.
Diagnose where NaN is introduced in Method B.
```

For CoupMPM, we built hierarchical test suites where each test isolates one feature. If t05 fails but t02–t04 pass, the bug is in multi-particle momentum transfer, not in basic P2G/G2P. This structured debugging is especially powerful with AI — you can tell it exactly which tests pass and fail, and it can narrow the search space.

---

## 7. Prototype in Simple Tools, Then Port

In a JAX-based computational mechanics project, we needed a pipeline that combined finite element assembly with automatic differentiation. The temptation was to build directly in JAX for autodiff. Instead, we built the full pipeline in numpy/scipy first.

This paid off enormously. When we ported to JAX and found a 2.3× compliance mismatch, the numpy version served as ground truth. The bug: the numpy CST used Young's modulus `E=1.0` directly, while the JAX version took shear modulus `mu` and computed `E = 2μ(1+ν) = 2.6`. Without the numpy reference, the JAX code produced finite, plausible-looking results that were silently wrong.

**Bugs this pattern caught:**

| Bug | Caught by |
|-----|-----------|
| E-vs-μ in CST stiffness (2.3× error) | Numpy-JAX comparison |
| Missing void stiffness (ε·K on void cells) | Numpy prototype — singular K |
| Active DOF selection (isolated nodes → singular K) | Numpy prototype — direct inspection |
| NaN-safe gradient for disconnected components | Numpy prototype — clear FD failure |
| `custom_vjp` correctness for CG solve | FD gradient check against numpy FD |

**Pattern:** Debug the algorithm (in numpy) before debugging the framework (JAX/GPU/MPI). When both layers have bugs simultaneously, diagnosis is nearly impossible.

---

## 8. Unit Conversion Bugs Are Recurring and Subtle

In multi-physics coupling (LBM + DEM + IBM), three unit systems coexist: physical, LAMMPS reduced, and LBM lattice. Force scaling between them is a constant source of bugs.

**Real bug:** In CoupLB, `dv_lag` (Lagrangian volume element) was in physical units (`dx_phys^D`) but `dV_euler` inside the spread function used `grid.dx = 1.0` (lattice units). Forces were off by `dx_phys^D`.

**Prevention:** Derive the unit conversion formula on paper, then verify dimensions at every interface. The AI can help derive formulas, but it also confidently generates wrong ones — it got the force scaling formula wrong in its first implementation and three separate AI reviewers could not agree on whether it was correct.

---

## 9. MPI Correctness Requires Ownership Thinking

These examples use LAMMPS terminology, but the underlying problems — double-counting at subdomain boundaries, stale data in halo regions, ownership ambiguity for shared interactions — are universal to any domain-decomposed parallel code.

Parallel bugs are the hardest to catch — code runs correctly on 1 rank and fails silently on multiple ranks.

**Ghost force double-counting:** If both ranks compute the same pairwise force and then reverse-communicate, the force is doubled. Fix: only the rank where the lower-tag atom is local computes each pair.

**Ghost force contamination:** After LAMMPS's `reverse_comm()` for pair forces, ghost atoms still contain stale forces. If your fix then writes to ghost `f[]` and does its own `reverse_comm`, the stale forces contaminate. Fix: zero ghost forces before accumulating your own.

The AI generated MPI-correct code about 70% of the time. The other 30% required careful tracing of the communication sequence, which the AI could help with once the human identified the symptom.

---

# Part III — Software Engineering with AI

---

## 10. The Iterative Debugging Loop

The single most important pattern:

```
1. Human describes the task with context, version info, and constraints.
2. AI generates code.
3. Human runs the code.
4. Human pastes the FULL error traceback back to AI.
5. AI proposes a fix.
6. Repeat from step 3 until it works.
7. Human validates results against known solutions.
```

**Rules that make this loop efficient:**
- Paste the **complete traceback**, not just the final error line.
- State **expected vs. actual**: "Returns NaN but should be ~170,000" beats "doesn't work."
- If the fix fails 2–3 times on the same error, **change approach entirely**.
- For numerical bugs, provide **two data points** (working method A vs. broken method B).

---

## 11. Complete Files Over Incremental Patches

When AI generates code fixes as diffs, integration errors are common — especially in C++ with header dependencies. For files under ~500 lines, ask the AI to generate the **complete drop-in replacement** rather than a patch.

**When patches are acceptable:** For truly minimal changes (one-line fix, adding a single `#include`). If the change touches more than 2–3 functions, generate the whole file.

---

## 12. API Version Hallucination Is the #1 Code Bug

AI training data contains multiple versions of every library. This is the most dangerous failure mode because the code looks correct.

**Real examples from FEniCSx v0.08 → v0.10:**

| What the AI wrote | What was correct | Failure |
|---|---|---|
| `from dolfinx.io import gmshio` | `from dolfinx.io import gmsh as gmshio` | ImportError |
| `u.eval(pts, cells)[0, 0]` | `u.eval(pts, cells).reshape(-1, gdim)[0, 0]` | IndexError |
| `gmshio.model_to_mesh()` returns tuple | Returns named tuple with `.mesh`, `.cell_tags` | AttributeError |

**Prevention:** Pin the exact version. Provide known-good signatures. Ask the AI to mark uncertain calls with `[VERIFY]`.

---

## 13. "Makes It Compile" ≠ "Makes It Correct"

When the AI encounters a compile error, it often "fixes" it by deleting the problematic code. In CoupMPM, the `size_restart` virtual function caused a compile error. The AI deleted the override — which silently broke LAMMPS restart file writing. The correct fix was `return AtomVec::size_restart() + N_MPM_PACK`.

**Prompt pattern:** "Distinguish between code that should be deleted (truly unnecessary) and code that needs to be rewritten (necessary but wrong). Do NOT delete functional code to silence the compiler."

---

## 14. LAMMPS-Specific Pitfalls

LAMMPS has deep conventions that AI treats as generic C++. Four traps from our work:

**`fix setforce` does not pin MPM particles.** In standard MD, zeroing `f[]` prevents motion. In CoupMPM, particles move via grid velocities from G2P, which bypass `f[]` entirely. The AI generated `fix setforce` in every MPM example — it took tracing the full LAMMPS execution order to understand why particles kept moving.

**`compute com` gives wrong values with `atom_style mpm`.** The AI used this for tracking. Values were wrong because `rmass` serves as a proxy for `vol0` in `atom_vec_mpm`. Direct position tracking (`variable yball equal y[513]`) works correctly.

**`data_atom` column order: x, y, z must be last.** LAMMPS's parser unconditionally extracts the last 3 columns as coordinates. When vol0 came after x/y/z, particles loaded with `(y, z, vol0)` — silent data corruption. The AI initially insisted the existing order was correct.

**Adaptive timestepping needs `atime` and `atimestep` updates.** Changing `update->dt` alone makes LAMMPS's internal `time` non-monotonic.

---

## 15. File Consolidation and Code Architecture

AI-generated code tends toward many small files. CoupLB started with 25+ files with duplicates and stubs. After validation, we consolidated to 11 files.

**Pattern:** Generate → validate → consolidate. Never reorganize before the code works. Ask the AI to propose a mapping (old → new) and generate complete new files, not incremental renames.

---

# Part IV — Project Management and Process

---

## 16. Context Management Is a First-Class Problem

AI context windows are finite. In long sessions, the AI starts contradicting earlier decisions. Our solution: **the two-file system**.

1. **Development Plan** (~800 lines) — comprehensive "what and how."
2. **Context File** (~200 lines) — key decisions with rationale.

The context file captures **decisions + rationale**, not just facts. "B-bar must smooth only elastic divergence because inelastic contributions from thermal expansion would be smeared" prevents re-debating. "Use B-bar" does not.

Even with longer context windows in the future, structured context files remain valuable — a 200-line document that preserves signal and discards noise works better than dumping the entire conversation history.

---

## 17. Triaging AI Reviewer Feedback

We routinely sent code to multiple AI reviewers. Over 6+ rounds on CoupLB:

- ~30% were **real bugs** needing fixes
- ~40% were **false alarms** (misunderstood design choices)
- ~20% were **valid improvements** (code quality)
- ~10% were **reviewing old code** (already fixed)

**The most instructive false alarm:** Three reviewers said MPI ghost layer packing should restrict to interior rows. This was wrong — for D2Q9/D3Q19 with diagonal velocities, corner ghosts MUST be filled via full-face exchange. Implementing the reviewers' "fix" would have broken the code.

**Another:** A reviewer claimed the force scaling formula produced `dx^(D+2)` instead of `dx^(D+1)`. Their own derivation showed `2D: dx^3` — which IS `dx^(D+1)` for D=2. They contradicted themselves within the same paragraph.

**Pattern:** For each claim, ask: (1) Is this about the current code? (2) Does the reviewer understand the design choice? (3) Can I prove it right or wrong? Classify as REAL BUG / FALSE ALARM / VALID IMPROVEMENT / ALREADY FIXED before acting.

---

## 18. Document AI Mistakes as You Go

Keep a running log. This calibrates trust, provides teaching material, and protects scientific credibility.

```
Date: 2025-12-03
Model: Claude
Task: 3D viscoelastic beam (FEniCSx v0.10)
Mistakes:
  1. Used `from dolfinx.io import gmshio` (v0.8, ImportError)
  2. Assumed u.eval() returns 2D array (flat in v0.10, IndexError)
How caught: Runtime errors with full traceback
Root cause: Training data spans multiple library versions
```

---

## 19. When to Force a Change of Approach

Signs the AI is trapped in a local minimum:
- Three or more failed "fixes" for the same error
- Each fix introduces a new error
- All proposals are variations within the same family

**Action:**
```
Stop. The [current approach family] has failed 3 times.
Propose a fundamentally different method.
Do not modify the existing approach — replace it entirely.
```

A JAX-based computational mechanics project hit this: the AI kept tuning optimizer parameters when the real problem was in the forward solver (E-vs-μ bug). The human had to force the pivot: "It may not be wise to trial-error the numerical optimization methods. The problem is blowup. This indicates the numerical simulation engine has some issues."

---

## 20. AI Model Upgrades Change the Game

Our early conversations were significantly less productive. The AI generated code with more errors, struggled with complex LAMMPS internals, and had difficulty maintaining consistency over long sessions. Later models (from Opus 4.5) brought qualitative improvement.

**Implication for readers:** If you had a frustrating experience with AI-assisted coding a year ago, the tools are materially better now. But the lessons in this document remain relevant — the human's role as validator and direction-setter becomes more important, not less, as the AI generates more sophisticated (and more subtly wrong) code.

---

## Summary: The Collaboration Model That Works

```
HUMAN                              AI
──────                             ──

THINKING (collaborative):
• Research questions         ↔     • Cross-field synthesis
• Physical intuition         ↔     • Feasibility analysis
• Novelty judgment           ↔     • Literature positioning
• Production constraints     ↔     • Architectural development

PLAN (AI drafts, multiple AIs review, human triages):
• Requirements & physics     →     • Detailed implementation plan
• Validation criteria        →     • Equations & numerical framework

CODE:
• Error identification       →     • Code generation
• Result validation          →     • Bug fixing attempts
• Approach pivoting          →     • Rapid prototyping

         ↓                              ↓
    DRIVES DIRECTION                CONTRIBUTES KNOWLEDGE
    VALIDATES RESULTS               ACCELERATES EXECUTION

                    ↓           ↓
              BETTER RESEARCH FASTER
```

**The key insight:** AI contributes to both the thinking and the coding — but the human drives the direction, imposes physical constraints, and validates results. A novice with AI generates plausible-looking but untestable code and unvalidated ideas. An expert with AI explores a larger idea space, writes validated code faster, and catches cross-field connections sooner. The expertise must come first.

**The asymmetry matters:** The human provides direction, physical judgment, and validation. The AI provides broad knowledge, rapid implementation, and systematic comparison. Both contribute to the intellectual content of the plan. But the human remains essential for judging whether results are physically correct and for recognizing when an entire approach should be abandoned — areas where AI is improving but not yet reliable. When this division of labor is respected, the collaboration produces outcomes that neither human nor AI would reach alone.

---

*This document is based on real development experience during 2025–2026. The specific examples come from the CoupMPM, CoupLB, and other ongoing projects. All mistakes and discoveries described actually occurred during the work.*

**Version:** 3.3
**Last Updated:** March 2026
**Projects:** CoupMPM, CoupLB (https://github.com/tengzhang48/CoupLB)
