# Case Study: When Verification Rewrites the Theory — A Symplectic Mooney–Rivlin Crack Tip

**How a human–AI team turned a new nonlinear crack-tip field, a useful but incomplete spectral scaffold, and several rounds of mutually inconsistent “verified” claims into a carefully scoped pre-submission draft — and why the decisive work was not generating equations, but learning exactly what each check could prove.**

---

## 📖 Table of Contents

- [Overview](#overview)

**Part I — The Scientific Journey**
- [1. The Problem: A Two-Invariant Crack Tip](#1-the-problem-a-two-invariant-crack-tip)
- [2. The Constraint That Reorganizes the Tip](#2-the-constraint-that-reorganizes-the-tip)
- [3. From Local Theory to Parameter-Free Tests](#3-from-local-theory-to-parameter-free-tests)
- [4. The Symplectic Promise and the Missing Operator](#4-the-symplectic-promise-and-the-missing-operator)
- [5. Where the Final Manuscript Stops](#5-where-the-final-manuscript-stops)

**Part II — Technical Lessons**
- [6. Correct Equations Can Still Form a Contradictory Paper](#6-correct-equations-can-still-form-a-contradictory-paper)
- [7. A Unit Gauge Hid a Missing Amplitude](#7-a-unit-gauge-hid-a-missing-amplitude)
- [8. A True Premise Is Not a Sufficient Argument](#8-a-true-premise-is-not-a-sufficient-argument)
- [9. A Fitted Coefficient Is Not Automatically an Asymptotic Coefficient](#9-a-fitted-coefficient-is-not-automatically-an-asymptotic-coefficient)
- [10. A General Theorem Is Not a Specific Reduction](#10-a-general-theorem-is-not-a-specific-reduction)
- [11. Degenerate Endpoints Decide the Admissible Theory](#11-degenerate-endpoints-decide-the-admissible-theory)
- [12. Find the Carrier by Decomposing the Flux](#12-find-the-carrier-by-decomposing-the-flux)
- [13. A Closed Rung Is Not a Closed Tower](#13-a-closed-rung-is-not-a-closed-tower)
- [14. Fix Passes and Stale State Are New Error Surfaces](#14-fix-passes-and-stale-state-are-new-error-surfaces)

**Part III — Collaboration Patterns**
- [15. The Multi-AI Review Loop](#15-the-multi-ai-review-loop)
- [16. Different Review Styles Saw Different Failure Classes](#16-different-review-styles-saw-different-failure-classes)
- [17. Where AI Failed, Specifically](#17-where-ai-failed-specifically)
- [18. The Human's Critical Contributions](#18-the-humans-critical-contributions)
- [19. Attribution, Carefully](#19-attribution-carefully)

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
the two transverse stretches to become equal. That constraint changes the
in-plane exponent, the deformed crack shape, and the areal stretch while
leaving the leading energy-release relation in neo-Hookean form.

The resulting manuscript gives a leading opening proportional to r¹ᐟ², an
in-plane field proportional to r⁵ᐟ⁴, a deformed-tip profile with exponent
2/5, an angle-independent compensated Jacobian, and

```text
G = (π/2) c₁ P².
```

A pure-shear strip then fixes the tip amplitude P from the applied grip
stretch. Finite-element calculations of that strip test this relation and the
predicted kinematics without imposing the asymptotic crack-tip field.

Those headline results survived the review campaign. Much of the higher-order
story did not survive unchanged. A five-row spectral pencil that began as the
organizing theory was ultimately scoped as a *scaffold*: exact on its opening
block, useful for locating candidate families, but not the derived full
reaction-carrying operator. Several higher-order amplitudes moved, acquired
missing dimensional factors, or were demoted from free parameters to
conditional candidates. The submission draft became stronger by claiming less.

The scientific repository began in June 2026, with manuscript revisions
recorded from 3 July. The multi-AI review campaign ran from 5–19 July, with an
especially intensive 17–19 July cycle. It used
Claude/Fable as the principal revision executor,
GPT/Codex as a structural reviewer and later derivation lead, Kimi as an early
independent verifier, DeepSeek/OpenCode as a late end-to-end auditor of the
then-current theory tree, and earlier GLM and Opus reports. Teng Zhang, the human author, acted
as the meta-reviewer and made the scope and stopping decisions. The central
lesson is not that multiple AIs vote their way to correctness. They do not.
The useful unit was a disagreement converted into an artifact that could
falsify one side.

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
y₁ = P^(-1/2) r^(5/4) g(θ) + … .
```

The angular profile g is selected by an endpoint regularity condition on the
intact ligament. Its face value is g(π) = 2.0333… in the manuscript's
normalization. At leading order near the tip, the resulting principal-stretch
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

On the crack face, y₂ ~ r¹ᐟ² while the in-plane distance from the deformed
tip scales as r⁵ᐟ⁴. Eliminating r gives the 2/5 deformed-tip profile. The
corresponding neo-Hookean profile has exponent 1/2.

The first correction is forced by the *on-manifold I₂ stress*, not by
off-manifold compliance. Its opening profile is
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

The finite-element campaign used two specimens with distinct roles. The strip
was the primary specimen-level validation: its computed energy flux agreed
with hW∞ within 0.00–0.15%, and its measured P agreed with the closed-form
prediction within 2.2–3.0% over the reported load range. Its compensated
Jacobian had 3.2–9.1% angular spread, while the c₂ = 0 control showed
101.5–112.2% angular spread. A boundary-driven disk reached much deeper toward
the tip and served as a consistency cross-check for the in-plane profile,
2/5 tip shape, and stress relation. It was not presented as an independent
specimen-scale validation.

This division mattered. The strip FEM does not impose the crack-tip field and
can falsify the predicted exponent, amplitude relation, and angular structure.
The disk instead tests interior consistency under a homogeneous remote-stretch
boundary condition.
The c₂ = 0 control is especially valuable because it shares enough of the
leading opening behavior to rule out a generic mesh or fitting explanation for
the Mooney–Rivlin Jacobian plateau.

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

The correction was not to discard the scaffold. It was to name it accurately.
The final manuscript establishes the conserved pairing and the
3/2 − Λ duality exactly on the opening block. It uses the remaining rows as a
classified spectral scaffold and states that a future full constrained
operator would replace, not simply ratify, them. At the scaffold/eigenvector-
audit level, a characteristic shear sᵏ pairs with the singular auxiliary
s¹⁻ᵏ, corresponding to labels k and 1 − k. This is not yet a full-operator
shear-channel conservation theorem. Applying the opening reflection globally
had been another category error.

## 5. Where the Final Manuscript Stops

The final scope has several layers.

**Established at the stated evidence level:**

- The leading constrained field, its first forced correction, and the
  parameter-free energy and stress relations.
- The finite-element strip validation and disk cross-check of the named
  leading predictions.
- The exact opening-block pairing and its 3/2 − Λ duality.
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

- Higher material orders of the k + 1/2 block.
- The row-two rung generated at k + 3 and any tower beyond it.
- The general reaction-carrying constrained endpoint operator and its full
  conserved pairing.
- The finite-compliance operator and the shrinking axis layer needed to match
  the non-smooth outer multiplier to the smooth finite-c₂ solution.
- Normalized extraction integrals for the higher parameters.
- Whether a specimen actually excites the candidate amplitudes B and Qₖ.

The paper's leading field and energy release rate do not depend on those open
items. The higher amplitudes are candidates, not established universal second
parameters. That separation between result and program is part of the result
of the review process.

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
modes. (Q₁ = P⁻¹ᐟ² is the leading-field gauge, not a member of this family.)
The corrected action calculation found two ordered consequences rather than a
single closed tower:

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

## 14. Fix Passes and Stale State Are New Error Surfaces

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

The final public-companion audit exposed the same problem across data
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

The same final audit caught prose quantifiers that were stronger than their
evidence. The radial-mesh study supports the representative `λ = 1.6`,
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
to 57 checks, while specialized analysis scripts carried deeper derivations.
Those counts are coverage descriptions, not proof by quantity: some checks
encode printed identities, some independently derive them, and some are
sampled numerical regressions. The final manuscript and ESI label those levels
rather than calling every assertion an independent proof.

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

The release candidate made the relational character of evidence visible. The
claim ledger and code/evidence map declared the scope; gates checked
raw-to-summary, figure-to-input, and artifact-to-protocol edges; nested content
locks pinned the resulting bytes. Checksums establish byte identity; semantic
gates establish that the artifacts form a coherent evidence family and support
the stated claim. Neither substitutes for the other. Likewise, fast
reproduction from curated arrays and an expensive fresh finite-element solve
are separate lanes: one checks the curated evidence against its derived
summaries and regenerates its figures, while the other tests whether the
underlying computation can reproduce that evidence.

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

**“Pause and submit.”** The theory–verification loop had no natural terminal
rung. Teng first wrote a stopping line — analysis for endpoint solvability and
conservation, numerics for a well-posed spectrum — and then made the stronger
decision to pause before completing it because no printed leading result
depended on the unfinished blocks. External peer review was designated as the
next verification instrument.

This separated three decisions that are often collapsed. **Review again** when
a promoted result lacks a discriminating falsification route adequate to its
scope. **Continue** when an unresolved claim or failed gate lies on the
dependency path of a claim the paper needs. **Release** when the bounded claim
subgraph passes its full circuit and all remaining open work has been scoped
out of the shipping claims and named explicitly. Release readiness is not
research completion: the verified leading result could be frozen and shared
while the full constrained operator remained an open program.

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
decision, led the Qₖ derivation rounds. It contributed the action/scaffold
distinction, dimensional and full-stress attacks, exact endpoint and flux
checks, and the later companion construction. In the subsequent release work,
it also helped formalize the multi-gate circuit. Fable reviewed the promoted
results at the scope recorded in each handoff; the later k + 3/2 construction
received a dedicated PASS before manuscript integration.

Kimi supplied independent reproduction and code-versus-text checks in the
early rounds, including an independent route to P⁻³ᐟ² and the P2 element
correction. DeepSeek/OpenCode performed the late end-to-end audits. Its third
pass reviewed the then-current theory/manuscript tree at `74edb13` and reported
“Ready for submission.” That verdict predates the final mesh-provenance, data,
figure, and scope corrections and is not a review of public-companion commit
`3369dbc`. One intermediate DeepSeek review used stale state and was retained
as history rather than authority. GLM and Opus contributed earlier
referee reports. This was an AI review verdict before journal peer review, not
a proof statement or an external signoff.

Line-level authorship cannot be reconstructed reliably from a shared working
tree, and this case study does not assign it. Some source records were drafted
by the same agents they assess, so their evaluative claims were checked against
the round-by-round record before being used here. The defensible attribution
is layered: human scientific ownership and termination, AI-assisted
derivation and integration, independent model-specific checks, and final
human responsibility.

Two statements coexist. No individual AI verdict was trustworthy without an
artifact capable of falsifying it. The calculations emerged through documented
handoffs among participants; no load-bearing AI derivation was promoted on one
model's unreviewed assertion. The transferable result is the protocol that
allowed both statements to be true.

---

## Summary

```text
The progression that matters:

  Two-invariant plane-stress gap
      → emergent uniaxial constraint
      → r^(1/2) opening, r^(5/4) in-plane field, 2/5 tip shape
      → G = (π/2)c₁P² and parameter-free strip test

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

  Manuscript review
      → local checks pass while cross-claims conflict
      → fixes introduce dimensional, traction, and duality errors
      → independent routes, controls, and component decompositions
      → scoped submission draft with open problems named
```

**When AI worked well:** the claim could be attacked from a genuinely
different direction — symbolic differentiation versus dimensional
restoration, asymptotics versus FEM, total flux versus component
decomposition, endpoint recurrence versus high-precision global solution.
Generation was fast because falsification was concrete.

**When AI struggled:** the missing content was outside the frame it had been
given — an omitted constitutive coupling, an unmodeled same-order background,
a theorem-to-operator identification, a stale file, or a quantifier stronger
than the evidence. More re-reading inside the same frame did not help.

**The meta-lesson:** executable verification is essential, but “make a test”
is not the end of the scientific question. A test certifies only what it could
have falsified, on the artifact it actually exercised, at the scope its
dependencies permit. The project reached its recorded pre-submission state
when that sentence became a rule for equations, code, reviewer reports, and
prose alike.

---

*This case study documents the Mooney–Rivlin plane-stress crack-tip project
and its intensive June–July 2026 verification campaign. At the recorded
signoff, the festschrift manuscript was prepared for submission but had not
yet undergone journal peer review. The sanitized release-candidate companion
is currently private pending the author's visibility decision. Its pinned
commit is
[3369dbc](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/tree/3369dbcfa8b415217e51cbcb4f50935fd45b5341),
and its curated
[verification lessons](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip/blob/3369dbcfa8b415217e51cbcb4f50935fd45b5341/PROCESS_AND_LESSONS.md)
are intended to replace raw internal review records as the public process
reference once released. The
symbolic environment is pinned there to NumPy 2.5.0, SciPy 1.18.0, and SymPy
1.14.0; the FEM environment records FEniCSx/dolfinx 0.10. Exact AI model build
identifiers were not preserved consistently, so this account reports the
system names and roles recorded at the time rather than inventing versions.*

**Version:** 0.97 (gate-architecture review draft)
**Last Updated:** July 20, 2026
