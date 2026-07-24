# Case Study: When Verification Rewrites the Theory — A Symplectic Mooney–Rivlin Crack Tip

**How a human–AI team turned a new nonlinear crack-tip field, a useful but
incomplete spectral scaffold, and several rounds of mutually inconsistent
“verified” claims into a pre-submission candidate—then reopened it when a
green gate proved blind to a leading-constraint-compatible measurement-space
direction, rebuilt the reaction-carrying hierarchy, found that a second
family of green gates shared the wrong inner variable map, and closed a
bounded release with a nuisance-free exact-axis channel in a matching-circle
campaign.**

---

## 📖 Table of Contents

- [Overview](#overview)
- [Evidence map](#evidence-map)

**Part I — The Scientific Journey**
- [1. The Problem: A Two-Invariant Crack Tip](#1-the-problem-a-two-invariant-crack-tip)
- [2. The Constraint That Reorganizes the Tip](#2-the-constraint-that-reorganizes-the-tip)
- [3. From Local Theory to Parameter-Free Tests](#3-from-local-theory-to-parameter-free-tests)
- [4. The Symplectic Promise and the Missing Operator](#4-the-symplectic-promise-and-the-missing-operator)
- [5. Where the Defensible Scope Now Stops](#5-where-the-defensible-scope-now-stops)

**Part II — Technical Lessons**
- [6. Correct Equations Can Still Form a Contradictory Paper](#6-correct-equations-can-still-form-a-contradictory-paper)
- [7. A Unit Gauge Hid a Missing Amplitude](#7-a-unit-gauge-hid-a-missing-amplitude)
- [8. A True Premise Is Not a Sufficient Argument](#8-a-true-premise-is-not-a-sufficient-argument)
- [9. A Fitted Coefficient Is Not Automatically an Asymptotic Coefficient](#9-a-fitted-coefficient-is-not-automatically-an-asymptotic-coefficient)
- [10. A General Theorem Is Not a Specific Reduction](#10-a-general-theorem-is-not-a-specific-reduction)
- [11. Degenerate Endpoints Decide the Admissible Theory](#11-degenerate-endpoints-decide-the-admissible-theory)
- [12. Find the Carrier by Decomposing the Flux](#12-find-the-carrier-by-decomposing-the-flux)
- [13. A Closed Rung Is Not a Closed Tower](#13-a-closed-rung-is-not-a-closed-tower)
- [14. Fix Passes, Stale State, and Blind Gates Are New Error Surfaces](#14-fix-passes-stale-state-and-blind-gates-are-new-error-surfaces)

**Part III — Collaboration Patterns**
- [15. The Multi-AI Review Loop](#15-the-multi-ai-review-loop)
- [16. Different Review Styles Saw Different Failure Classes](#16-different-review-styles-saw-different-failure-classes)
- [17. Where AI Failed, Specifically](#17-where-ai-failed-specifically)
- [18. The Human's Critical Contributions](#18-the-humans-critical-contributions)
- [19. Attribution, Carefully](#19-attribution-carefully)

**Part IV — Closing the Verification Loop**
- [20. Remove Nuisance Directions Before Estimating a Singular Power](#20-remove-nuisance-directions-before-estimating-a-singular-power)
- [21. Submission Readiness Was an Executable Checkpoint](#21-submission-readiness-was-an-executable-checkpoint)

**Part V — Comparing Two Method-Defining Frontiers**
- [22. Crack Tip and Wrinkle: Different Walls, the Same Standard](#22-crack-tip-and-wrinkle-different-walls-the-same-standard)

- [Summary](#summary)

---

## Overview

Analytical crack-tip fields for highly deformed soft sheets are largely
restricted to generalized neo-Hookean materials whose energy depends on one
invariant, W = W(I₁). The Mooney–Rivlin solid,

```text
W = c₁(I₁ - 3) + c₂(I₂ - 3),        c₁ > 0, c₂ > 0,
```

is the simplest standard rubber model outside that class. In plane stress,
the second invariant does not merely perturb the known neo-Hookean solution.
As the dominant tip stretch diverges, it becomes a stiff penalty that forces
the two transverse stretches to become equal. That constraint reorganizes the
singular transverse in-plane field and the areal stretch while leaving the
leading energy-release relation in neo-Hookean form. It does not determine a
regular characteristic-parallel shear, a fact recognized only in a later
mode-completeness audit.

The July 19 manuscript reported a leading opening proportional to r¹ᐟ², an
in-plane field proportional to r⁵ᐟ⁴, a raw deformed-tip profile with
exponent 2/5, an angle-independent compensated Jacobian, and

```text
G = (π/2) c₁ P².
```

A pure-shear strip fixes the tip amplitude P from the applied grip stretch.
Its finite-element solutions test the G–P relation and compensated-Jacobian
kinematics without imposing the asymptotic crack-tip field.

The core G, J, and P results survived the review campaign. The later audit
withdrew the unconditional raw 2/5 imaging claim: the
leading-constraint-compatible term
`C_s s`, with `s = r sin²(θ/2)`, dominates the raw horizontal face coordinate
if a nonzero coefficient persists after matching. The 2/5 law remains a
conditional prediction for the detrended r⁵ᐟ⁴ remainder, or for a special
solution in which matching selects `C_s = 0`. Much of the
higher-order story also did not survive unchanged. A five-row spectral pencil
that began as the organizing theory was ultimately scoped as a *scaffold*:
exact on its opening block, useful for locating candidate families, but not
the derived full reaction-carrying operator. Several higher-order amplitudes
moved, acquired missing dimensional factors, or were demoted from free
parameters to conditional candidates. The submission draft became more
defensible by separating established, conditional, and open statements, and
its July 19 signoff was reopened when the raw-profile gate failed. The July 20
correction then synchronized the manuscript, ESI, and public-companion
candidate. It retained the G/J/P core, made the raw-profile statement
conditional, inserted the missing dominant-balance derivation, and replaced
the blind tangent comparison with a target-free profile-mode audit.

The July 21–22 campaign asked a harder question: how far could the candidate
`B` and `Q_k` families be carried by the radial symplectic method before they
were merely a catalog? Gates 1–3 rebuilt the reaction-carrying Hessian system,
its boundary current, and the first sourced `B` handoff from the constrained
action. Gate 4 extended several formal outer rungs, while Gate 5A froze the
isolated opening projectors. Gate 6 then invalidated the archived axis-layer
target itself. A derivation restarted from fixed-Cartesian physical PK1 found
a different cusp operator, and the next one-scale reaction problem produced
an exact incompatibility between smooth-axis parity and its prescribed outer
tail. This is a precise obstruction to the present sequential one-scale
endpoint construction, not a proof that the nonlinear continuum crack problem
has no solution. A two-scale endpoint construction is now a future-paper
problem.

The July 22–24 closure did not attempt to finish that second paper. A
restricted 13/4 calculation established an opening-sector resonance and a
nonzero restricted projection, but a later five-sector audit showed that the
same-grade source census was incomplete. The manuscript therefore reports the
resonance and coefficient-qualified logarithmic consequence while leaving the
coupled response and physical net amplitude open. For the 5/4 field, the team
changed the numerical observable instead of abandoning the result. On the
intact axis, the two undetermined matching contributions vanish identically.
A matching-circle campaign then obtained `q = 1.251529` and a parameter-free
amplitude ratio of `1.012420`, with a free two-power fit recovering the next
radial slot near 7/4. The paper-facing public state was frozen as `v1.2.0` on
24 July. A final AI pre-submission review passed the bounded physics/data chain
after two release conditions were closed. A later full-document reading,
submission-package build, and reference/scope audit added further checks
without changing the central equations or numerical values. These are
documented internal verification steps, not journal peer review.

The scientific repository began in June 2026, with manuscript revisions
recorded from 3 July. The initial multi-AI review campaign ran from 5–19 July,
with an especially intensive 17–19 July cycle. It used
Claude/Fable as the principal revision executor,
GPT/Codex as a structural reviewer and later derivation lead, Kimi as an early
independent verifier, DeepSeek/OpenCode as a late end-to-end auditor of the
then-current theory tree, and earlier GLM and Opus reports. Teng Zhang, the
human author, acted as the meta-reviewer and made the scope and stopping
decisions. The central lesson is not that multiple AIs vote their way to
correctness. They do not. The useful unit was a disagreement converted into
an artifact that could falsify one side.

---

## Evidence map

This case study separates public scientific evidence from internal process
evidence. The public release contains the equations, tests, curated numerical
records, claims ledger, and reproduction paths. Signed agent reports and
superseded branches remain in the research workspace and are used here only
to establish who checked what, when, and with which limitations.

| Episode | Controlling evidence | What the evidence supports | What it does not support |
|---|---|---|---|
| Leading constraint, opening, Jacobian, and energy relation | [`principal_claims.json`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/data/claims/principal_claims.json), the [`run_verification.py`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/tests/run_verification.py) analytical runner, and the stored strip controls | The bounded plane-stress claim set and its executable checks | Experimental validation of the constitutive model |
| Missing `C_s s` motion and disk diagnosis | [`PROCESS_AND_LESSONS.md`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/PROCESS_AND_LESSONS.md) and the preserved disk records | Why the raw face-shape claim became conditional and why the disk left the quantitative validation | A proof of continuous-boundary contact or a converged alternative disk branch |
| Restricted 13/4 resonance | [`THEORY_NOTES.md`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/THEORY_NOTES.md), [`verify_lambda13_restricted_log.py`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/analysis/verify_lambda13_restricted_log.py), and the dated internal adjudication | Exact resonance plus a nonzero projection for one audited source sector | The total same-grade source, coupled response, or a universal physical logarithm |
| Matching-circle campaign | [`GLOBAL_LOCAL_RESULTS.md`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/fem/GLOBAL_LOCAL_RESULTS.md), [`GLOBAL_LOCAL_WORKFLOW.md`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/v1.2.0/fem/GLOBAL_LOCAL_WORKFLOW.md), and retained JSON/NPZ records | The exact-axis 5/4 class and predicted amplitude for the tested strip, with stated convergence checks | Selection of specimen-level `C_s` or `C_h`, the complete 7/4 field, or two-way coupling |
| Public release | Tag [`v1.2.0`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/tree/v1.2.0), commit `bba3c93`, and its 201-file `MANIFEST.sha256` | The immutable paper-facing code/data state | A DOI, journal acceptance, or external peer review |
| Submission closure | Research commits `29b8f09`, `92c60e2`, and `bd0652c`, plus `paper/submission/soft_matter_2026-07-24/SUBMISSION_CHECKLIST.md` | Scientific claim closure, isolated package rebuild, and final citation/scope checks | Independent rederivation of every coefficient by the document reviewers |

The map is intentionally claim-specific. A reviewer who read every page but
did not rerun the code supplied a different kind of evidence from a reviewer
who checked archived values or an executable that differentiated the action.
Those probes should not be counted as interchangeable votes.

---

# Part I — The Scientific Journey

---

## 1. The Problem: A Two-Invariant Crack Tip

In an incompressible sheet under plane stress, the thickness stretch is the
inverse of the in-plane areal Jacobian. Eliminating it leaves a two-dimensional
energy in the in-plane deformation gradient. For W(I₁) materials, classical
hodograph methods can linearize important versions of the crack problem. The
I₂ term in a Mooney–Rivlin solid breaks that route.

The first temptation was to treat c₂ as a conventional correction. The tip
scaling says otherwise. The largest principal stretch behaves as λ₁² ~ 1/r.
At fixed incompressible product λ₂λ₃ = λ₁⁻¹, the I₂ contribution penalizes
λ₂² + λ₃² with an effective stiffness proportional to c₂λ₁². For every fixed
c₂ > 0, that stiffness diverges as r → 0. Minimizing the penalized sum at fixed
product gives

```text
λ₂ = λ₃ = λ₁^(-1/2).
```

The c₂ → 0⁺ and r → 0 limits therefore do not commute. The constrained zone
shrinks away as c₂ vanishes, but inside that shrinking zone the limiting
kinematics remain locally uniaxial. This singular limit is why the
neo-Hookean control can share the leading opening field and energy relation
while failing the two-invariant kinematic signatures.

## 2. The Constraint That Reorganizes the Tip

At leading order, the in-plane equilibrium collapses to the pointwise
constraint

```text
J⁴ = |∇y₂|²,
```

where J is the in-plane areal Jacobian. Combining this identity with the
surviving harmonic opening equation gives

```text
y₂ = P r^(1/2) sin(θ/2) + …,
y₁ = c₀ + C_s s + P^(-1/2) r^(5/4) g(θ) + …,
s = r sin²(θ/2).
```

The constraint fixes the component of `∇y₁` transverse to `∇y₂`. After the
opening-gradient-parallel null addition is separated, formal power balance
gives an r⁵ᐟ⁴ constraint-active residual on a chosen regular-axis analytic outer
representative. The local constraint cannot fix `C_s s`: for the leading
opening `y₂ = P√s`, `∇s` is
parallel to `∇y₂`, so this addition leaves the leading-map determinant J
exactly unchanged. More generally, `y₁ → y₁ + F(y₂)` is the exact null
transformation. The mode is regular across the intact ligament and changes a
physical coordinate; calling it a gauge does not make it invisible to a
camera.

The corrected manuscript and ESI now derive this decisive equilibrium
reduction from both reduced-Piola equilibrium rows. They state the dominant
orders, show how the divergent c₂ term acts as a reaction rather than a
leading stored-energy contribution, recover `J⁴ = |∇y₂|²`, impose the
leading face and symmetry conditions, and identify the assumptions behind the
dominant-principal-stretch reduction. The public companion now reproduces the
exact stress, constraint-null, leading-field, and flux identities while
explicitly scoping its older row-4 script as a linearization of the already
derived constraint, not a derivation of this entire dominant-balance chain.
This is an asymptotic dominant-balance derivation, not a uniform finite-c₂
matching theorem.

The angular profile g is selected by an endpoint regularity condition on the
intact ligament. Its face value is g(π) = 2.0333… in the manuscript's
normalization. This is the manuscript's analytic outer-branch selection; a
singular angular matching layer remains an acknowledged open issue. At leading
order near the tip, the resulting principal-stretch
magnitudes are angle-independent,

```text
λ₁ = (P/2) r^(-1/2),
λ₂ = λ₃ = sqrt(2/P) r^(1/4),
J r^(1/4) = sqrt(P/2).
```

These are asymptotics of the reduced two-dimensional plane-stress model. A
physical sheet accesses them only in a nonempty overlap annulus,

```text
t_s << r << min(r_*, r_I2).
```

Here `r_* = P²c₂/(4c₁)` estimates the constrained-zone edge, and
`r_I2 ~ P²(c₁/c₂)²` is the scale beyond which the on-manifold I₂ correction is
no longer small.

Below the sheet thickness `t_s`, the field is three-dimensional; the formal
`r → 0` computation verifies the reduced model's mathematical limit, not that
sub-thickness field.

On the crack face `s = r`, so

```text
y₁ - c₀ = C_s r + P^(-1/2)g(π)r^(5/4) + …,
y₂ ~ r^(1/2).
```

If `C_s = 0`, eliminating r gives the 2/5 profile. If matching produces a
nonzero coefficient that persists asymptotically, the regular linear term
dominates the raw horizontal coordinate and the raw limiting exponent is 1/2,
the same as the neo-Hookean face exponent. The 2/5 law is the chosen
regular-axis analytic representative's conditional prediction for the detrended remainder
`y₁ - c₀ - C_s r`. Whether global specimen matching selects either branch is
not established.

On the chosen `C_s = 0` outer representative, the first correction is
forced by the *on-manifold I₂ stress*, not by off-manifold compliance. Its
opening profile is
v(θ) = -(2/3)sin(θ/2), and its in-plane term carries the dimensional factor
P⁻³ᐟ². This apparently small distinction in mechanism and scaling later became
one of the review campaign's most consequential tests.

## 3. From Local Theory to Parameter-Free Tests

The energy flux calculation produces

```text
G = (π/2)c₁P²,
σ₂₂ r = G/π.
```

For a Rivlin–Thomas pure-shear strip of reference height h and grip stretch λ,

```text
G = h(c₁ + c₂)(λ² + λ⁻² - 2),
```

so the remote loading determines P without a numerical specimen calculation.
This creates a stricter test than fitting an unconstrained tip amplitude.

The finite-element campaign ultimately retained one specimen for a
quantitative within-model check: the Rivlin–Thomas pure-shear strip. Its
computed energy flux agreed with hW∞ within 0.00–0.15%, and its measured P
agreed with the closed-form prediction within 2.2–3.0% over the reported load
range. Its compensated Jacobian had 3.2–9.1% angular spread, while the c₂ = 0
control showed 101.5–112.2% angular spread.

An auxiliary boundary-driven disk was initially presented as a second
cross-check. A later boundary-condition and geometry audit showed that its
prescribed outer map imposed a different loading path, including strong
crack-parallel compression, and constrained parts of the crack mouth. At the
larger loads its stored upper-face vertex trace also crossed itself away from
the tip. The disk was removed from the current quantitative validation because
it is not a pure-shear surrogate and its global branch is unresolved. The
calculation itself was preserved as a second boundary-value problem whose
loading, disk-to-crack size, continuous boundary, stability, and inner field
can be tested separately.

The first strip-only production audit used one physical offset shared across
five rays, checked per-ray sensitivity, and fitted the residual exponent over
nested windows. It exposed the allowed `C_s s` background, but the available
fixed-core windows did not independently resolve the r⁵ᐟ⁴ residual. The former
raw 2/5 tip-shape claim was therefore withdrawn: its legacy estimator omitted
the leading-constraint-compatible term rather than testing its coefficient.

The final test changed the observable. On the intact axis,
`C_s r sin²(θ/2)` and the homogeneous
`P^(-1/2) C_h r^(5/4) sin^(5/2)(θ/2)` both vanish exactly. Six newly built
global strips supplied complete quadratic (P2) displacement traces on matching
circles: four formed the core/angular sequence and two varied the matching
radius. For each accepted case, the strip cells inside the circle were
transferred and re-solved as an exact-restriction consistency check. This local
step did not add independent tip resolution. Core convergence came from
rebuilding the global strip at successively smaller cores. Its finest
exact-axis fit gave

```text
q = 1.251529,
A_axis/A_axis,pred = 1.012420.
```

A separate free two-power fit returned leading powers 1.24980–1.25152 and
next powers 1.68971–1.74746 without fixing either exponent. The latter
interval approaches the predicted 7/4 in-plane slot. The full-angle fit gave
`q = 1.25349` after subtraction of the regular background and agreed with the
angular ODE family when its homogeneous member was admitted. It did not
select `C_h = 0`.

This division mattered. The global FEM did not impose the crack-tip field,
and the exact restriction checked the transferred global solution rather than
prescribing the asymptotic displacement. The exact-axis channel removed the
two matching coefficients algebraically before fitting, while the free
two-power and holdout tests checked that the result was not created by fixing
the target exponent. A separately refined local mesh was retained only as a
one-way diagnostic and did not enter the exponent sequence. The campaign
supports the asymptotic class and its parameter-free exact-axis amplitude for
the tested strip. It does not determine specimen-selected `C_s` or `C_h`, and
it is not a two-way global–local coupling.

The c₂ = 0 control is especially valuable because it shares enough of the
leading opening behavior to argue strongly against a generic mesh or fitting
explanation for the Mooney–Rivlin Jacobian plateau.

## 4. The Symplectic Promise and the Missing Operator

The symplectic formulation treats ξ = ln r as a time-like coordinate. The
deformed-position trace on a circle and its r-weighted radial traction form a
canonical pair. Linearization about the scale-similar leading field is a
second variation, so a conserved bilinear pairing should exist on a correctly
derived constrained state space.

The early manuscript moved too quickly from that general statement to a
specific five-row differential–algebraic pencil. The pencil correctly
contained the harmonic opening block and useful analytic mode families, but
its in-plane momentum omitted reaction content and its multiplier propagated
independently. A later action-level reduction showed that the canonical
reaction is slaved and that the full momentum differs from the scaffold
variable. The generic second-variation theorem was sound; the identification
of the printed five rows with its full operator was not derived.

The July 20 correction did not discard the scaffold. It named it accurately.
At that checkpoint the manuscript established the conserved pairing and the
3/2 − Λ duality exactly on the opening block and retained the other rows as a
classified spectral scaffold. At the scaffold/eigenvector-audit level, a
characteristic shear sᵏ pairs with the singular auxiliary s¹⁻ᵏ,
corresponding to labels k and 1 − k. This is not by itself a full-operator
shear-channel conservation theorem. Applying the opening reflection globally
had been another category error. The later Gate-1/2 work derives a
reaction-carrying constrained *outer* operator and current; it does not
retroactively turn the old five rows into that operator or supply the physical
finite-compliance endpoint domain.

## 5. Where the Defensible Scope Now Stops

The July 20 audit reopened the manuscript, and the conservative correction is
implemented in its source and ESI. At that checkpoint the working title
emphasized constrained asymptotics, the unfinished five-row scaffold was
reduced to an outlook, and the unconditional raw 2/5 claim was removed. The
July 21–22 work did not restore the old scaffold as a completed spectrum. It
derived substantially more of the exact symplectic construction and made the
framework, rather than the energy-flux corollary alone, central again. The
evidence supports the following bounded scope.

### The July 21–22 gate campaign

The next decision was not to put every higher-order candidate back into the
paper. It was to determine whether the candidates `B` and `Q_k` came from a
reproducible symplectic construction or only from the old five-row catalog.
The team wrote a dependency-ordered six-gate program:

```text
Gate 1   reaction-carrying Hessian operator and provisional outer endpoint chart
Gate 2   Green/symplectic current and admissible pairing domain
Gate 3   selected B seed and its first complete sourced handoff
Gate 4   nonlinear outer recursion and Fredholm assembly
Gate 5   normalized dual extraction from finite-radius fields
Gate 6   finite-compliance endpoint matching and physical selection
```

Gates 1 and 2 replaced the inferred scaffold dynamics with a non-autonomous
Hessian DAE derived from the constrained action, including the reaction in the
canonical momentum, total endpoint tractions, and an off-shell Green identity.
Gate 3 then closed the selected analytic-displacement `B` block at its frozen-
leading, first-handoff scope. Its endpoint logarithms, current tails, and
source-resolved Fredholm data survived a hostile Kimi review that restarted
from the physical action rather than trusting the coefficient generator.

Gate 4 was deliberately harder. It had to combine the `B`, `Q_k`, material,
and background ladders rather than continue one mode in isolation. Several
representative rungs closed exactly, including the first stationary-background
handoff, and the calculation exposed a formal `Lambda = 17/4` outer field that
leaves the regular finite-action endpoint class. This is a verified handoff,
not total Gate-4 closure. Gate 5 was not skipped: Gate 5A independently froze
the normalized projectors for the isolated opening harmonics and their source/
face ledger. Mixed reaction-carrying extraction must wait for the physical
endpoint form.

That dependency pulled Gate 6 forward. An extensive archived T3 calculation
had solved a scalar axis-layer ODE accurately, but the ODE itself had not been
derived from physical PK1. The deformed components `y_1,y_2` are fixed
Cartesian scalars; only the reference columns of their gradients are resolved
in the polar frame. T3 had inserted the `-B,+A` connections appropriate to
spatial components expressed in a rotating polar basis. It had also failed to
carry the fixed-physical-angle radial derivative of
`eta = theta/delta(r)`, for which

```text
r partial_r [r^alpha U(eta)]
  = r^alpha [alpha U-(eta/2)U']       when delta is proportional to r^(1/2).
```

Returning to the exact reduced energy and direct fixed-Cartesian PK1 gave the
physical `h=3` cusp equation

```text
(1+4eta^2)Z''-14eta Z'+18Z=0,
```

not the archived T3 target. Exact symbolic extraction, substitution into the
unexpanded stress divergence, and an independent finite-difference gauge all
confirmed the reset. The old T3 numerics remain a record of an internally
consistent assumed model; they are not evidence for this physical operator.

The reset did more than change coefficients. The first inhomogeneous
one-scale reaction connection is

```text
(1+4eta^2)Pi1''-10eta Pi1'+12Pi1
  = 30(1+4eta^2)^(-1/4).
```

The solution selected only by the required far-field tail cannot also obey
smooth Mode-I parity. With the homogeneous test function
`H = 1-6eta^2`, the exact Green identity gives

```text
-Pi1'(0)
  = 30 integral_0^infinity
      (1-6eta^2)(1+4eta^2)^(-5/2) d eta
  = 5/2.
```

Thus the tail-selected branch has `Pi1'(0) = -5/2`, whereas smooth-axis parity
requires zero. The even homogeneous solution cannot change that derivative;
the odd repair grows at infinity and reorders the matching. The local
differential row and its outer tail can therefore both be correct while the
proposed one-scale half-line boundary-value problem is incompatible as posed.
Any later
`Lambda = 17/4` cascade built on that tail is conditional connection data, not
a closed smooth-axis solution. The final bounded one-scale audits closed two
important loopholes. The complete homogeneous connection fixes the odd
parity-repair coefficient to `5/2`; after optimally removing its faster
`eta^2` component, the exact `(10sqrt(2)/3)eta^(3/2)` overlap remains. A
separate `t = sqrt(delta)` grade audit proves that regular analytic
finite-compliance backgrounds cannot alter the obstructed `t^1` Green moment;
direct PK1 puts their local mixing and the `c1` tangent at `t^5`. A
nonanalytic same-grade sector, retained-`C_s` reordering, or a two-scale match
can still alter the balance and was not solved. Nor does the mismatch predict
a physical divergent axis field: the outer obstruction enters inside the shrinking
finite-compliance region where the smooth inner solution must supersede the
outer expansion. It is matching data that forces a reorganization.

This checkpoint separates three meanings of completion that earlier notes had
blurred:

- A **submission-ready reduced-model paper** needs every printed claim and
  figure supported and reproducible. It may leave higher-order matching open.
- **Six-gate reduced-model closure** would also complete the declared outer
  hierarchy, physical endpoint domain, dual extraction, and composite
  matching. It is stronger than the present manuscript requires.
- **Full mathematical closure** would prove existence, uniqueness,
  convergence, and global control for the unreduced nonlinear continuum
  problem. This project does not claim it.

The present paper should push the one-scale symplectic analysis to an exact
frontier and prove through its claim ledger that the unresolved connection is
not a hidden premise of the leading field, Jacobian plateau, energy relation,
or exact opening-block pairing. A two-scale polyhomogeneous/switchback
endpoint state, retained-`C_s` intermediate deck, singular dual normalization,
and composite PK1/FEM matching belong to a future paper.

**Established at the stated evidence level:**

- The formal leading opening, r⁵ᐟ⁴ constraint-active residual, and first forced
  correction on the chosen `C_s = 0` analytic outer representative, together
  with the parameter-free energy and stress relations.
- The leading energy flux on the superposed truncated map: an exact
  Laurent-coefficient audit gives `G = (π/2)c₁P²`, independent of `C_s`, c₂,
  g, g′, and the normalized r⁵ᐟ⁴ amplitude used in that audit. This is not a
  completed retained-`C_s`, finite-compliance equilibrium branch.
- The strip G/P/J validation, the finite-window diagnosis of the omitted
  s-like background, and matching-circle support for the exact-axis r⁵ᐟ⁴
  class and its parameter-free amplitude. The full-angle field is consistent
  with the ODE family when `C_h` is retained, but the evidence does not select
  that coefficient or validate a universal raw profile. The auxiliary disk is
  outside the current quantitative validation while its global branch and
  inner field are assessed separately.
- The exact opening-block pairing and its 3/2 − Λ duality.
- At the opening-block pencil label `Lambda = 13/4`, corresponding to opening
  power r⁵ᐟ², the resonance and its compatibility condition are exact. On the
  chosen `C_s = 0` representative, the restricted `rho*stationary` scalar
  source has a numerically converged nonzero compatibility projection, so that
  formal coefficient requires a generalized r⁵ᐟ² log(r/r₀) opening
  contribution.
  This is a coefficient- and sector-qualified result, not a completed coupled
  field or a universal physical logarithm.
- The Gate-1 reaction-carrying constrained Hessian DAE and Gate-2 off-shell
  Green identity on their declared provisional outer endpoint domain.
- The Gate-3 selected `B` seed and first source-resolved handoff, including
  its polyhomogeneous endpoint current and formal Fredholm data.
- For the stated one-scale `Pi1` connection equation, the exact tail/parity
  defect `Pi1'(0) = -5/2`. This is an obstruction result, not Gate-6 closure.
- The Gate-5A normalized isolated-opening projectors and source/face ledger;
  these are extraction infrastructure, not a mixed physical extractor.
- The normalized outer base multiplier of the *formal leading constrained
  action* and its non-smooth endpoint incompatibility.
- The analytic families of the five-row scaffold, as candidate locations and
  regularity diagnostics rather than a complete physical spectrum.
- For each integer shear Qₖ, k ≥ 2, the leading constraint/row-one reaction and
  canonical momentum, followed by its unique first constrained-action slaved
  opening.
- The complete first material order in c₂/c₁ of the Qₖ block at label
  k + 1/2.
- The constraint/row-one companions at label k + 3/2, within the stated
  analytic-even/Puiseux-log endpoint class. Their normalized multiplier obeys
  Hₖ(π) = 20k g(π). The transport *can* generate a
  θ^(2k+2)log|θ| term; its selected coefficient was found numerically nonzero
  for Q₂ and Q₃, not proved nonzero for the whole family.

**Still open:**

- Total Gate 4: the all-source background/material/`B`/`Q_k` recursion and its
  assembled Fredholm conditions.
- At `Lambda = 13/4`, the total same-grade multi-sector defect, sourced
  coupled response, total-traction selection, and physically selected net
  logarithmic amplitude. The restricted scalar result does not close any of
  these objects.
- Higher material orders of the k + 1/2 block.
- The generic row-two family generated at k + 3 and its later tower. The
  representative k = 2 rung closes formally, but does not establish the
  all-`k`, all-source recursion.
- The *physical finite-compliance* endpoint domain and its inner symplectic
  boundary form. The formal outer operator/current does not supply this datum.
- Mixed reaction-carrying extraction integrals and controlled finite-radius
  error laws for the higher parameters.
- Whether a specimen actually excites the candidate amplitudes B and Qₖ.
- The full k = 1 characteristic-shear completion and whether global matching
  selects `C_s = 0`; without that selection the raw deformed face has exponent
  1/2 rather than 2/5.
- A uniform finite-c₂ existence and matching analysis that connects the outer
  constrained field, any shrinking angular/core layers, and the global
  specimen while determining `C_s`.
- The nonanalytic same-grade or reordered sector that must absorb the exact
  parity-repair switchback; regular analytic backgrounds have been excluded at
  this grade.
- The two-scale repair of the exact `Pi1'(0) = -5/2` parity/tail mismatch and
  every later endpoint coefficient that depends on that repair.

The core G/P/J relations survive the leading-map null addition. The formal
r⁵ᐟ⁴ residual is retained on the chosen `C_s = 0` analytic representative,
while its placement in a completed k = 1 branch with nonzero `C_s` remains
open. The higher amplitudes are
candidates, not established universal second parameters. That separation
between result and program is part of the review process.

---

# Part II — Technical Lessons

---

## 6. Correct Equations Can Still Form a Contradictory Paper

An early independent AI verification pass reproduced every equation it checked
and declared the manuscript submission-ready. A structural review found that
the level table, selection principle, and printed spectrum were jointly
inconsistent: the text called B a free level-one amplitude, but the admissible
opening harmonic at that level violates the traction-free face condition.
The free opening harmonic belongs at level two, with ν = 3/2 and weighted
label Λ = 9/4.

No arithmetic check of any one displayed equation was guaranteed to catch
this. The error lived *between* individually plausible statements.

**Lesson:** equation verification and cross-claim consistency are different
tests. A positive verdict may only be read as broadly as the reviewer's probes
could have falsified.

A post-correction hostile audit found a smaller version of the same failure in
the retained opening block. The manuscript introduced the separated angular
shape `b(θ)` and then wrote its radial momentum as `∂ξb`; taken literally that
derivative is zero. The duality `Λ′ = 3/2 − Λ` was nevertheless correct because
the verification calculation had implicitly restored the radial exponential.
The printed definition was repaired by writing the full field
`u₂ = exp[(Λ−3/4)ξ]b(θ)` and `τ₂ = ∂ξu₂`, and the gate was changed to operate
on those full fields. This did not alter the leading crack-tip physics, but it
exposed a useful type error: after separation of variables, an angular
eigenfunction and the physical field it parametrizes are not interchangeable.
Verification should differentiate the same mathematical object that the paper
defines, not an implicitly reconstructed one.

The final wording audit exposed the semantic counterpart of that type error:
the manuscript called the `C_s = 0` field “selected by the asymptotic balance”
even though the next sentence correctly said that the same local balance leaves
`C_s` undetermined. “Selected” is not a decorative synonym for “chosen.” It
must name a selector—local balance, regular-axis continuation, global matching,
or an imposed boundary condition. The manuscript now calls `C_s = 0` a chosen
representative and reserves selection language for the operation that actually
performs it.

## 7. A Unit Gauge Hid a Missing Amplitude

One revision corrected the hierarchy but introduced a new dimensional error:
the level-one in-plane correction lost P⁻³ᐟ². The derivation archive mostly
used P = 1, so the missing factor was invisible there.

GPT/Codex varied P in the complete stress and recovered the exponent
numerically. Kimi independently restored the dimensions from the relative
correction scaling. The two routes agreed. Provenance review then showed that
the error was not inherited from the original derivation; it had been created
by the attempted fix.

The durable rule became stronger than “check dimensions.” Any result promoted
from a unit gauge must restore every amplitude and material scale explicitly,
then be tested with those scales varied. A unit-gauge script can establish an
angular identity while being unable to certify its physical prefactor.

## 8. A True Premise Is Not a Sufficient Argument

The Qₖ shears are functions of the characteristic coordinate s. Their angular
derivative vanishes at the crack faces. One review verified that fact and
endorsed the conclusion that the shears add no face load.

The premise was true; the conclusion was not generally justified. In a
nonlinear material, the tangent moduli couple a surviving radial gradient into
the angular nominal traction. Direct differentiation of the complete stress
exposed the missing term. The corrected statement had to be made order by
order, using the total elastic-plus-reaction traction at that order.

**Lesson:** checking that a stated reason is true is not the same as checking
that it is sufficient. Derive the claimed observable from the constitutive
law, especially when nonlinear coupling can bypass the intuitive route.

## 9. A Fitted Coefficient Is Not Automatically an Asymptotic Coefficient

The first forced opening correction predicts a crack-face term
−(2/3)(c₂/c₁)r. The FEM already used a two-term fit,

```text
y₂|face = P r^(1/2) + C r,
```

so it was tempting to report C as a zero-cost validation of the forced
coefficient. The control calculation prevented that claim. A c₂ = 0 specimen,
for which the forced Mooney–Rivlin term does not exist, returned a comparable
nonzero C. The finite-window fit also absorbs a smooth specimen-scale
background in the same radial slot.

The two-term fit remains useful because it reduces bias in P. It does not
isolate the inner level-one coefficient.

**Lesson:** a regression coefficient equals an asymptotic coefficient only
when the fitted model contains every same-order contribution. A control that
removes the proposed mechanism is often the fastest completeness test.

## 10. A General Theorem Is Not a Specific Reduction

The abstract constrained action has a symmetric second variation and hence a
Lagrange identity. The manuscript initially treated this as proof that its
five-row scaffold was the canonical Hamiltonian reduction. The missing step
was precisely the hard one: deriving the weighted momenta and endpoint domain
for this singular constrained limit.

An executable interior reduction confirmed the opening and constraint rows
but refuted the full identification. The canonical in-plane momentum carries
reaction content; the scaffold momentum does not. The reaction is slaved and
forced, not an independent homogeneous row in the way the scaffold suggested.

The generic theorem and the scaffold were each useful. The asserted map
between them was wrong.

**Lesson:** verify an identification between a theorem and a concrete system
as carefully as either object. “This system has the structure of…” is a
technical claim, not explanatory prose.

## 11. Degenerate Endpoints Decide the Admissible Theory

Several apparently numerical errors were endpoint-selection errors. The base
multiplier's regular branch was first integrated from a limiting algebraic
value at the symmetry axis and gave ψ_reg(π) ≈ 9.849. A closed-form substitution
showed that the exact value is ψ_reg(π) = 10. The traction-free total multiplier
is ψ₀ = ψ_reg − 10f³ᐟ² and therefore ψ₀(π) = 0. The axis is degenerate: a small
initialization defect excites a θ³ᐟ² homogeneous component and becomes O(1)
at the face.

The later Qₖ companion exposed two further issues. First, uniqueness of an
endpoint boundary-value problem does not imply that an outward initial-value
integration is stable; the stable calculation runs in the direction that
damps the excluded homogeneous branch. Second, an even multiplier can contain
both Puiseux behavior and a higher logarithmic resonance. Prohibiting
logarithms would turn the selected Q₂ and Q₃ solutions into incompatibilities.

A hostile audit also found that a series had been truncated too early before
division by a vanishing f² factor. A coefficient that looked “higher order” in
the numerator entered a lower reported coefficient after division.

**Lesson:** at a degenerate endpoint, the admissible function class, series
depth, and stable integration direction are part of the physics. They are not
solver details to be chosen after the operator is written.

## 12. Find the Carrier by Decomposing the Flux

Evaluating the full stress on the truncated leading map gives an r¹ᐟ² excess
in the finite-radius energy integral. This is a truncation diagnostic; the
J-integral of an exact equilibrated solution remains path-independent. The
excess's mechanism was misidentified twice. First it was attributed to a
reaction-dominated row-one term. After that was corrected, it was attributed
to an on-manifold c₂ energy term of the right magnitude.

Both explanations followed power counting. Both were wrong. The first used an
interpolation that violated the exact constraint and amplified the error
through a penalty term. The second ignored the cos θ projection in the
J-integral: the angle-independent energy term integrates to zero. Component
decomposition showed that the positive finite-radius excess is carried by the
opening-row c₂ traction contribution πc₂P r¹ᐟ².

**Lesson:** scaling identifies candidates, not carriers. Establish a signed
flux mechanism by decomposing the actual integrand, including its angular
projection.

## 13. A Closed Rung Is Not a Closed Tower

The integer shears Qₖ, k ≥ 2, initially appeared as reaction-free scaffold
modes. The separate leading-constraint-compatible k = 1 candidate/null
direction `C_s s` is not the normalization P⁻¹ᐟ² of the r⁵ᐟ⁴ slave field;
treating both as a gauge helped
hide the raw-profile error described below. The corrected action calculation
for k ≥ 2 found two ordered consequences rather than a single closed tower:

```text
bare Qₖ shear
  ├─→ leading constrained-action row-one reaction and momentum
  │     → row-two residual and slaved opening
  │     → constraint/row-one companions at k + 3/2
  │     → generated row-two source at k + 3 (open)
  └─→ direct/full-MR first-material-order block at k + 1/2.
```

The k + 3/2 companions are uniquely selected at their current balance within
an explicitly stated endpoint class. They do not make Qₖ a completed
standalone eigenmode of an infinite coupled operator. The newly generated
k + 3 load belongs to the next rung and must not be imposed as an extra
condition on the current one.

**Lesson:** asymptotic closure is indexed by powers and rows. State exactly
which balance is closed. A later residual is a source for the next problem,
not evidence that the current solution failed — and not permission to claim
the whole tower succeeded.

## 14. Fix Passes, Stale State, and Blind Gates Are New Error Surfaces

The review did not follow a clean sequence of “find error, remove error.” The
first major fix introduced the *omission* of P⁻³ᐟ² and an over-strong traction
claim. The next erratum introduced an incorrect in-plane dual label. Later,
the mathematics advanced faster than the manuscript: first the body lagged,
then the conclusion, then the README and knowledge map.

File state caused a second class of failure. The revision executor once
reviewed the wrong pair of notes because its search was anchored to the wrong
timestamp. A stale legacy manuscript retained a known row-one flux error until
it was explicitly archived. One DeepSeek pass reviewed a checkout that
predated that move and reported the already-fixed file as still present. Its
note was retained as process history, not treated as final signoff.

Even executable gates were not exempt. A pre-handoff hostile audit of the
GPT-led round-three implementation found a missing ψ₀′ chain-rule term in a
helper and several assertions that merely restated definitions. The displayed
formulas survived, but the evidence was weaker than advertised; the gates were
replaced by less definition-dependent routes.

The July 19 public-companion audit exposed the same problem across data
representations. Most scalar and ray records used a 15,360-cell strip mesh,
two material-ratio records used 15,616 cells, and the full-field snapshots had
the opposite split. Reproducing one headline case therefore could not certify
the files driving the portrait and material-ratio figures. The first proposed
repair—restoring uniform 120-sector code—reproduced part of the archive but
clipped 0.47% of the baseline specimen's rectangular outer boundary. Simply
inserting two corner rays restored the rectangle but created sub-degree
sectors extending to the tip. The final construction retained 120 sectors and
aligned the nearest two rays with the corners. All 15 required solves were
rerun: 14 scalar/ray cases plus the auxiliary `NH_lam16` field-only solve.
They yielded 14 scalar JSON files, 70 ray CSVs, and six field NPZ snapshots
with mesh and continuation metadata; the release-candidate gate now checks
their inventory, numerical parity, geometry, and cross-file provenance.

### A residual-field gate failed the raw observable

A still later mode-completeness audit exposed a different failure. The
leading constraint and scaffold catalog contained the regular characteristic shear
`C_s s`, but the leading physical map and raw-profile claim omitted it. The
existing data had already revealed the term: the angular-profile extraction
fitted `y₁ = c + br + ar^(5/4)` and removed the linear background before
recovering `g(θ)`. Figure 8 then fitted only an offset plus r⁵ᐟ⁴, and its
numerical headline divided a face opening exponent by an in-plane exponent
measured near `θ = 2°`, where the s-mode is suppressed by
`sin²(1°) ≈ 3.0×10⁻⁴`. The plot placed a 2/5 guide where the measured
local slope happened to come closest to 2/5. Neither route tested `C_s = 0`.

An initial refit of the stored fields with the
leading-constraint-compatible face model

```text
y₁ = c₀ + C_s r + A r^(5/4)
```

gave face-proxy coefficients `b = -1.6339` for the λ = 2 disk and
`b = -3.2402` for the λ = 1.6 strip. Across angle, the fitted linear
coefficient followed `b(θ) ≈ C_s sin²(θ/2)`, consistent with a stable
nonzero s-like background over those finite-core annuli. It does not establish
the ultimate matched `r → 0` coefficient. The raw face slopes were about 0.510
and 0.501. After subtracting the fitted linear term, fixed-r⁵ᐟ⁴ consistency
slopes were about 0.391 and 0.374; because the detrending basis imposed the
5/4 power, these are not independent exponent measurements. The evidence
family conflated two pipelines: Figure 5 deliberately removed the background
to isolate a residual, while Figure 8 omitted it and the numerical headline
combined exponents from different rays.

That quick probe was enough to falsify use of the zero-mode assumption as an
unqualified description of the stored finite-window fields, but its nuisance
treatment was not yet a release analysis. The production correction
imposed one physical `c₀` shared across five angular rays and added per-ray
and nested-window sensitivity checks. It gave face `b` values of −2.1393 and
−1.6718 for the λ = 1.5 and 2.0 disks, and −3.2684 and −3.5802 for the
λ = 1.6 and 2.2 strips. Across angle, the fitted linear coefficient collapsed
as `b(θ) ≈ C_s sin²(θ/2)`, with normalized residuals of 1.5–1.8% for the
disk and 1.1–1.4% for the strip. This is consistent with a stable nonzero
s-like background over those finite-core annuli; it does not establish the
ultimate matched `r → 0` coefficient. The production raw face slopes were
0.502–0.514. Target-free free-q fits of the detrended residual ranged from
1.236 to 1.339 across cases and windows. These estimates are evidence about
the stored finite-window fields, not a proof that the asymptotic exponent is
exactly 5/4.
No new FEM solve was needed to withdraw the universal raw-profile claim: the
stored fields already contained the missing mode. Those fields were
insufficient for a positive 5/4 verification. The later matching-circle
campaign supplied the needed new near-tip calculation and a nuisance-free
axis channel. It supports the 5/4 class and exact-axis amplitude for the
tested strip, but it still does not select the global matching coefficients
or establish a universal raw profile.

**Lesson:** asymptotic order depends on the observable. A regular mode can be
subleading relative to the singular opening gradient and leading energy
density—leaving G, the Jacobian plateau, and P intact—yet dominate a raw horizontal coordinate and
the r⁵ᐟ⁴ residual gradient. Before converting
field exponents into a visible shape law, enumerate every
lower-coordinate-order candidate compatible with the governing constraints
and fit or constrain its coefficient. A gate whose basis
omits the nuisance mode cannot falsify it; a tangent guide is visualization,
not evidence. Most importantly, a nuisance-removal operation used to isolate a
theoretical field must not be forgotten when that residual is promoted to a
physical observable.

### Boundary conditions and global injectivity are part of validation

The auxiliary disk incident exposed a failure mode that residual and
convergence checks do not detect. Its nonlinear solver found stationary
solutions of the boundary-value problem it was given, but those boundary
conditions did not represent the pure-shear experiment used to motivate the
comparison. Boundary conditions are part of the physics, not merely a
numerical container around the tip.

At higher loading, the exported upper-face vertex trace crossed itself away
from the tip. This was not contact between opposing faces. It also did not
certify the continuous quadratic boundary because the exporter interpolated
the quadratic solution onto linear vertices. The model contained no contact,
global-injectivity, bending, or stability mechanism that could select a
physical post-onset branch.

The resulting questions must be separated. Newton convergence addresses
stationarity of a discrete branch. Continuous-boundary and tangent checks
address global injectivity and stability. Nested mesh, core, and fitting-window
studies address convergence of the inner field. A globally inadmissible branch
would limit the physical interpretation of its inner field, but that does not
make inner convergence and global admissibility the same test.

The comparison also clarified what load variation can test. The normalized
local similarity exponents and angular shapes belong to the local asymptotic
problem; loading changes amplitudes, crossover scales, and global matching.
Apparent load-dependent exponents can therefore signal a changing fitting
window, an omitted regular term, or an inadmissible global branch rather than
new local physics. Here an independent review found exactly such an omission:
the legacy profile estimator left out the regular `C_s r` face contribution.

**Lesson:** validate the intended boundary-value problem before interpreting a
converged field. Check global injectivity as well as local residuals, classify
self-intersection geometrically before calling it contact, and separate
load-independent local exponents from load-dependent amplitudes and matching.
An estimator must include every lower-order term allowed in the measured
observable.

The size question also became precise. The membrane model has no intrinsic
in-plane length, so uniformly scaling the disk, slit, numerical core, and
sampling window cannot change its dimensionless solution. Every stored
tip-centered disk has `R_disk/a = 1`, because the slit runs from the center to
the rim. A genuine size study must hold crack length fixed and vary
`R_disk/a`, for example over 1, 2, and 4. Comparing the existing
`diag(1/lambda,lambda)` boundary map with `diag(1,lambda)` then separates
disk geometry from the strong crack-parallel compression of the original
loading.

### A green family can share one wrong derivation root

The Gate-6 reset exposed a failure that test-count summaries conceal. The T3
scripts agreed with one another because they inherited the same insertion map:
the same polar-vector connections, the same treatment of radial differentiation,
and the same scalar target. High-precision ODE solutions, coefficient
regressions, and matching-power checks could certify that implementation while
remaining unable to test whether its variables represented the physical
fixed-Cartesian deformation. Porting the system to JAX would have produced
faster and more accurate derivatives of the wrong residual.

The corrective test changed the derivation root. One route differentiated the
exact reduced energy to physical PK1 and took its polar divergence; another
inserted manufactured profiles into the unexpanded stress; a third used a
different numerical gauge. Only after those routes agreed was the new cusp
operator promoted. The subsequent Green identity did not merely report that a
boundary solver failed. It returned the exact defect `Pi1'(0) = -5/2`, showing
which pair of one-scale conditions cannot coexist.

**Lesson:** independence is structural, not social. Two agents, solvers, or
scripts are not independent when they reuse the same coordinate map or reduced
generator. Every new variable reduction needs at least one audit that begins
again at the physical action or stress, states which basis rotates, and keeps
the physical coordinate held fixed during differentiation. A verified
obstruction is a stronger endpoint than a converged solution of an assumed
equation.

This is also a publication-risk lesson. The unconditional raw 2/5 profile,
the scaffold/full-operator identification, and the T3 physical axis target all
reached polished, internally checked states before a root-changing audit found
the missing alternative. None was an obvious algebraic typo. A reviewer given
only a conventional manuscript could reasonably miss a constraint-null mode,
a theorem-to-operator gap, or a coordinate-map error distributed across a
derivation archive. That possibility does not lower the standard; it places
the burden on the authors to perform the hostile audit before release. In this
project, stopping at the first green candidate could have placed a partially
wrong result in the literature.

Near-submission status therefore became a trigger for four attacks: enumerate
every lower-order mode visible in the claimed observable, restart one route at
the physical energy or PK1, derive the endpoint domain with an exact Green
test, and inspect the immutable tree that would actually ship. A bounded paper
may still stop short of the future two-scale problem, but any new finding that
reconnects to a printed claim revokes the release state immediately.

Separately, the July 19 audit caught prose quantifiers that were stronger than
their evidence. The radial-mesh study supports the representative `λ = 1.6`,
`c₁ = c₂` case, not every reported case. The no-compression statement applies
to the sampled `c₂ > 0` strip fields; the auxiliary control reaches a small
`0.993` chord stretch only on a specimen-scale interval outside the near-tip
windows. Most importantly, a numerical window below `t_s` probes the reduced
model's formal limit, not a physically accessible two-dimensional field.

**Lesson:** a fix is a new change set, a review is a new claim, and a test is a
new artifact. Each needs its own provenance and adversarial check. A verdict is
state-bound: its minimum coordinates are the claim scope, commit, environment,
command, and input/output manifest. It cannot be inherited by a later checkout
merely because the filenames and headline values look unchanged. Inspect the
file that actually ships, then sweep the body, conclusion, status documents,
and data-availability language together.

### A passing recurrence can share the derivative map it should audit

A later `Lambda = 13/4` tranche made the shared-oracle problem unusually
concrete. Its imported implementation reported 58/58 exact self-gates and 5/5
numerical self-gates. Those counts were accurate for the implemented objects,
but three quantities were reused in ways the gates did not challenge.
First, a derivative-free Fredholm defect and its raw projection were treated
as the same normalization operand even though they differ by the opening
exponent. Second, a stored reaction field already contained an inherited
amplitude direction, which was appended a second time. Third, the symbolic
angular derivative map sent `w` to `w'` and `v` to `v'` but supplied no
successors for those derivative variables when they entered the stress.

The recurrence generated from that incomplete map could still have zero
residual under the same map. Likewise, tests assembled from the twice-counted
field could verify coefficients of the field they were given. The green
result therefore established internal consistency of a representation, not
completeness of the governing derivative chain or uniqueness of the amplitude
assembly.

The publication check supplied a smaller version of the same failure mode. An
initial “clean-clone” command created an isolated clone but did not change into
it before running the checks, so it actually retested the source worktree. That
run was discarded. The replacement printed and verified both its working
directory and exact commit before executing the full release circuit.

The decisive audits changed the probes rather than increasing their number. A
typed normalization check kept the two defect definitions separate.
Unit-direction differentiation exposed the doubled inherited amplitude.
A jet-closure audit enumerated every free field and required its angular
successor, while a separate route substituted the full profiles into the
unreduced angular stress and differentiated that expression directly. These
checks corrected the implemented recurrence, but the corrected route still
reused lower profiles and source construction from the imported route. It was
a repair, not an independent reproduction.

The resulting evidence boundary was deliberately narrow. The opening-block
resonance and compatibility condition are exact. For the selected
`C_s = 0`, restricted `rho*stationary` scalar coefficient, the numerically
converged nonzero compatibility projection requires a logarithmic generalized
contribution. The total same-grade source, sourced coupled response,
total-traction-selected reaction, and physical net logarithmic amplitude
remain open. No provisional higher-order coefficient was promoted.

A separate scope adjudication received five concrete disputed propositions,
not a request to rerun the calculation. It upheld this narrower boundary and
corrected overstatements in the earlier review handoff itself. The adjudication
therefore closed the publication claim while leaving the unfinished
mathematics explicitly open.

The human scientific owner chose to stop this calculation because none of the
manuscript's leading-field, flux, Jacobian, or exact opening-pairing claims
depends on uncertified `Lambda = 13/4` completion. This was an evidence and
scope decision, not a claim that the missing coefficient is physically
unobservable or that the higher hierarchy cannot be completed.

**Lesson:** self-tests establish implemented scope, not omitted completeness.
Give mathematically different quantities distinct types, differentiate a
completed field with respect to each inherited amplitude before adding another
copy, and require symbolic derivative maps to be closed over every jet
variable they consume. Treat execution context the same way: a clean-clone
claim must assert the working directory and commit it actually tested. After a
repair, distinguish exact algebraic correction from independent derivation and
from numerical certification. A bounded stop is scientifically useful when
the open dependency is explicit and no printed claim relies on it.

---

# Part III — Collaboration Patterns

---

## 15. The Multi-AI Review Loop

The stable workflow eventually had four explicit roles:

1. **Deriver:** produce equations, code, and a note naming the weakest points.
2. **Verifier:** reproduce the result by a distinct route where possible and
   attack the named weak points.
3. **Executor:** disposition findings, update the shipping files, run the full
   regression set, and record what remains unverified.
4. **Human meta-reviewer:** decide scope, route attention, adjudicate with
   artifacts, and stop the loop.

The role assignment changed. Fable began as the principal executor and
author-side responder; Codex began as the structural reviewer. After the
review record showed a persistent division of strengths, Teng explicitly
swapped them for the later Qₖ rounds: Codex led the derivation, and Fable
became the adversarial verifier and shipping executor. The invariant was not
which model held which title. It was that the deriver did not sign off alone.

Load-bearing algebraic and numerical disagreements were not settled by a vote.
They were converted into checks:
vary P outside the unit gauge; differentiate the full nominal stress; run the
c₂ = 0 control; reconstruct the endpoint series; decompose the flux; solve the
same face identity by another route. The manuscript-level suite grew from 31
to 59 checks, while specialized analysis scripts carried deeper derivations.
Those counts are coverage descriptions, not proof by quantity: some checks
encode printed identities, some independently derive them, and some are
sampled numerical regressions. The corrected manuscript and ESI label those
levels rather than calling every assertion an independent proof.

The workflow therefore combined a dependency-ordered claim graph with a closed
release circuit, rather than a flat checklist. The release circuit was:

```text
candidate hashes
  → analytic identities
  → semantic and cross-artifact provenance
  → deterministic regeneration
  → candidate hashes unchanged
```

An upstream scientific failure revoked dependent claim passes; a material
release change returned the candidate to the full circuit, even when some
downstream checks still appeared green. Multiple gates were treated as
stronger evidence only to the extent that their failure modes did not share the
same equation, code path, basis, or fixed gauge.

The July 19 release candidate made the relational character of evidence
visible. The claim ledger and code/evidence map declared the scope; gates checked
raw-to-summary, figure-to-input, and artifact-to-protocol edges; nested content
locks pinned the resulting bytes. Checksums establish byte identity; semantic
gates test a coherent evidence family only within their encoded model and
scope. The `C_s s` incident showed that the gate model itself also needs a
constraint-compatible candidate-mode audit. Neither kind of gate substitutes
for the other.
In claim-graph terms, the missing edge was not equation-to-equation but
field-to-measurement: a null direction for the determinant remained visible in
the camera coordinate. Release design now requires an explicit audit of every
constraint-compatible mode below the claimed observable order, followed by a
target-free fit or a proof that matching kills its coefficient.
Likewise, fast reproduction from curated arrays and an expensive fresh
finite-element solve are separate lanes: one checks the curated evidence
against its derived summaries and regenerates its figures, while the other
tests whether the underlying computation can reproduce that evidence.

## 16. Different Review Styles Saw Different Failure Classes

In this project sample, Codex reviews emphasized frame attack: varying
quantities that an archive had fixed, reading one manuscript claim against
another, and asking whether a true argument was sufficient. That style exposed
the misplaced B, missing P factor, channel-dependent duality, full-stress
traction term, and scaffold/operator gap. Some passes did not consult every
archive record before presenting alternatives.

Kimi reviews emphasized exact reproduction: checking numbers to the digit,
running existing suites, comparing prose with the line the solver executes,
and finding the P1-versus-P2 finite-element mismatch. Some verdicts generalized
“every probe I ran passed” into “the manuscript is sound,” even when the probe
family could not detect a cross-claim contradiction or an omitted constitutive
term.

Fable's principal role was integration: building symbolic and FEM
infrastructure, applying dispositions, and eventually synchronizing the
manuscript and code after several documented lags. It also introduced errors
during ambitious fix passes and once missed an already-present review file.
Its later hostile review of Codex's derivation had explicit roles and requested
falsification targets.

DeepSeek provided broad end-to-end reads and a late pre-submission audit of the
then-current theory and manuscript tree. Its early passes had narrower
evidentiary scope—one lacked SymPy execution and one used a stale checkout—than
the later pass on the pinned tree. GLM and Opus supplied earlier referee-style
pressure.

After the recorded signoff, a separate ChatGPT review compared the Λ = 1 mode
catalog with the physical crack-face observable and challenged the omitted
`C_s s` term. Codex then tested that objection against both FEM geometries and
the figure/test code, finding finite-window consistency with a nonzero s-like
background and exposing the blind raw-profile gate. The full matched k = 1
branch remains
open. This late finding did not rank one reviewer above the others; it used a
probe that the earlier rounds had not posed.

These differences were stage-dependent as well as reviewer-dependent. Early
review was most valuable when it challenged framing and claim scope; middle
rounds needed dependency-local derivations, admissibility checks, and distinct
falsification routes; integration review had to chase contradictions across
the manuscript; release review had to inspect the pinned shipping tree, data
bindings, regenerated figures, and history boundary. The late reviewer also
inherited a more mature artifact and the gates then available, built by earlier
rounds. A verdict therefore belongs to a **model–stage–artifact–probe tuple**,
not to a model alone. These observations are not a general ranking of models.

## 17. Where AI Failed, Specifically

**It inherited the manuscript's frame.** “Compliance,” “full symplectic
operator,” and “free mode” were sometimes treated as definitions rather than
claims to test.

**It confused premise verification with validity.** Confirming that an
angular derivative vanishes did not establish a nonlinear traction statement.

**It assumed fitted models were complete.** A same-order outer background was
invisible until a mechanism-removing control was run.

**It verified a residual and promoted it to a raw observable.** One pipeline
removed an O(r) background to recover the r⁵ᐟ⁴ field. Another omitted that
background, combined exponents from different rays, and called the result a
camera-visible 2/5 face profile.

**It made quantifier jumps.** One verified dual pair became a universal
duality rule; selected nonzero Q₂/Q₃ logarithmic residues risked becoming a
family theorem; a rung closure risked becoming a complete spectrum.

**It generated new errors while correcting old ones.** This was not an edge
case but a repeated pattern. Fast editing increased the surface area that had
to be reviewed.

**It reviewed stale or wrong artifacts.** Memory, timestamps, and plausible
filenames were unreliable substitutes for checking the current tree and
commit.

**It over-trusted executable checks.** A check can share algebra or code with
the claim it “verifies.” Until the dependency is examined, a passing gate may
certify transcription rather than truth.

**It confused available hardware with executed parallelism.** An early
full-domain refinement used 42,240 triangles and 170,146 quadratic
displacement degrees of freedom before boundary conditions, but it was
launched on one MPI rank and used about 1.3 of the machine's 64 available
cores. Repeated serial sparse-direct factorizations made the two-dimensional
problem slow. The nonlinear solve reached the target load, but the exporter
rejected 402 of 43,440 requested samples, so no scientific fit was accepted
from that run. The later MPI-safe path used root-owned mesh distribution,
MUMPS, distributed point ownership, root-only output, and one BLAS/OpenMP
thread per rank. Its final 16-rank strip solve took 29.4 seconds. Hardware
allocation, process activity, solver exit, and validated scientific output
are four different facts.

**It became defensive when a result was challenged.** Removing a disputed
figure, narrowing a claim, or labeling a calculation “quarantined” reduced
immediate publication risk. In the disk episode, that response began to
replace the harder work of asking whether the observed fold came from loading,
dimensionless geometry, branch selection, missing contact or bending, or a
numerical defect. The same tendency could have erased the analytical
r⁵ᐟ⁴ residual merely because the available finite window could not yet
separate it from an allowed O(r) motion. Claim control is necessary, but it is
not mechanism discovery.

The corrected process used four dispositions: **false**, **unsupported**,
**conditional**, and **open but testable**. False results were retracted.
Unsupported results were demoted, conditional results retained their
assumptions, and open results received discriminating tests. This prevented
editorial risk control from being mistaken for a physical explanation.

**The workflow had no intrinsic stopping condition.** The Qₖ campaign could
always generate one more rung. The stopping decision required scientific
judgment about what the paper needed, what numerics could safely take over, and
what a referee should be allowed to ask for.

## 18. The Human's Critical Contributions

The human interventions with the highest leverage were not long derivations.
They were questions about process and epistemic status.

**“Read very carefully; there are serious mistakes.”** This forced an
adversarial self-audit after a superficially successful revision.

**“Did you read the two reviews just in?”** This exposed that the executor had
reviewed the wrong files. Without that attention-routing correction, two
independent reports containing the missing P factor would have remained
unused.

**“Was it an old error?”** Provenance mattered because it showed that the
revision process itself had created the dimensional mistake. The response was
therefore to review fixes as new work, not merely to patch the original text.

**“Program versus result.”** Teng required the manuscript to distinguish the
exact opening block, the formal constrained-action Qₖ responses, the spectral
scaffold, and the still-open full operator. This was a scientific positioning
decision, not copyediting.

**“How far are we from closing the problem?”** This question converted a long
list of candidate calculations into the six dependency-ordered gates. It also
forced each checkpoint to say whether it closed an operator, an endpoint
domain, one sourced rung, an extractor, or a matched physical branch.

**“This is a reduced model, not full mathematical closure.”** Teng rejected a
misleading use of “full closure” and separated manuscript readiness, six-gate
reduced-model closure, and existence/convergence for the unreduced PDE.

**“The two-scale problem can be a future paper.”** Once the exact one-scale
parity/tail defect was identified, this set a principled stopping boundary.
The present work must state the obstruction and protect its claim ledger; it
need not hide a second research paper inside the current submission.

**“Do not solve trouble by removing it.”** When the disk branch and the
two-term face field became difficult to interpret, Teng rejected the emerging
defensive strategy. The revised instruction was to retain the physical
observation, enumerate mechanisms, and define discriminating numerical tests.
For the disk, this means separating discrete stationarity, global
admissibility or contact, and inner-field convergence, then varying the
outer-radius-to-crack-length ratio and remote loading. For the face field, it
means fitting the regular O(r) motion and r⁵ᐟ⁴ residual together. This
intervention changed a manuscript-protection exercise back into a research
program.

**“Pause and submit.”** The theory–verification loop had no natural terminal
rung. Teng first wrote a stopping line — analysis for endpoint solvability and
conservation, numerics for a well-posed spectrum. At that stage, none of the
recognized unfinished higher-order blocks fed the printed G/J/P core, so Teng
paused the tower extension and designated external review as the next
instrument. In this record that meant another independent AI review, not
journal peer review. The later `C_s s` audit showed that the broader raw-shape claim
still depended on an unclosed matching coefficient, and the signoff was
reopened.

This separated three decisions that are often collapsed. **Review again** when
a promoted result lacks a discriminating falsification route adequate to its
scope. **Continue** when an unresolved claim or failed gate lies on the
dependency path of a claim the paper needs. **Release** when the bounded claim
subgraph passes its full circuit, its load-bearing gates have been audited for
omitted leading-constraint-compatible directions, and all remaining open work
has been scoped out of the shipping claims and named explicitly. Release
readiness is not research
completion: the verified G/J/P core could be frozen and shared while the full
finite-compliance matched hierarchy remained an open program, but only after a
G/J/P-only artifact had been synchronized and passed its corrected release
circuit.

The human also owned the physical problem, the manuscript's claims, the
choice of which FEM comparisons counted as validation, and the final decision
that an honest weaker statement was preferable to a more impressive
unsupported one. Multiple agents increased coverage; they did not replace
that ownership.

## 19. Attribution, Carefully

Teng Zhang is the author of record and the scientific and editorial lead. He
set the problem, supplied the mechanics judgment and research context, routed
the reviews, demanded provenance, chose the stopping line, and accepts
responsibility for the paper.

Fable/Claude was the principal revision executor and infrastructure builder
through most of the campaign. It integrated symbolic checks, FEM evidence,
review dispositions, and manuscript revisions. Several important errors
introduced during its fix passes were caught in subsequent rounds.

Codex/GPT began as the structural falsifier and later, by explicit human
decision, led the Qₖ and six-gate derivation rounds. It contributed the
action/scaffold distinction, dimensional and full-stress attacks, exact
endpoint and flux checks, the reaction-carrying Gate-1/2 construction, and the
fixed-Cartesian Gate-6 reset. In the subsequent release work, it also helped
formalize the multi-gate circuit. Fable reviewed promoted results at the scope
recorded in each handoff; the later k + 3/2 construction received a dedicated
PASS before manuscript integration.

Kimi supplied independent reproduction and code-versus-text checks in the
early rounds, including an independent route to P⁻³ᐟ² and the P2 element
correction. In the July 21–22 campaign Kimi also performed a hostile Gate-3
review, rebuilt early Gate-4 rungs, and independently confirmed both the
`Lambda = 17/4` formal outer obstruction and the later `Pi1'(0) = -5/2`
one-scale connection defect. Kimi's named 13/4 branch then supplied the
restricted resonance tranche. Codex's repair and a broader source audit found
the defects and scope gap described above, and Kimi independently confirmed
the three algebra/implementation errors. Kimi later added the asymptotic map
and closed 7/4 rung to the manuscript, ran the first bounded FEM pilot, and
reviewed the final matching-circle figure. Codex implemented the
verification-grade matching-circle campaign and integrated the review. Fable
performed the final line-by-line and pre-submission audits.

DeepSeek/OpenCode performed the late end-to-end audits. Its third
pass reviewed the then-current theory/manuscript tree at `74edb13` and reported
“Ready for submission.” That verdict predates the July 19 mesh-provenance,
data, figure, and scope corrections and is not a review of public-companion
commit `3369dbc`. It also predates the July 20 `C_s s` audit, its required
withdrawal of the raw Figure 8 claim, and the subsequently implemented
manuscript/ESI and local-companion correction. One intermediate DeepSeek
review used stale state
and was retained as history rather than authority. GLM and Opus contributed
earlier referee reports. The external ChatGPT report supplied by Teng exposed
the `C_s s` issue; Codex confirmed the finite-window s-like background and the
blind gate against the stored fields and code. These were AI review results
before journal peer review, not proof statements or external signoff.

Line-level authorship cannot be reconstructed reliably from a shared working
tree, and this case study does not assign it. All research-repository Git
commits use Teng Zhang's author identity. Agent attribution comes instead
from signed note headers, named branch handoffs, commit subjects, and
self-reports checked against executables and later reviews. The record does
not preserve complete raw conversations, exact task timing, or reliable model
build identifiers. Some source records were drafted by the same agents they
assess, so their evaluative claims were checked against the round-by-round
record before being used here. The defensible attribution is layered: human
scientific ownership and termination, AI-assisted derivation and integration,
independent calculation-specific checks, and final human responsibility.

The process reports themselves were not exempt. Kimi's signed July 24 report
was preserved at `b03d249`. A separate signed Codex report recorded eight
factual corrections, including the restricted source census, the distinction
between one convention error and two implementation defects, the manuscript
page count, the final release commit, and the status of the disk trace. The
earlier report was not silently rewritten. A signed narrative is provenance,
not self-validating evidence.

Two statements coexist. No individual AI verdict was trustworthy without an
artifact capable of falsifying it. The calculations emerged through documented
handoffs among participants. The central load-bearing derivations described
here were not promoted from one agent's assertion alone; the recorded final
claim set attaches an independent review or executable cross-check to them.
That record is not proof that every possible dependency was found. The
transferable result is the protocol that allowed both statements to coexist.

---

# Part IV — Closing the Verification Loop

---

## 20. Remove Nuisance Directions Before Estimating a Singular Power

The fixed-core strip data did something scientifically useful even when they
could not resolve 5/4. They showed why the old estimator was ill posed. The
regular `C_s r sin²(θ/2)` field and the r⁵ᐟ⁴ residual are strongly correlated
over a short radial window, and a fixed-r⁵ᐟ⁴ detrending basis cannot
independently rediscover the exponent it assumes.

The human intervention was not “trust the analytical result anyway.” It was
to ask for a numerical problem in which the global specimen selects the
boundary data while the local observable removes the unresolved amplitudes.
That led to a one-way matching-circle construction. Four related routes
must be kept distinct:

| Calculation | What changes | Role |
|---|---|---|
| Tip/core-refined global strip | Matching radius, core radius, or angular resolution in the full strip mesh | Supplies the convergence sequence and the complete live-P2 trace |
| Exact inner restriction | Reuses and re-solves the strip cells inside the matching circle | Supplies the accepted profiles and checks transfer and interface equilibrium; it adds no independent mesh resolution |
| Independently refined local solve | Refines the local cells at a fixed core while holding the outer strip unchanged | Diagnostic one-way submodel only; it is not used in the reported exponent sequence |
| Future two-way coupling | Would return local reaction changes to the outer strip | Not implemented and not needed for the present exact-axis claim |

This is not a disk loaded by an analytical tip field. The nonlinear strip is
the outer solution. Its exact restriction receives the complete P2 trace,
uses the transferred field as its initial state, and solves again at the final
load. Core convergence comes from rebuilding the global strip, not from
calling the restricted solve “refined.” The separate refined local diagnostic
ended with a positive Jacobian but a 2.10% P2 reaction-coefficient defect
relative to the unchanged strip. That coefficient-vector norm is not a
mesh-invariant 2.10% traction error, but it shows why one-way displacement
transfer is not two-way equilibrium.

The implementation checks the interface before interpreting the exponent.
For the final case, the manufactured P2 transfer error is
`1.69×10⁻¹⁵`, the imposed trace error is zero to stored precision, all
28,960 polar samples are valid, and the exact-restriction reaction-coefficient
defect is `4.21×10⁻⁹`. The production calculation used 16 MPI ranks, 15,360
global strip triangles, and 10,320 triangles in the exact local restriction.

The campaign then separates three kinds of convergence:

- `R-`, `1`, and `R+` vary the matching radius from `0.005h` to `0.02h`;
- cases `1`, `2`, and `3` reduce the inner core from `10⁻⁵h` to
  `2.5×10⁻⁶h`; and
- case `4` holds the smallest core and doubles the angular resolution from
  60 to 120 sectors.

The three radial windows are overlapping post-processing intervals on each
field, not distinct “inner,” “middle,” and “outer” simulated annuli. The
largest matching-radius change in the fitted exponent is
`5.50×10⁻⁴`. The final exact-axis result is

```text
q = 1.251529,
A_axis/A_axis,pred = 1.012420.
```

The critical design choice is the exact axis. There,
`sin²(θ/2) = sin^(5/2)(θ/2) = 0`, so both the `C_s` term and the
`P^(-1/2) C_h` homogeneous member disappear before fitting. A second estimator
frees both radial powers and returns
`q = 1.24980–1.25152` and `p_next = 1.68971–1.74746`. This is a
cross-check of the 5/4 class and the next 7/4 slot, not a verification of the
7/4 angular profile or amplitude.

The episode changed the role of FEM. It did not “prove” the analytical
algebra. It tested whether the reduced continuum model, global strip solution,
interface transfer, and local asymptotic observable formed one consistent
chain. The result supports the 5/4 exact-axis class and its parameter-free
amplitude for the tested `c₁=c₂=1`, `λ=1.6` strip. Global selection of `C_s`
and `C_h`, two-way displacement–traction coupling, and the complete 7/4 field
remain open.

**Reusable lesson:** when an asymptotic coefficient is confounded by a
matching nullspace, more mesh alone may not identify it. First search for a
symmetry line, projection, ratio, or compensated quantity that removes the
nuisance direction exactly. Then refine the numerical problem and vary the
interface, core, angular resolution, and fitting window. Observable design is
part of numerical analysis.

---

## 21. Submission Readiness Was an Executable Checkpoint

“Submission ready” did not mean that the full higher-order program was
finished. It meant that the bounded claim graph, the exact artifacts named by
the paper, and the journal package passed a defined circuit. The closeout had
separate scientific, review, packaging, and editorial stages. The first four
hashes below identify the internal research repository; the final row is the
public companion:

| State | Recorded revision | What closed |
|---|---|---|
| Bounded scientific close | `29b8f09` | The manuscript/ESI claim set, final figures, public-version pin, and the two conditions from Fable's archived-value audit |
| Process and review record | `b3b38df` | A fact-sourced collaboration report and the scope of the final AI audit, including what was not rerun |
| Soft Matter package | `92c60e2` | Three upload files, package-relative checksums, and an isolated rebuild of the source ZIP |
| Final reference and scope pass | `bd0652c` | Rendered DOI repair, citation-scope corrections, paragraph flow, and an explicit plane-stress/plane-strain distinction |
| Public paper-facing release | `v1.2.0` at `bba3c93` | The immutable 201-file reproducibility state used by the paper |

The final private circuit passed 59/59 manuscript-relation checks, 33/33
canonical-operator checks, 26/26 endpoint-domain checks, and 38/38
symplectic-current checks. The 24-page manuscript and 11-page ESI rebuilt
without undefined references, overfull or underfull boxes, or Type 3 fonts.
The public circuit also passed all ten verification programs and the
stored-data claims gate, and the tagged 201-file manifest verified. The
submission archive contains 13 files, including eight figure PDFs, and rebuilt
both documents in an isolated directory. The journal upload set contains the
two PDFs and the source ZIP. No cover letter is included, at the author's
request.

Review scope remained attached to each verdict. Fable checked archived
matching-circle values independently and required two release actions: define
the 7/4 multiplier convention and pin the public version. It did not rerun the
FEM campaign or public analytical suite. A later ChatGPT review
read all 24 manuscript pages and 11 ESI pages, including the equations,
figures, and numerical protocol, but explicitly did not rederive every
coefficient or rerun the code. Codex checked and acted on those comments, then
ran the analytical/operator suites, stored-data claims gate, document builds,
manifest, and package checks. The FEM campaign was not rerun in this closeout.
A complete reading, a value-by-value audit, an executable identity, and a
solver rerun are useful probes with different failure modes. None should be
described as the others.

The reference pass supplied a less obvious artifact lesson. The DOLFINx DOI
already existed in the BibTeX `doi` field, but the selected bibliography style
did not print that field for an `@misc` entry. A note had to be added before
the DOI appeared in the rendered bibliography. The same pass established that
the ORBilu and Zenodo pages described one item, not two references. It added Li
and Moran only for the neo-Hookean nested-field interpretation and removed
language that could transfer a plane-strain analogy into evidence for the
paper's plane-stress constraint. Source metadata, rendered output, and
scientific citation scope are three separate checks.

The public tag and public default branch are separate on purpose. Tag
`v1.2.0` remains the paper-facing state. Public `main` later advanced to
`719a1ff` to reorganize documentation into `docs/` and repair navigation. That
documentation change does not rewrite the tagged scientific release.

**Reusable lesson:** define submission readiness as an artifact-specific
checkpoint. Record the exact claim set, reviewers' probes and omissions,
executable gates, generated PDFs, source-only rebuild, public tag, and journal
upload files. Research may continue after that checkpoint without making the
checkpoint false.

---

# Part V — Comparing Two Method-Defining Frontiers

---

## 22. Crack Tip and Wrinkle: Different Walls, the Same Standard

The crack-tip and wrinkle projects did not become important because they took
a long time or consumed many review rounds. Difficulty is evidence only when
it identifies which assumption, representation, or asymptotic scale controls
the result. A prolonged calculation inside a shared wrong frame is not deeper
than a short correct derivation. Conversely, a quick leading solution is not
shallow when its scope is stated honestly.

What makes these projects comparable is that each reached a point where the
method's name became an executable scientific claim.

| Question | Wrinkle bifurcation project | Mooney–Rivlin crack-tip project |
|---|---|---|
| Early successful object | Fourier × depth-FE calculation near the observed period-doubling range | Five-row spectral scaffold, formal outer modes, and a solved T3 scalar axis-layer target |
| What the numerics really supplied | A depth-resolved oracle showing that through-depth relaxation matters | Accurate solutions of formal outer rungs, an assumed inner ODE, and global finite-resolution FEM evidence |
| Hidden method mismatch | The paper promised analytical depth while the production unknowns were nodal through depth | The inner map treated fixed-Cartesian deformation components as rotating polar components and omitted a fixed-angle radial connection |
| Human method boundary | No depth-nodal unknowns in the selected paper method; global analytical-depth Ritz coefficients were allowed | Derive the physical inner residual from the reduced action/direct PK1 before choosing a solver; distinguish one-scale reduced-model closure from full mathematical closure |
| Rebuild | Coefficient-only analytical-depth symplectic-basis Rayleigh–Ritz state and signed Floquet Hessian | Reaction-carrying Hessian/current gates, then a fixed-Cartesian direct-PK1 cusp and exact endpoint connection audit |
| Frontier result | Retained-space analytical-depth thresholds with convergence evidence, not continuum error bounds | Exact one-scale parity/tail incompatibility; the two-scale endpoint repair remains open |

### The wrinkle wall was a method-identity wall

The wrinkle depth-FE calculation was valuable. It relaxed the depth profile,
located a plausible threshold, and acted as a numerical oracle against which
reduced spaces could be judged. But its assembled unknowns were depth-node
values, so it could not substantiate the paper's claimed analytical-depth
symplectic method. Teng's intervention was not a request for a preferred
decimal. It was a method contract: exact Hamiltonian–Stroh functions had to
provide the depth backbone, nonlinear enrichment had to be represented by
global coefficients, and stability had to come from the signed Floquet
Hessian of that retained state. Fable's difficult turnaround mattered because
it built a calculation that met that contract. The final thresholds are still
retained-space estimates rather than full continuum closure.

### The crack wall is an endpoint-uniformity wall

The crack project first appeared easier because the leading constrained field,
Jacobian plateau, and energy flux closed quickly. The difficulty entered when
the paper's larger purpose was stated: demonstrate a reusable radial
symplectic framework for a nonlinear constrained crack-tip hierarchy, rather
than solve only for one leading specimen field. That goal made `B`, `Q_k`, the
reaction-carrying momentum, the boundary current, and the degenerate endpoint
part of the method rather than optional algebra.

The formal outer gates made substantial progress. The failure occurred at the
transition from their single-angular-scale endpoint data to a smooth physical
finite-compliance axis. Unlike the wrinkle case, replacing one numerical
representation with a method-compliant one is not enough. The exact
`Pi1'(0) = -5/2` identity says that the isolated one-scale half-line problem as
posed cannot obey both required conditions. The missing object is structural: an
additional scale, switchback state, reordered background, or global datum must
enter the matching. Constructing that two-scale canonical boundary form is a
new mechanics problem and is reserved for a future paper.

### Numerical work was essential, but it answered scoped questions

Both histories reject the idea that numerical work was wasted when it failed
to become the final method. In the wrinkle project, the depth-FE oracle showed
which physical freedom the analytical basis had to recover. In the crack
project, the FEM continues to test leading finite-window observables, and the
outer ODE calculations expose endpoint powers, resonances, and candidate
connections. The archived T3 solutions also preserve useful negative controls
and matching guesses.

The authority of each result is nevertheless bounded by the equation and
state space it solved. Numerical convergence cannot derive a residual.
Automatic differentiation cannot choose the physical variables. Global FEM
agreement validates a reduced model over resolved windows; it does not prove
its singular endpoint limit. The correct sequence in both projects was

```text
physical variational statement
  -> declared variables and approximation space
  -> derived operator and boundary form
  -> independent root-changing audit
  -> numerical solution and convergence
  -> paper claim at the same scope
```

### Why the symplectic framework remains the point

The Gate-6 obstruction is not evidence that symplectic mechanics caused the
crack difficulty. The noncommuting radial, angular, and compliance limits; the
constraint-null family; endpoint logs; resonances; and global selection of
local amplitudes are already properties of the crack problem. The symplectic
formulation converts them into auditable interfaces: action to canonical
operator, operator to Green current, current to endpoint defect, and endpoint
defect to a Fredholm or matching condition. In this case the Green identity
turned a vague failure to satisfy two boundary conditions into the exact
number `-5/2`.

That is also why the framework fits AI-assisted nonlinear mechanics. Agents
can work on bounded symbolic rungs, numerical connections, and hostile
re-derivations in parallel, while the current and endpoint form provide
cross-checks. The failure mode is equally clear: many agents can share the
same reduction root. A multi-agent workflow becomes stronger only when one
route is required to restart from the physical action or stress.

### Struggle is a diagnostic, not a target

The useful comparison is therefore not that the crack project should consume
as much effort as the wrinkle project. It is that both should be pushed until
the strongest paper-facing claim has either a method-compliant construction or
a named exact obstruction. For the wrinkle project, that point was the
analytical-depth retained-space method. For the present crack paper, it is the
leading constrained solution plus exact opening-block symplectic structure,
together with an honest one-scale boundary for the unfinished higher-order
program. The future two-scale paper begins from the exact half-line
incompatibility rather than from an unexplained solver failure.

Submission, six-gate reduced-model closure, and full mathematical closure are
not synonyms. The manuscript can be ready when its bounded claim graph is
correct, reproducible, and independent of the unresolved connection. The
six-gate program can continue as a stronger method-development objective.
Existence and convergence for the unreduced nonlinear crack PDE remain beyond
both. Stating these levels is not retreat; it is what makes the framework and
the AI research record reusable by others.

---

## Summary

```text
The progression that matters:

  Two-invariant plane-stress gap
      → emergent uniaxial constraint
      → r^(1/2) opening and a formal r^(5/4) residual on a chosen C_s = 0 representative
      → 2/5 only after C_s s detrending, or if matching selects C_s = 0
      → G = (π/2)c₁P² and parameter-free strip test
      → fixed-core strip windows expose but cannot separate the nuisance motion
      → exact-axis observable removes C_s and C_h identically
      → matching-circle campaign returns q=1.251529 and amplitude ratio 1.012420
      → free two-power fit recovers 5/4 and a next slot near 7/4

  Useful five-row spectral pencil
      → initially promoted as the full symplectic operator
      → action reduction exposes reaction-carrying momentum gap
      → retained honestly as a scaffold; opening block exact

  Candidate Qₖ shears
      → reaction-free mode claim fails
      → leading reaction + slaved opening branch
      → separate first-material block at k+1/2
      → k+3/2 companions on the constrained branch
      → generated k+3 rung remains open

  Six-gate method push
      → Gates 1–2 derive the reaction-carrying Hessian DAE and Green current
      → Gate 3 closes the selected B seed and first sourced handoff
      → Gate 4 advances formal outer ladders; Gate 5A freezes isolated projectors
      → Lambda=13/4 opening resonance and compatibility are exact
      → restricted rho*stationary scalar projection is numerically converged and nonzero
      → that formal coefficient requires an r^(5/2) log r contribution
      → a shared-map audit finds a normalization mismatch, a doubled
        inherited direction, and an incomplete derivative chain
      → total coupled response and physical net log amplitude remain open
      → the bounded calculation stops because manuscript claims do not depend on it
      → Gate 6 returns to fixed-Cartesian physical PK1
      → archived T3 inner target is quarantined
      → exact Pi1'(0) = -5/2 contradicts smooth one-scale parity
      → homogeneous repair leaves exact eta^(3/2) overlap
      → regular analytic backgrounds cannot alter that Green grade
      → later outer connection data are conditional
      → two-scale endpoint construction becomes a future paper

  Manuscript review
      → local checks pass while cross-claims conflict
      → fixes introduce dimensional, traction, and duality errors
      → independent routes, controls, and component decompositions
      → a green Figure 8 gate is blind to a constraint-compatible candidate
      → audit withdraws raw shape claim; corrected artifacts are regenerated
      → the disk is recognized as a distinct loaded boundary-value problem
      → its stored vertex trace shows post-processed crossings and an unresolved global branch
      → quantitative FEM claims use the strip; disk size, loading, and admissibility remain testable
      → matching-circle campaign provides bounded verification-grade 5/4 support
      → final AI pre-submission audit conditions are resolved
      → paper-facing public state is tagged as v1.2.0
      → isolated submission build and rendered-reference audit pass
      → symplectic framework, bounded G/J/P/5/4 claims, and analytical 7/4 rung survive
```

**When AI worked well:** the claim could be attacked from a genuinely
different direction — symbolic differentiation versus dimensional
restoration, asymptotics versus FEM, total flux versus component
decomposition, endpoint recurrence versus high-precision global solution.
Generation was fast because falsification was concrete.

**When AI struggled:** the missing content was outside the frame it had been
given — an omitted constitutive coupling, an unmodeled same-order background,
a theorem-to-operator identification, a stale file, or a quantifier stronger
than the evidence. More re-reading inside the same frame did not help, and
multiple green implementations of one inherited variable map did not create
independence.

**The meta-lesson:** executable verification is essential, but “make a test”
is not the end of the scientific question. A test certifies only what it could
have falsified, on the artifact it actually exercised, at the scope its
dependencies and fitted basis permit. A residual-field check does not certify
the raw observable from which the residual was extracted. The July 20 audit
reopened the recorded pre-submission state precisely because that distinction
had not yet become a gate. The correction demonstrates the corresponding
release discipline: revoke dependent claims, repair the claim graph,
regenerate every affected artifact, and rerun the complete circuit. Reviewer
performance must also be read at its stage: a late audit can expose a
measurement-space failure partly because earlier derivation and integration
rounds made the relevant mode catalog, observable, and artifact graph
available to inspect.

The comparison with the wrinkle project sharpens the point. There, a numerical
oracle had to be separated from the analytical-depth method promised by the
paper. Here, a formally successful inner calculation had to be separated from
the physical fixed-Cartesian PK1 problem. In both cases the decisive advance
was not more computation but a method contract that made the representation
falsifiable. The time or token cost of the struggle is not evidence; the
reusable result is the exact boundary it reveals.

---

*This case study documents the Mooney–Rivlin plane-stress crack-tip project
and its intensive June–July 2026 verification campaign. The July 21–22
extension was checked against the six-gate closure plan, Gate-3 hostile review,
Gate-4 handoffs, direct-PK1 and penalty-bridge executables, the Gate-6 pivot and
one-scale cascade records, exact homogeneous-connection and analytic-
background audits, and the publication-scope decision memo. The July 23
bounded `Lambda = 13/4` review added the restricted resonance result and the
shared-derivative-map postmortem without promoting the unfinished coupled
response. The manuscript reached a recorded signoff on July 19 but had not
undergone journal peer review. The July 20 `C_s s` audit reopened that
signoff. The later matching-circle campaign provided verification-grade
support for the 5/4 exact-axis class and parameter-free amplitude, and the
bounded manuscript/ESI claim pass closed at `29b8f09`. The Soft Matter package
was assembled at `92c60e2`, and the final reference and plane-stress scope pass
closed at `bd0652c`. The
[sanitized companion repository](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip)
retains its paper-facing reproducibility state as
[version `v1.2.0`](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/tree/v1.2.0)
at commit `bba3c93`. That release includes the mode-aware claims, public
theory and scope notes, curated data, matching-circle code and records, figure
generators, rendered assets, process lessons, and a 201-file hash manifest.
Public `main` later advanced to `719a1ff` to reorganize those notes under
`docs/`; it does not alter the tagged paper state. Older candidates remain
visible in history as provenance, not as the controlling claim set. Journal
peer review and a DOI or other archival identifier remain future steps. The
symbolic environment is pinned there to NumPy 2.5.0, SciPy 1.18.0, and SymPy
1.14.0; the FEM environment records FEniCSx/dolfinx 0.10. Exact AI model build
identifiers were not preserved consistently, so this account reports the
system names and roles recorded at the time rather than inventing versions.*

**Version:** 1.4 (submission closure, evidence map, and numerical-scope audit)
**Last Updated:** July 24, 2026
