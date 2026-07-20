# Case Study: When the Method Had to Match the Claim — Analytical-Depth Symplectic Wrinkle Bifurcations

**How a human–AI team separated a useful depth-resolved numerical oracle from
the method promised by the paper, and how Fable's sustained analytical-depth
rebuild, independent audits, and repeated self-corrections produced defensible
retained-space calculations of wrinkle period doubling and quadrupling.**

---

## 📖 Table of Contents

- [Overview](#overview)

**Part I — The Scientific and Methodological Journey**

- [1. The Problem: Stability About a Finite-Amplitude Wrinkle](#1-the-problem-stability-about-a-finite-amplitude-wrinkle)
- [2. Preliminary Estimates Answered Different Questions](#2-preliminary-estimates-answered-different-questions)
- [3. A Useful Depth-FE Oracle Revealed a Method Boundary](#3-a-useful-depth-fe-oracle-revealed-a-method-boundary)
- [4. Teng Made the Method Contract Explicit](#4-teng-made-the-method-contract-explicit)
- [5. Fable's Analytical-Depth Turnaround](#5-fables-analytical-depth-turnaround)
- [6. Independent Audit and Retained-Space Closure](#6-independent-audit-and-retained-space-closure)

**Part II — Lessons That Came From the Work**

- [7. A Method Name Is an Executable Claim](#7-a-method-name-is-an-executable-claim)
- [8. Exploratory Freedom and Publication Eligibility Are Different](#8-exploratory-freedom-and-publication-eligibility-are-different)
- [9. Verification Must Resolve the Scale of the Claimed Observable](#9-verification-must-resolve-the-scale-of-the-claimed-observable)
- [10. Symmetry and Conditioning Were Part of the Physics](#10-symmetry-and-conditioning-were-part-of-the-physics)
- [11. Coupled Approximations Must Be Closed Together](#11-coupled-approximations-must-be-closed-together)
- [12. Retractions Became Verification Assets](#12-retractions-became-verification-assets)
- [13. Agent Autonomy Made Provenance and Communication Scientific Requirements](#13-agent-autonomy-made-provenance-and-communication-scientific-requirements)

**Part III — Collaboration and Attribution**

- [14. Teng's Highest-Leverage Contributions](#14-tengs-highest-leverage-contributions)
- [15. Attribution and the Multi-AI Review Loop](#15-attribution-and-the-multi-ai-review-loop)

- [Summary](#summary)
- [Evidence Record](#evidence-record)

---

## Overview

A stiff film bonded to a soft substrate wrinkles under compression. With
further compression, the wrinkle may double its period and later quadruple
it. The onset of the primary wrinkle is a linear stability problem. Period
doubling is harder because stability must be evaluated about a nonlinear,
finite-amplitude wrinkle, and the destabilizing mode belongs to a signed
half-integer Floquet sector. Here a *carrier* is a Fourier wavenumber label,
and a *comb* is the finite set of carriers coupled by the wrinkled base state.
Quadrupling repeats the problem about the already doubled state.

The final calculation developed in this project is an
**analytical-depth symplectic-basis Rayleigh–Ritz method**. Exact homogeneous
Hamiltonian–Stroh modes at the current load provide the depth-wise backbone.
Analytical product-rate functions enrich the finite-amplitude representation.
The unknowns are global coefficients, not values at depth nodes. Those
coefficients are determined by stationarity of the unexpanded finite-strain
energy. Stability is assessed through a reflection-resolved signed Floquet
Hessian.

For the main modulus-ratio benchmark, the final retained-space calculation
gives a period-doubling estimate of 0.179. A separately discretized lattice
calculation crosses at 0.176; both sit near the lower edge of the broader
0.18–0.20 experimental and finite-element comparison range. Applied about the
doubled branch, the same analytical framework gives a
doubling-to-quadrupling estimate of 0.244, close to a separately discretized
single-grid lattice crossing at 0.243. These are retained-space numerical
estimates, not rigorous continuum bounds; the manuscript reports their
refinement behavior and the remaining strong-form limitations.

The collaboration history explains how the final values acquired their
present scope. A depth-resolved Fourier–finite-element calculation had earlier
produced a useful period-doubling result near the observed range. Its
through-depth freedom provided strong evidence that the reduced theory needed
a more flexible depth representation. Paper-facing assets, however, described
that calculation too broadly as symplectic or mesh-free even though its
assembled unknowns were nodal through depth. Teng insisted that the numerical
oracle and the claimed analytical method be separated. Fable then built a
coefficient-only analytical-depth method. That effort involved conditioning
and mode-identification failures, withdrawn thresholds, an ambitious but
incomplete precise-integration-method (PIM) strip referee, and repeated
revisions of the convergence argument. Independent reviewers later repaired,
audited, and extended specific retained-space tasks.

The depth-FE family also retained convergence and provenance limitations, so
its status as an oracle did not make it a publication-grade endpoint. The
central methodological problem was that its approximation space and label no
longer agreed. The analytical-depth rebuild, rather than recovery of a
preferred decimal, is the main subject of this case study. The Evidence Record
at the end distinguishes historical checkpoints from the sources governing
the final method and values.

---

# Part I — The Scientific and Methodological Journey

---

## 1. The Problem: Stability About a Finite-Amplitude Wrinkle

The project grew from Teng's 2017 linear symplectic framework for layered
wrinkling. In that formulation the depth coordinate plays the role of
pseudo-time, displacement and traction form a dual state, and each Fourier
carrier satisfies a Hamiltonian first-order system. This gives exact
homogeneous depth modes and a stable way to impose decay in a semi-infinite
substrate.

The nonlinear program began in January 2026 as the higher-order extension
anticipated by the earlier work. Period doubling was selected as the first
secondary instability because it has a precise local criterion while still
containing the main finite-amplitude difficulty. If
`u_primary(delta)` denotes the equilibrated single-period wrinkle, the
quantity of interest is schematically

```text
lambda_min^AP [ D²Pi(u_primary(delta)) ],
```

the lowest signed eigenvalue of the second variation in the anti-periodic
sector. A defensible calculation must satisfy four requirements at once:

- the primary wrinkle must be a self-consistent nonlinear equilibrium;
- its integer harmonics and through-depth profiles must be sufficiently rich;
- the perturbation must contain the signed half-integer Floquet comb; and
- the physical zone-boundary mode must be tracked without switching to its
  nearly degenerate reflection partner.

The benchmark is numerically delicate. In a diagnostic at compression
`delta=0.18`, the neutral curvature was the small residual of positive and
negative contributions of order 0.19. A change of only a few parts in a
thousand in either contribution can move the zero crossing by the amount under
debate. This fact eventually determined which verification instruments were
credible.

The scientific target was not merely a number near an experimental or finite
element range. The project sought an extension of the symplectic structure
into a finite-amplitude theory with a traceable approximation space. That
distinction became decisive: resolving the cascade tests whether one
continuum model and one nonlinear state can account for successive changes in
period, rather than only the first onset of wrinkling.

## 2. Preliminary Estimates Answered Different Questions

Before the threshold campaign, the project had to make its equations easier
to falsify. The original volumetric energy produced large bulk-modulus terms
whose failed cancellations could be explained away as conditioning. Teng
insisted on the `(J-1)^2` penalty, for which the relevant leading coefficient
is manifestly of order `mu`. Any surviving order-`kappa` term then signals an
equation or implementation error rather than a tolerance problem. The change
turned a numerical debate into an analytic gate.

That gate exposed a recurring AI tendency in this project: when an equation
gave the wrong scale, the first response was often to adjust the solver. The
productive order was the reverse—derive the coefficient, prove the expected
cancellation symbolically, test it on a limiting case, and only then run the
full pipeline. A later JAX/finite-difference comparison found a roughly three
percent discrepancy in the primary-amplitude coefficient; the automatic-
differentiation value was retained because its derivative path could be
checked more cleanly. Re-deriving the earlier PIM series also found a
denominator typo in a published coefficient. The same verification discipline
was applied to AI output, project legacy code, and the literature.

Several early values were sometimes narrated as successive corrections to
one calculation. They came from different states and stability spaces.

An early weakly nonlinear pipeline gave a period-doubling strain near 0.198.
It was encouraging because it lay near the finite-element observations, but
the result used a quadratic primary-amplitude relation and a limited
harmonic/depth representation. Improving the amplitude calibration while
leaving other ingredients fixed moved the estimated crossing upward, toward
0.25. Later reduced calculations placed a local instability near
0.233–0.239.

The historical retrospective interprets these movements as competing biases:
the quadratic amplitude law made the primary wrinkle too large, while an
incomplete perturbation space delayed instability. That interpretation is
useful, but the stages did not form a controlled two-parameter error study.
They changed different pieces of the model at different times. The careful
conclusion is narrower: the early agreement did not determine which
approximation was responsible for the value, and it could not close the
method.

The reduced local threshold near 0.233–0.239 left two plausible explanations
for the finite-element transition near 0.20. One was a subcritical jump: the
doubled branch might become energetically preferred before the period-one
state lost local stability. A fitted sixth-order Landau potential showed that
such a separation was mathematically possible, but it did not derive the
energy landscape of the elasticity problem. The other explanation was
representation bias: fixed weak-amplitude depth shapes could make the local
stability operator too stiff. The project kept both hypotheses open. The
depth-resolved calculations supplied evidence for the second, and later
nonlinear kick and reflection-sector tests supported a local instability in
the lower range.
This was a useful example of using computation to discriminate mechanisms
rather than fitting the expected transition.

A later Fourier–Galerkin calculation with finite-element profiles through
depth was a different development. It relaxed the depth shapes of both the
finite-amplitude state and the Floquet perturbation and obtained crossings
near 0.19: approximately 0.194 at a four-comb rung, approximately 0.190 at a
deeper rung, and a reported comb-limit family near 0.186–0.190. This was not
the same `0.198 -> 0.25 -> 0.233–0.239` sequence.

The depth-resolved calculation supplied a major physical clue. Weak-amplitude
flat-state profiles appeared too restrictive at finite wrinkle amplitude.
Allowing each coupled harmonic to alter its film profile and substrate decay
moved the prediction substantially. The remaining question was whether that
freedom could be obtained in the analytical method the paper claimed.

## 3. A Useful Depth-FE Oracle Revealed a Method Boundary

The depth-resolved route was not a conventional full two-dimensional FEM.
Fourier or Floquet harmonics represented the periodic direction, while
piecewise-linear nodal functions represented displacement through depth. A
variational nonlinear solve produced the primary state, and a signed
anti-periodic Hessian detected the secondary instability. As a numerical
method in its own right, it was useful and physically revealing.

The issue appeared when the code and paper were compared at the assembly
level. Scripts used names such as “semi-analytical symplectic solver,” and
manuscript text said the depth profiles were not discretized on a mesh. The
assembled production state nevertheless had hundreds of nodal depth degrees
of freedom; one audit counted 792 before reduction. Stroh profiles were used
to seed or project part of the state calculation, but the operator remained a
piecewise-linear depth-FE operator, and the stability block was not converted
into a global analytical-depth space.

This distinction matters because a method claim identifies more than the
physics model. It identifies the unknowns, trial space, assembly, and boundary
treatment. A Stroh-generated initial guess does not make the resulting nodal
operator analytical-depth. A symplectic linear subroutine inside a larger
pipeline does not make the finite-amplitude solve a nonlinear symplectic
method.

The depth-FE work remained an oracle with a deliberately different
approximation error and had already supplied evidence for the importance of
through-depth relaxation. The correction was to
separate its role from publication eligibility. It could test energy
landscapes, branch content, and bias direction. It could not be the evidence
for the claim that the reported solution had no depth-nodal unknowns.

That separation is one of the central lessons of the project. Exploratory
methods often become valuable precisely because they differ from the final
method. Their usefulness is lost, rather than increased, when their identity
is blurred.

## 4. Teng Made the Method Contract Explicit

Teng repeatedly returned the project to four constraints:

- the selected paper method could not contain depth-FE or interface-node
  unknowns hidden behind a favorable label;
- finite amplitude had to follow from nonlinear equilibrium, not from an
  onset solvability condition extrapolated beyond its range;
- the separate moving-manifold method under development elsewhere should not
  be duplicated or quietly merged into this track; and
- improving the last decimal was secondary to establishing what method had
  actually produced the figure and threshold.

These were not editorial preferences. They fixed the scientific object being
developed. When source-level inspection confirmed the depth-nodal assembly,
Teng pushed for a new analytical route rather than accepting the numerical
agreement as sufficient.

The resulting method contract was more precise than the phrase “nonlinear
symplectic method.” The acceptable route could use the Hamiltonian–Stroh
system to generate exact homogeneous depth functions and organize nonlinear
enrichment. The finite-amplitude state could then be obtained by Rayleigh–Ritz
stationarity of the full energy. What it could not do was imply that the
nonlinear state itself was produced by a fully nonlinear PIM propagation when
it was not.

At an intermediate review, Teng explicitly relaxed the earlier blanket
restriction on Galerkin/Rayleigh–Ritz methods while retaining the no-depth-node
boundary. This made Fable's global analytical Ritz route eligible for the
paper, provided that its symplectic ingredients, variational closure, and
limitations were stated separately. The change was an explicit scientific
decision, not a silent reinterpretation of the original instruction.

The final defensible description is therefore deliberately compound:

> A finite-amplitude analytical-depth Rayleigh–Ritz energy method whose
> homogeneous depth functions and decay structure are generated by the
> Hamiltonian–Stroh system, and whose analytical enrichments use rate families
> organized by the symplectic spectrum and weakly nonlinear hierarchy.

This wording retains what is genuinely symplectic and identifies what is
variational. It also makes the no-depth-node condition testable in the code.

## 5. Fable's Analytical-Depth Turnaround

Fable opened the coefficient-only analytical-depth track on 10 July. Its
chronology records construction, diagnosis, withdrawal, and reconstruction at
each stage of the state and stability calculation.

### 5.1 Building a state without depth nodes

The first stage replaced nodal depth fields with global coefficients
multiplying explicit analytical functions. At each integer Fourier harmonic,
the basis combined:

- exact film eigenmodes of the current-load Hamiltonian;
- the decaying substrate invariant subspace;
- interface-matched homogeneous functions; and
- analytical product-rate enrichments motivated by nonlinear harmonic
  interactions.

The coefficients were determined by Newton iteration on the unexpanded
compressible neo-Hookean energy. The primary amplitude was therefore an output
of energy stationarity. Gauss points were used for integration, but no
displacement value at a Gauss point was an unknown.

The first state calculations already passed useful gates. The energy was
invariant under quadrature refinement to near machine precision, and the
coefficient gradient converged to approximately `10^-10` or smaller.

The analytical states had slightly lower energy than the production depth-FE
states. Refining the depth-FE mesh moved its energy toward the analytical
value, supporting the analytical state rather than merely fitting the oracle.
The difficult part was the stability space.

### 5.2 Learning what the stability instrument could resolve

The first analytical half-comb used a mass-norm Gram reduction—a spectral
filter that removes numerically redundant combinations of candidate basis
functions. Increasing
the rate order left the retained rank frozen at 114 out of 928 candidates.
Without the rank report, the unchanged answer could have been mistaken for
convergence. The mass metric was suppressing high-gradient content that had a
small displacement norm but substantial energy.

Fable changed the reduction to a gradient/energy seminorm and then swept the
Gram cutoff in both directions. The soft mode lived in combinations of nearly
degenerate exponentials—the confluent tail of the dictionary. Those
directions looked numerically suspicious, but controlled noise tests showed
that they were stable at the actual roundoff scale. Removing them because
their Gram eigenvalues were small would have removed physical span.

A cross-Rayleigh comparison initially appeared to show that the analytical
operator was too soft. Fable then decomposed the curvature and found that the
answer was a residual of approximately `+0.19` and `-0.19` contributions.
Interpolating the analytical eigenfield into a depth-FE mesh perturbed the two
large terms by more than the residual being compared. The cross-evaluation
could not adjudicate the disagreement.

The decisive referee was the flat state, where the harmonics decouple and a
dense one-dimensional calculation is available. In that regime, the refined
depth-FE result moved toward the analytical value, and the remaining absolute
depth-FE error was still much larger than the dressed neutral curvature. This
did not prove the full analytical result, but it established which instrument
could resolve the cancellation scale and why internal mesh stability alone
was inadequate.

Fable's method retrospective later grouped these episodes as three instrument
failures: mode identification, conditioning, and validation tests that could
not falsify the proposed answer. Each required a different gate; no single
convergence ladder addressed all three.

### 5.3 Withdrawing a promising threshold when the mode was not identified

The enriched comb produced a provisional crossing near 0.178. Teng objected
that unusually close agreement with the lattice was not, by itself, evidence;
the lattice had different and incompletely quantified errors. Fable then added
physical mode classification rather than treating the global minimum as
automatically relevant.

A score based on half-harmonic mass and vertical content selected a different
mode, so Fable withdrew the 0.178 threshold. Further nonlinear kick tests
showed that the period-one state was unstable in the expected range. Inspection
of the low modes then revealed the problem. The physical zone-boundary mode
and its reflection twin differed by only about one percent in the heuristic
scores; the score had selected the wrong twin.

Fable replaced identification by score with a structural reflection-sector
decomposition. Even that required three versions:

- splitting each Stroh field into component-pure pieces enlarged the raw span
  but destroyed its natural displacement pairing and buried the soft mode
  below the Gram floor;
- projecting the naturally paired fields fixed the conditioning and restored
  flat-state degeneracy; but
- reflecting about a fixed coordinate axis failed whenever the translation-
  invariant state solver returned a phase-shifted wrinkle.

The working construction measured the crest angle from each converged state,
verified reflection symmetry about that physical axis, and then projected the
stability space. The union of the two sector spectra reproduced the
unprojected spectrum to printed precision. The soft mode occupied the
crest-centered sector and the non-crossing twin occupied the valley-centered
sector. What had looked like an eigenvalue-tracking nuisance was a physical
standing-wave pair and required a symmetry-level solution.

### 5.4 Freezing, retracting, and rebuilding the convergence argument

The first sector-certified harmonic ladder gave

| Largest half-integer carrier | Crossing |
|---|---:|
| `7/2` | 0.18382 |
| `9/2` | 0.17922 |
| `11/2` | 0.17836 |

After Gram and depth checks, Fable provisionally froze a value near 0.178.
The doubled-branch calculation then appeared to be born near 0.185, which was
incompatible with a supercritical crossing at 0.178. Fable compared the branch
and stability spaces directly.

The branch representation contained only the equivalent of a `7/2` stability
comb. Its birth point therefore agreed with a shallow rung of the stability
ladder, not with the comb limit. In addition, the doubled-cell representation
gave a slightly better period-one state and shifted the matched crossing. The
perturbation-space ladder had been mistaken for certification of the
parent-state space.

Fable retracted the tight freeze and recomputed a state-corrected ladder:

| Matched comb level about the improved state | Crossing |
|---|---:|
| `7/2` | 0.18527 |
| `9/2` | 0.18056 |
| `11/2` | 0.17967 |

An independent Codex review then identified another missing axis: the integer
harmonic count of the parent state had not been laddered. Fable accepted the
finding, suspended the quote, corrected a separate traction-index diagnostic,
and ran the missing sequence. The crossings moved from 0.179679 to 0.179511
and 0.179414 as the state was enriched, with shrinking increments. The final
paper later centered its reported 0.179 value on an even richer direct
calculation, 0.179131, rather than on a manual tail correction.

### 5.5 The PIM strip became a diagnostic route

After Teng asked for a more explicitly symplectic construction and rejected
linear finite-element hats as the paper method, Fable designed a strip method
whose local interiors were generated by frozen Hamiltonian flow. Interface
traces parameterized each strip, and the element dynamic stiffness acted as a
generating function of the symplectic transfer map. The deep substrate used an
exact decaying impedance.

The design used exact local Hamiltonian flow and required work on exponential
growth, condensation, band-edge validity, global-matrix scale separation, and
Hermiticity. It consumed a substantial part of the turnaround.

GLM then found four genuine sign, block, and adjoint-convention defects in the
strip implementation and rebuilt the critical propagation step using the
validated mixed-energy PIM convention. Fable accepted and documented the
repair. A later review found that the positive-only complex strip omitted the
signed sum coupling needed to split the two reflection sectors in the dressed
state. Flat symplectic and Hermiticity gates could not expose that omission
because the relevant non-flat Fourier coefficient vanishes at the flat state.

The strip therefore remained valuable as a diagnostic of propagation
conventions and structural invariants, but it did not generate the final
period-doubling or quadrupling values. It was also element-like under Teng's
strict method boundary because it retained a depth partition and interface
traces. The production route remained the global analytical-depth Ritz
method.

## 6. Independent Audit and Retained-Space Closure

Review became useful when a reviewer traced a claim to its generator and
produced a test that could change the conclusion.

Codex's source audit is instructive because it corrected the reviewer as well
as the reviewed work. An initial criticism treated positive harmonic labels
as proof that Fable's production Floquet comb omitted negative carriers. The
source trace showed that the production path constructed real sine/cosine
fields, which already contain the conjugate pair and both sum and difference
couplings under direct integration. The omission belonged only to the
experimental complex strip. Codex withdrew the broad criticism and separated
the two routes in the audit.

The same audit verified the constitutive tangent and the gradient and Hessian
of the unexpanded energy in the retained basis by independent finite
differences; confirmed that the production unknowns were global analytical
coefficients; and confirmed that finite amplitude came from energy
stationarity. It also found real remaining issues:
an incomplete state-harmonic ladder, a traction component index error, a
carrier-assignment mismatch in one forced-tail family used for the
period-two-to-period-four boundary, missing hard gates, and incomplete
artifact provenance.

The later retained-space integration kept Fable's architecture. Carrier-
correct spaces for `T45`, the period-two-to-period-four neutral boundary, were
compared as nested numerical unions rather than unrelated replacements.
The period-doubled state and its stability space were lifted into the
period-four cell by the exact carrier identity `(2m)Q = mq`. A physical
quarter-harmonic amplitude constraint located the daughter branch, after
which the constraint was released and full energy stationarity was checked.
State and quarter-comb refinements were closed at a joint deep corner. These
steps produced the current retained-space estimate of 0.244 and the analytical
period-four configuration.

The final scientific picture contains more than the two thresholds. The
period-doubled daughter's squared half-harmonic amplitude is nearly linear in
load over the sampled near-onset interval and extrapolates close to the
independently computed 0.179 neutral root, supporting a continuous local
branch within the retained space. A matched pilot calculation across modulus
ratios from 14 to 375 moves the doubling boundary by less than 0.006, which
supports the near-flat phase-boundary trend within that protocol rather than a
universal material law.

Quadrupling remains less closed than doubling. The analytical `T45=0.244`
estimate is close to the single-grid lattice crossing at 0.243448, but the
doubled parents retain strong residual ratios of roughly 0.22–0.30. The
analytical period-four state at compression 0.2675 is stationary and stable in the
retained space, while its film strong-residual ratio is about 0.495. A finite-
element phase diagram for a related incompressible model has been read near
0.26. That reading is approximate and the material model differs, so the
offset is an open comparison rather than a failed validation. These
qualifications prevent the quadrupled daughter from being presented as a
pointwise-converged continuum solution.

The final method statement is intentionally limited:

- homogeneous depth functions and half-space decay are literal
  Hamiltonian–Stroh objects;
- nonlinear product-rate fields are analytical Ritz enrichments, not all
  exact Hamiltonian eigenfunctions or forced-ODE particular solutions;
- the finite-amplitude state is a stationary point of the full energy in a
  retained global space;
- stability is a signed, reflection-resolved Floquet Rayleigh–Ritz problem;
- no depth-nodal unknowns occur in the selected calculation; and
- strong pointwise residuals remain diagnostics of omitted enrichment rather
  than being presented as zero.

That description is less sweeping than “fully nonlinear symplectic solver,”
but it says exactly where the symplectic structure enters and what the
calculation actually solves.

---

# Part II — Lessons That Came From the Work

---

## 7. A Method Name Is an Executable Claim

The most important review question was not “does the file say symplectic?” It
was:

```text
What are the unknowns?
What basis multiplies them?
What is assembled?
Which conditions are exact, weak, or numerical?
```

The old depth-FE route, the production analytical-depth route, and the PIM
strip all used Fourier harmonics and some form of Stroh or Hamiltonian
machinery. They were nevertheless different methods:

| Route | Through-depth unknowns | Role of symplectic analysis | Proper status |
|---|---|---|---|
| Fourier × depth-FE | Piecewise-linear nodal values | Initialization/projection and shared linear ingredients | Numerical oracle |
| Analytical-depth Ritz | Global coefficients of Stroh/exponential functions | Homogeneous backbone and rate organization | Selected paper method |
| PIM strip | Interface traces across a depth partition | Local Hamiltonian propagation and dynamic stiffness | Experimental diagnostic |

The source trace attached those categories to generators rather than names in
prose. Historical `rev27_full_enrichment.py` belonged to the depth-nodal
family. The selected route ran through `analytic_state.py`,
`analytic_comb.py`, `comb_sector.py`, and `doubled_state.py`; the experimental
route ran through `symplectic_strip.py` and its repaired variants. This check
prevented a figure label from deciding the method class.

A method label must travel with every paper-facing numerical asset. An array
of surface coordinates is not self-describing: it should identify the
generator, approximation space, source revision, load, residual status, and
whether its sampling points are unknowns, quadrature points, or visualization
points. Without that metadata, an old depth-nodal configuration can acquire a
new analytical label simply by passing through a renderer.

This lesson extends beyond symplectic mechanics. In agent-assisted research,
names propagate faster than understanding. The assembly loop is where a
methodological claim becomes falsifiable.

## 8. Exploratory Freedom and Publication Eligibility Are Different

Under the final method contract, the depth-FE route served as an oracle and
the PIM strip as an experimental diagnostic. Both supplied useful design
lessons.

The depth-FE calculation explored the nonlinear energy landscape, supplied
evidence that depth-profile relaxation mattered, and provided a one-sided
variational comparison. The strip forced explicit tests of Hamiltonian signs,
mixed-energy PIM transfer, Lagrangian subspaces, Hermiticity, and missing
Fourier couplings. High-dimensional kicks that converged to distant states
clarified the difference between a local cascade daughter and a lower-energy
long-wave state.

The variational comparison also supplied a direction, not only a discrepancy.
With the parent state and operator held fixed, restricting a Rayleigh–Ritz
perturbation space can only raise the lowest retained eigenvalue, so omitted
directions tend to delay the predicted instability. That one-sided fact helped
separate a stability-space bias from changes in the nonlinear parent state.

The retrospective therefore recommends assigning every numerical route one
of five statuses before its products approach a paper figure:

```text
paper method | referee | diagnostic | oracle | superseded
```

These labels describe authority, not quality. A strong oracle may be
ineligible to support a method claim, while a selected paper method may need
an oracle precisely because its errors differ.

This distinction also protects creativity. Agents can explore broadly without
silently changing the scientific question. A strict human constraint does
not prohibit off-boundary experiments; it requires that they be quarantined
until the human explicitly changes the boundary.

## 9. Verification Must Resolve the Scale of the Claimed Observable

The dressed stability curvature was a cancellation residual. The relevant
question was therefore not whether an FE mesh looked converged in relative
terms, but whether its **absolute** error was smaller than the residual.

The project initially tried to compare methods by interpolating one soft mode
into the other's space. That operation disturbed the `+0.19` and `-0.19`
terms by more than the `10^-4` answer. It could not distinguish a real
operator difference from projection error.

The flat-state referee succeeded because it removed the finite-amplitude
confound while retaining the same cancellation structure. The harmonics
decoupled, a dense one-dimensional solution became available, and the two
instruments could be judged against a third answer. This was a stronger test
than another refinement of either production solver.

Three related principles followed:

1. An internally smooth convergence curve is insufficient if the instrument's
   absolute error exceeds the observable.
2. A referee must be evaluated in a regime where it is independently known to
   be accurate; transferring delicate fields between discretizations can
   destroy that independence.
3. Structural identities certify the property they test, not omitted physics.
   A perfectly Hamiltonian or Hermitian truncated operator may still omit the
   Fourier channel that drives the instability.

The verifier itself also needed verification. One equilibrium-traction check
used flattened components `(P21,P22)` even though its comment correctly named
`(P12,P22)`. First Piola stress is not symmetric, so the index slip
under-reported the shear-traction defect; at the early `m<=4` states the
corrected value was roughly three to four percent of the fluctuation scale.
Because the gate only printed a warning, it could not stop the run. The repair
rule was specific: give each diagnostic a manufactured-solution test, and make
a publication gate fail the runner rather than decorate its log.

These principles explain why the project needed analytical gates, exact
limiting regimes, and distinct discretizations rather than more confidence in
one calculation.

## 10. Symmetry and Conditioning Were Part of the Physics

The period-doubling mode has a near-degenerate zone-boundary partner. A scalar
score based on vertical displacement or half-harmonic mass differed by only
about one percent between them. More careful scoring could not solve a problem
whose origin was symmetry.

Projecting the stability space into reflection classes made the mode identity
structural, but only after the reflection axis was measured from the state.
The energy is translation invariant, so a converged wrinkle may place its
crest at any phase. Reflecting about the coordinate origin is valid only when
the physical crest happens to be there. The failed projector produced smooth,
plausible, wrong values at interior loads—a more dangerous failure than a
crash.

Conditioning carried similar physical content. Splitting a paired Stroh field
into component-pure pieces created a mathematically larger raw span but
destroyed the displacement pairing that kept the physical mode numerically
resolvable. Likewise, small Gram eigenvalues were not automatically noise;
near-degenerate exponentials synthesized confluent functions in the tail.

The resulting rules are concrete:

- impose a known symmetry rather than score nearly degenerate eigenvectors;
- anchor the symmetry to a feature measured from the state;
- preserve physical field pairings when constructing reduced bases;
- report retained rank at every enrichment step; and
- noise-test a small Gram direction before discarding it.

Here, numerical linear algebra did not sit downstream of the mechanics. The
representation of symmetry and field pairing determined whether the physical
mode existed in finite precision.

## 11. Coupled Approximations Must Be Closed Together

The period-doubling threshold depends on both the finite-amplitude parent
state and the perturbation space. The quadrupling threshold adds a third
layer: the quality of the doubled parent branch. Refining only one family can
give a clean but incomplete ladder.

The clearest doubling example was the mismatch between a branch birth near
0.185 and a provisional deep-comb crossing near 0.178. The branch space was
equivalent to a shallow `7/2` comb. Once compared at the same rung, the two
calculations agreed. The remaining difference came from the parent-state
representation. The “contradiction” was a comparison of unmatched spaces.

At quadrupling, state-harmonic sensitivity measured on a shallow quarter comb
appeared to grow and suggested a large correction. At deeper comb levels the
same sensitivity shrank and reversed sign. The measured effect therefore
depended on comb depth and could not be extrapolated from the shallow rung. A
single-axis extrapolation would have assigned the wrong magnitude and even
the wrong direction to the state error.

Branch capture required the same care. An arbitrary kick can return to the
parent or jump to a distant long-wave minimum. Neither outcome proves that a
small local daughter branch is absent. The successful period-four route
lifted the validated parent and neutral-mode spaces exactly into the daughter
cell, imposed a physical amplitude constraint to cross the pitchfork, and
then released the constraint before accepting the state.

The project also had to use a convergence test appropriate to the selected
method. Rayleigh–Ritz equilibrium means that the first variation vanishes
against every retained test function. It does not make `Div P` vanish
pointwise. Teng repeatedly corrected attempts to turn the strong residual
into the method's Newton equation. The eventual protocol used nested energy
changes, residual work in newly opened analytical directions, physical-field
overlap, and stability changes as the primary convergence evidence. The
pointwise traction and `Div P` spectra were retained as independent indicators
of where the basis still needed enrichment. This avoided two opposite errors:
claiming continuum equilibrium from a small coefficient gradient, and
rejecting a valid variational solution because it was not a strong-form
collocation method.

For nested bifurcations, “convergence” is therefore a joint statement about:

- the parent equilibrium space;
- the stability or neutral-mode space;
- the map into the daughter cell;
- branch identity; and
- the residual notion appropriate to the variational method.

The headline belongs at the joint deep corner, with the final movement along
each coupled axis recorded.

## 12. Retractions Became Verification Assets

Fable's record contains several provisional values labeled frozen, later
withdrawn, and then replaced. Preserving that chronology turned each
retraction into a new gate. The first two withdrawals led from heuristic mode
scores to reflection sectors. The branch-birth mismatch required matched
state and comb spaces; the missing state-harmonic ladder required a joint
corner; the incomplete strip required a dressed Fourier-completeness test;
and unsuccessful period-four kicks led to exact cell lifting and
physical-amplitude continuation. Fable's detailed record let later agents
recover this reasoning after the original session was lost.

The record also shows why an append-only chronology needs a current-state
header. Historical words such as `FINAL`, `FROZEN`, and `WITHDRAWN` remained
valid descriptions of what was believed at their timestamps. They were not a
safe guide to what the current manuscript used. The project eventually paired
the immutable history with a short table naming the governing value,
generator, status, and superseded claims.

Nonfinal routes should be preserved without forcing a future agent to infer
the present state from hundreds of chronological entries.

## 13. Agent Autonomy Made Provenance and Communication Scientific Requirements

This project used agents that could run calculations, edit files, maintain
memory, make commits, archive modules, and disposition other agents' reviews.
That capability accelerated the work and changed the failure surface.

### Live workspace state outranked persistent memory

In one later session, persistent memory said the designated worktree had been
moved; the live path was still a symlink, and the actual move occurred later.
The lesson was narrow but consequential: a status report about a path, branch,
process, or artifact must be checked against the current workspace. More
memory does not make remembered state authoritative.

### A test could guard the wrong copy

A mixed-energy impedance bug had been corrected in the production route and a
JAX variant but remained in another shipped module. The regression test
imported the corrected variant. When that variant was archived, the broken
test was skipped as stale without checking what it protected. The wrong copy
therefore survived until a pre-submission audit executed the shipped module
against a half-space fixed-point invariant.

No manuscript number changed: the paper-relevant `pb_floquet.py` route already
had the correct update, and the analytical-depth Ritz thresholds did not call
the defective helper. The episode still showed that a guard must import the
file that ships and that skipping a broken test is a verification decision.
When one copy of a function is fixed, every copy must be found, fixed, or
removed in the same change.

The limited historical reconstruction reports a related provenance failure:
the clean-looking rev24 package omitted the then-active core theory solver. It
also records stale paths, missing uploaded modules, and smoke tests described
more broadly than the production work they exercised. Because the original
packages were unavailable to that reconstruction, this is historical evidence,
not a fresh execution audit. The lesson remains that reproducibility requires
checking both the numerical result and whether a fresh clone contains its
generating code path.

### Agent-to-agent notes did not replace user communication

Fable wrote unusually detailed handoffs to GPT and GLM, including blockers,
invariants, review dispositions, and offers of reusable states. Yet Teng did
not receive an equally concise early statement distinguishing the
analytical-depth Ritz route, the element-like strip, and the remaining
depth-nodal paper assets. The technical documentation was strong while the
method-boundary status was too distributed.

After this episode, a method pivot required a short user-facing update:

```text
What method is actually running?
Does it cross a stated boundary?
What claim can it support?
What remains exploratory?
```

### Reproducibility became an artifact graph

When several agents touch shared files, prose provenance is too weak. The project
moved toward a directed chain:

```text
runner -> numerical artifact -> claims ledger -> figure/manuscript -> manifest
```

A finding was considered closed only when the implementation, comparison
artifact, and physical interpretation agreed. A hash could freeze local bytes
without making them available in a clone; a saved `converged=true` flag could
describe an old source state; and a smooth plotted branch could contain
nonstationary points. Each claim required the portion of the graph that could
actually support it.

Manuscript editing had the same directional constraint. The 7 July draft held
the intended cascade narrative but still contained depth-FE methods and
numbers; a later draft contained the governing analytical-depth evidence but
had shifted the narrative. Neither was a safe whole-file baseline, so claims
had to be ported individually. In another round, an artifact value of
`1.083e-8` became “below `1e-8`” after being copied from summary prose. The
project therefore treated quantifiers and inequality directions as numerical
claims: transcribe from the artifact and round bounds outward.

In an agent-driven project, workspace state, method identity, and evidence
lineage are components of the scientific result.

---

# Part III — Collaboration and Attribution

---

## 14. Teng's Highest-Leverage Contributions

Teng defined the scientific program as a nonlinear analytical extension of
the earlier symplectic theory and selected period doubling as the first
secondary bifurcation. His interventions fixed the problem's governing
constraints: the `(J-1)^2` constitutive gate, no depth-nodal paper method,
finite amplitudes from energy stationarity rather than solvability, and weak
residuals interpreted consistently with Rayleigh–Ritz equilibrium.

Those constraints operated in both directions. Teng declined the early
in-range estimate while its amplitude calibration remained unresolved, then
declined to accept either the higher reduced threshold or the depth-FE oracle
as closure of the requested analytical method. He prioritized method identity,
carrier maps, branch classification, and paper provenance over adjustment of
the last digit. Teng retained the final scope and stopping decisions.

## 15. Attribution and the Multi-AI Review Loop

The useful unit of multi-AI review was a disagreement converted into a
falsifiable artifact, not a vote among models. The surviving record supports
the following contribution ledger:

| Contributor | Documented role |
|---|---|
| **Teng Zhang** | Scientific and editorial owner: defined the problem, supplied the earlier symplectic framework and mechanics judgment, imposed and later refined the method contract, selected manuscript claims, and retained final responsibility. |
| **Fable / Claude Fable 5** | Primary architect and principal contributor to the analytical-depth computational method: global analytical-depth state evaluated with the unexpanded energy, analytical stability dictionaries, doubled-cell representation, reflection sectors, branch-capture practices, coupled ladders, and much of the convergence and error-budget logic. |
| **GLM** | Found four defects in the experimental PIM strip and rebuilt its critical propagation step on the validated mixed-energy convention. The repaired strip remained diagnostic rather than production. |
| **Codex / GPT** | Performed the principal source and physics audit, including correction of its own initial overbroad signed-harmonic criticism; later contributed carrier-correct `T45` closure, exact period-four lifting and continuation, diagnostic hardening, and paper-facing asset integration on Fable's framework. |
| **Kimi, DeepSeek, and other reviewers** | Supplied independent manuscript, convention, hierarchy, bound-transcription, provenance, and presentation checks with their scopes recorded in project notes. |

Fable's retractions belong in this ledger. Fable withdrew premature values,
accepted findings that reopened the calculation, preserved failed hypotheses,
and wrote handoffs detailed enough for other agents to reconstruct the work
after session loss. Those acts made the eventual audit possible.

The earlier `FastNodal/FullNodal` depth-FE route is not assigned to Fable as an
original implementation because the surviving record does not establish its
authorship. The evidence supports a narrower statement: inherited depth-nodal
assets remained in the Fable-era pipeline under an overbroad label; Fable
later acknowledged the mismatch and did the substantial work of building the
replacement analytical-depth framework. Authorship of the historical
`rev27_full_enrichment.py` asset is likewise not established by the available
records. A shared, sometimes uncommitted worktree does not support reliable
line-level attribution.

The review loop was most effective when it followed a five-step protocol:

1. the builder stated the method and its weakest points;
2. a reviewer traced the actual generator and tried to falsify a claim;
3. an executor changed the code and produced a new artifact;
4. the finding closed only when implementation, artifact, and physical
   interpretation agreed; and
5. Teng decided whether the result could enter the paper.

Not every review finding survived source inspection. Codex's initial
conflation of the real-valued production comb with the incomplete complex
strip is the clearest counterexample, and the review record preserves the
correction. Independent models broadened coverage because their claims were
tested against code and mechanics; no individual AI verdict was treated as
self-authenticating. Several confident “JMPS-ready” assessments preceded
source-level findings of real errors, so reviewer confidence and consensus
never replaced an independent gate.

---

## Summary

The project is best understood through its **method genealogy**:

```text
2017 linear Hamiltonian–Stroh framework
        |
        v
weakly nonlinear and reduced finite-amplitude estimates
        |  useful mechanism; amplitude and representation still open
        v
Fourier × depth-FE oracle near the observed range
        |  evidence for depth freedom; method label found too broad
        v
Teng's no-depth-node method boundary
        |
        v
Fable analytical-depth unexpanded-energy Ritz framework
        |  conditioning, symmetry, branch, and joint-ladder rebuilds
        v
independent source audits and targeted repairs
        |
        v
final retained-space results: PD 0.179, lattice 0.176, T45 0.244
```

The nonfinal routes made distinct contributions. The depth-FE calculation
provided an oracle and evidence for the importance of depth freedom. Fable's
incomplete PIM strip forced convention and structural checks. Withdrawn
thresholds exposed the missing mode, state-space, and refinement gates that
the later calculation had to pass.

The evidence supports the following transferable lessons:

- a method must be identified from its unknowns and assembly;
- exploratory evidence must carry an explicit claim status;
- an instrument must resolve the absolute scale of the observable;
- diagnostics, tests, and reviewer verdicts need gates that can falsify the
  claim they are asked to certify;
- physical symmetry can be more reliable than heuristic mode scoring;
- parent-state and stability approximations must be refined together;
- a local daughter branch must be captured by its physical identity, not by
  whichever minimum a kick finds;
- retractions are valuable when their causes and artifacts are preserved;
- agent-to-agent reasoning does not replace concise communication with the
  human owner; and
- in autonomous research workflows, provenance and current-state checks are
  part of verification rather than clerical work.

The final record shows a clear division of labor. Teng kept the scientific
claim tied to the requested method; Fable built and repeatedly repaired the
analytical-depth framework after the depth-nodal closure was rejected; and
independent reviewers tested distinct call paths, invariants, and branches.
The resulting method is more carefully named, more limited, and more
defensible. That change—not recovery of a preferred decimal—is the main
outcome of the project.

---

## Evidence Record

This case study was checked against the following internal project records:

| Record | Evidentiary role |
|---|---|
| `symplectic_wrinkles/WRINKLE_PD_PROJECT_LESSONS.md` | Historical reconstruction of the early and depth-FE phases; explicitly limited and pre-turnaround |
| `symplectic_wrinkles/project_progress.md` and `lesson.md` | Historical project summaries of the 2017 seed, nonlinear program, and early human–AI lessons |
| `analytic_depth_method/PROGRESS.md` | Append-only chronology begun by Fable and later updated during Codex/shared closure |
| `analytic_depth_method/METHOD_RETROSPECTIVE.md` | Fable's account of mode identification, conditioning, and falsifiability failures |
| `analytic_depth_method/CAMPAIGN_SUMMARY_2026-07-11.md` | Artifact-indexed summary of the sector, branch, and joint-ladder campaigns |
| `analytic_depth_method/FABLE_RESPONSE_TO_GPT_REVIEW.md` | Finding-by-finding acceptance, correction, and rerun record |
| `analytic_depth_method/CODEX_SOURCE_AUDIT_OF_FABLE_2026-07-11.md` | Independent call-path, physics, method-classification, and provenance audit, including reviewer self-correction |
| `analytic_depth_method/ANALYTICAL_DEPTH_TURNAROUND_RETROSPECTIVE_2026-07-12.md` | Dated Codex attribution ledger and technical chronology |
| `analytic_depth_method/PAPER_METHOD_DATA_FIGURE_UPDATE_REPORT_2026-07-12.md` | Governing method integration and final credit record, subject to its dated addenda |
| `analytic_depth_method/CODEX_JMPS_MANUSCRIPT_REVIEW_2026-07-17.md` | Snapshot audit of manuscript commit `18c964a`, covering physics, equations, data, figures, code paths, and retained-space limitations |
| `analytic_depth_method/GPT_REVIEW_PUBLIC_REPO_AND_CASE_STUDY_2026-07-19.md` | Snapshot audit of public HEAD `6584809` and case-study v0.9, including independent recomputation of both lattice crossings |
| `analytic_depth_method/LESSONS.md` | Failure-to-rule ledger, including method identity, coupled ladders, handoffs, provenance, and test-scope lessons |
| `pd-analysis/paper/JMPS_manuscript.tex` and `pd-analysis/results/paper_numerical_claims.json` | Governing final method wording and numerical values |

### Source hierarchy and limits

The three summaries under `symplectic_wrinkles/` do not govern the final
calculation. `WRINKLE_PD_PROJECT_LESSONS.md` explicitly reconstructs the early
history without the original software packages and ends before the decisive
10–12 July analytical-depth turnaround. `project_progress.md` is a
pre-turnaround checkpoint, while `lesson.md` is a thematic record of earlier
equation and workflow failures.

For the turnaround itself, the shared chronology, campaign summary, and
Fable's response establish the sequence of construction and retraction. The
source audit establishes the Fable-era production call paths and records the
reviewer's correction. The dated turnaround retrospective establishes the
method distinctions and contribution ledger. The integration report, claims
ledger, and current manuscript govern the final method wording and numerical
values. Historical labels such as `FINAL` and `FROZEN` are quoted as states of
knowledge at their dates, not as current authority.

The records do not establish the original author of the historical
`rev27_full_enrichment.py` or every line in the shared worktree. This account
therefore attributes architectures, dated interventions, and audited outputs;
it does not infer authorship from a filename, session owner, or later file
location.

---

*This case study documents the symplectic wrinkle period-doubling and
quadrupling project from January through July 2026. The companion manuscript
is being prepared for submission to JMPS. The planned public companion
repository is
[nonlinear-symplectic-wrinkle-bifurcations](https://github.com/tengzhang48/nonlinear-symplectic-wrinkle-bifurcations).*

**Version:** 1.0 (substantive rewrite for author review)

**Last Updated:** July 2026

**Evidence review and rewrite:** Codex (GPT-5), 19 July 2026
