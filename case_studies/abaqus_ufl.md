# Case Study: From Code Generation to Scientific Evidence — `abaqus_ufl`

**How a UFL-inspired Python-to-Fortran prototype became a broader program of
compiled-element testing, Abaqus validation, example porting, and
release-level evidence control.**

**Participants and naming.** Teng Zhang is the human scientific owner. Saved
project records identify Fable/Claude, Codex/GPT, Kimi, DeepSeek, GLM,
Gemini, Qwen, and other AI systems as contributors or reviewers at different
stages. Their roles changed over time. This study assigns a contribution to a
named participant only where a dated note, commit, or retained artifact
supports it; a shared worktree does not support line-by-line authorship.

---

## Contents

1. [Overview](#1-overview)
2. [Evidence map and scope](#2-evidence-map-and-scope)
3. [The first phase: connecting declarative mechanics to Abaqus](#3-the-first-phase-connecting-declarative-mechanics-to-abaqus)
4. [The May 24 transition: validation became the center of the project](#4-the-may-24-transition-validation-became-the-center-of-the-project)
5. [The second phase: validation became the larger project](#5-the-second-phase-validation-became-the-larger-project)
6. [Why the examples mattered](#6-why-the-examples-mattered)
7. [Durable technical lessons](#7-durable-technical-lessons)
8. [Human–AI collaboration after agents could execute the work](#8-humanai-collaboration-after-agents-could-execute-the-work)
9. [Review, authorial authority, and the danger of over-correction](#9-review-authorial-authority-and-the-danger-of-over-correction)
10. [Scientific lineage and credit](#10-scientific-lineage-and-credit)
11. [Audited July 28 snapshot](#11-audited-july-28-snapshot)
12. [Summary](#12-summary)
13. [Evidence record](#13-evidence-record)

---

## 1. Overview

In the current public subset, `abaqus_ufl` lets a researcher describe a
constitutive response or a supported finite-element weak-form template in
Python and generate a self-contained Abaqus UMAT or UEL in fixed-form
Fortran. The interface is inspired by the declarative style of the Unified
Form Language (UFL), but it does not depend on UFL, implement UFL, or compile
arbitrary variational expressions. The framework translates a defined
vocabulary of material methods, fields, interpolation choices, balance terms,
local variables, and tangent policies into Abaqus-compatible source.

That distinction matters historically. The original idea joined two parts of
Teng Zhang's prior experience:

- coupled large-deformation and diffusion mechanics implemented in FEniCSx;
- Abaqus UMAT and UEL development, including the interface and fixed-form
  Fortran constraints that make user elements difficult to audit.

Early conversations with Claude helped turn those two bodies of experience
into a software architecture: users would write the problem-level material
responses and supported balances in Python, while the framework would own
repeated assembly, differentiation, DOF packing, and source generation. This
origin story remains important.

It is no longer the whole story.

An early March 2026 case-study draft described a Python prototype with a
substantial test suite and recorded that, at that draft's checkpoint, its
generated Fortran had not yet been compiled or exercised in Abaqus. That was
an early historical state, not the state of the project on May 24. By late
April and early May, generated UEL and UMAT source had already been compiled
and executed through the internal `feacheap` host, including a gel Hex20
end-to-end path and a coarse corrosion run.

May 26 marked a narrower but important boundary: the project added the first
retained direct f2py validation harness and began a systematic live
Abaqus/Expanse validation campaign. The workflow compiled generated sources,
ran Abaqus jobs on the Expanse system at the San Diego Supercomputer Center,
inspected ODB results, ported additional examples, and eventually tested the
public release as an artifact. The retained commits and run log establish
these project actions but do not identify the operator of every command.

Those activities exposed a deeper project:

```text
declaration
  → emitted Fortran
  → compiled subroutine
  → element call
  → assembled solver problem
  → completed analysis
  → raw output
  → extracted data
  → figure and claim
  → curated public release
```

Every arrow is a possible failure boundary. A correct Python derivative does
not prove correct Fortran packing. A compiled element does not prove correct
weak-form signs. A completed solver job does not prove every coupled field
converged. A sound ODB does not prove that a visualization bridge mapped every
state variable. A validated lab example does not prove that a clean public
archive contains the source, deck, data, and instructions needed to reproduce
it.

The most durable result of the post-May work was therefore not a larger
example count. It was a change in the meaning of “done.” Generated scientific
software became acceptable only through artifact-specific evidence with a
different failure mode from the code path it was intended to check.

---

## 2. Evidence map and scope

This case study draws from three different scopes. They must not be collapsed:

1. **Full research project.** The private lab contains the evolving generator,
   many research ports, validation tools, solver experiments, cluster results,
   development notes, and unpublished work.
2. **Manuscript evidence.** The paper reports a selected set of formulations
   and examples at explicitly stated evidence levels.
3. **Public release.** The public repository is a curated subset at a
   particular revision, built with an explicit licensing boundary. The later
   credit audit still found that the exact BSD notice and redistribution
   status of the Cui-derived comparison mesh needed to be recorded for an
   archival release. Curation intent must not be confused with a completed
   license review. The subset is not a permanent capability map for the full
   project.

The four paper examples do not define everything the package can do. The
private example inventory likewise does not mean that every example has
reached the same verification level. A directory count is evidence of
development activity, not evidence of scientific validity.

| Episode | Controlling evidence | What it supports | What it does not support |
|---|---|---|---|
| Early architecture | Historical case-study draft; March–May design notes and commits | Origin of the declaration layer, code-generation strategy, and principal design decisions | Correctness of the later generated Fortran or Abaqus analyses |
| Direct-wrapper and live-Abaqus transition | May 26 f2py, Abaqus-validation, and Expanse commits; `abaqus_validation/VALIDATION_RUN_LOG.md` | Generated source entered direct compiled calls and live Abaqus paths; interface failures were observed and repaired | The first-ever compilation of generated source or independent verification of every constitutive equation or element |
| Adversarial validation | June audit reports, validation-harness documentation, known-broken controls | Tests with identified failure modes can detect specific history, tangent, sign, and packing errors | Universal correctness of every generator path or physical model |
| Abaqus benchmark | Submitted source, exact deck, job log, ODB, extracted records, and comparison script for the stated case | Solver execution or quantitative reproduction under the recorded conditions | Physical validation beyond the benchmark or validity after untracked source changes |
| Paper figure | Retained image, raw or reduced data, extraction script, and frame map | The displayed quantity at the recorded run state | Provenance inferred only from today's renderer or generator |
| Public package | Public commit, allowlist, tests run from that checkout, license and citation metadata | Scope and passing package tests of the curated core and released examples | Clean reproduction of every paper package, the complete research inventory, or all future package capabilities |
| Collaboration history | Named prompts, reviews, handoffs, signed notes, and commits | Recorded roles, corrections, and decisions at particular stages | Fine-grained authorship not preserved by the record or independence merely because several agents agreed |

Two revision coordinates govern the July 28 snapshot used here:

- private lab: `56a6420`;
- public release checkout: `a1b5825`.

At the public revision, `pytest -q` produced `125 passed` on July 28, 2026.
That number describes one test collection at one commit. It is not a
standalone scientific claim and should not be copied forward without its
revision and command.

The pinned private revision was not fully green. At committed `56a6420`,
`pytest -q tests/test_uel_gen.py` produced `1 failed, 10 passed` because one
test still expected a retired `LFLAGS(3)=4` branch. A later uncommitted
working-tree repair made that targeted suite pass, but it is not evidence
about the pinned commit. The case therefore does not describe the whole lab
suite as passing at `56a6420`.

---

## 3. The first phase: connecting declarative mechanics to Abaqus

### 3.1 Starting from mechanics and reference implementations

The project did not begin from an empty codebase or an empty scientific
tradition. Teng brought prior coupled gel formulations, a three-field
displacement–pressure–chemical-potential implementation in FEniCSx, and years
of experience with Abaqus user subroutines. Several shared or published
implementations supplied distinct kinds of prior knowledge:

- Shawn Chester's UMAT was used historically to study Abaqus conventions such
  as state layout, initialization, and time-step control.
- The supplemental gel UEL associated with Shawn Chester, Claudio Di Leo, and
  Lallit Anand supplied an important scientific and finite-element reference:
  a coupled gel implementation, local solution of a constitutive volume
  variable, volumetric treatment, and Abaqus output patterns.
- Bibekananda Datta and Thao D. Nguyen's modular hydrogel UEL supplied another
  total-Lagrangian implementation and prompted explicit comparison of stress
  measures and assembly choices.
- Allan Bower's EN234_FEA teaching code, later extended internally as
  `feacheap`, supplied an executable finite-element host for Abaqus-compatible
  subroutines outside Abaqus.

These sources did not all play the same role. Some supplied formulation
lineage, some interface conventions, some a benchmark or tangent oracle, and
some an execution environment. “Inspired by,” “compared against,” “adapted
from,” and “redistributed” are different relationships and require different
evidence and licensing decisions.

### 3.2 The main architectural choices

The historical draft records several decisions that remained important.

**Generate a UEL rather than hide coupling behind separate material
interfaces.** A UMAT plus a thermal or transport material can be a practical
route for some coupled problems. A UEL exposes the complete coupled residual,
DOF map, cross-field blocks, interpolation, and state update. Once repeated
assembly is generated, the UEL's extra implementation burden is shifted from
every new material model into the framework.

This does not make UEL development trivial. The later validation phase showed
that node-dependent DOFs, unsymmetric blocks, procedure flags, state
commitment, output bridges, local condensation, and solver scaling remain
substantive. The framework makes those obligations explicit and reusable; it
does not remove them from finite-element mechanics.

**Use first Piola–Kirchhoff stress in the finite-deformation declaration
path.** This aligns naturally with a reference-configuration displacement
residual. The choice also matched Teng's prior formulation experience. The
important historical point is not that one stress measure is universally
superior, but that the declaration and generator need one unambiguous stress
contract.

**Promote or eliminate local variables deliberately.** The original gel
reference solved a local variable at each integration point. Teng's earlier
three-field formulation promoted pressure to a global field. The project
eventually supported both globally interpolated pressure paths and
element-local pressure followed by condensation. Later tests showed that
these are not cosmetic alternatives: each creates a different solver and
verification contract.

**Emit self-contained Fortran.** The target was source that could enter the
Abaqus build process without a Python runtime. This led to an AST-based
translation layer, fixed-form line handling, tensor helper routines, and
generator templates. It also created a new obligation: helpers, templates,
declarations, and emitted source could diverge while Python-level tests still
passed.

### 3.3 How the UFL-inspired interface emerged

The valuable insight in the original case study was conversational. Teng knew
the declaration style of FEniCSx/UFL and the practical constraints of Abaqus
subroutines as separate workflows. Claude contributed software-architecture
patterns—translation, templates, material/weak-form interfaces, and generated
helpers—while Teng supplied the mechanics, the target conventions, and the
judgment about which information a user should declare.

The record supports the statement that the interface crystallized through
those exchanges. It does not support the stronger counterfactual that neither
participant could ever have developed it independently. The durable claim is
the observed one: conversation connected two bodies of expertise and produced
an implementable architecture.

The package name records that origin, but also creates a responsibility:
`abaqus_ufl` must be described consistently as UFL-inspired and not
UFL-compatible.

### 3.4 Complex-step differentiation was an engineering choice, not magic

Complex-step differentiation made it possible to calculate many material
tangent blocks without building a complete symbolic differentiation compiler.
For an analytic active code path, a small imaginary perturbation avoids the
subtractive cancellation of ordinary finite differences.

The early draft overgeneralized this strength. Later examples exposed the
conditions:

- real-part extraction can silently destroy the derivative;
- `abs`, clipping, ordering, branch cuts, and branch changes need explicit
  treatment;
- a history-dependent update must restart every perturbation from the same
  committed state and recompute the trial update;
- repeated eigenspaces require invariant or carefully regularized
  reconstruction, not the assumption that an imaginary perturbation
  automatically resolves every degeneracy; and
- agreement between complex step and finite difference can reproduce the same
  wrong governing equation.

Complex step remains useful because its domain of validity can be stated and
tested. It is one tangent source and one consistency gate, not an independent
oracle for the physics.

---

## 4. The May 24 transition: validation became the center of the project

The original March case-study draft ended at an honest but revealing
checkpoint: the Python prototype had 128 passing tests, while generated
Fortran had not yet been compiled or run in Abaqus at the time represented by
that draft. Those tests established useful properties of the Python
framework—translation behavior, local identities, source patterns, and
selected derivative checks. They could not establish:

- that Abaqus's compiler accepted the emitted fixed-form source;
- that array dimensions and DOF packing matched the real subroutine call;
- that trial and committed state were ordered correctly across increments;
- that assembled residuals and tangent blocks matched an external oracle;
- that the chosen Abaqus procedure activated the intended fields;
- that an ODB output bridge exposed the values actually computed by the UEL;
  or
- that a clean external checkout reproduced the claimed workflow.

That checkpoint did not remain current for long. Before May 26, generated code
was already running through `feacheap`: the April 22 history records a gel
Hex20 end-to-end path, the May 13 history a coarse Cui corrosion run with
MUMPS, and the May 18 repository state a generated Mooney–Rivlin smoke case.
These were valuable solver-level checks, but they did not provide the later
direct-wrapper and live-Abaqus evidence.

On May 26, commits `6a82ed6`, `84f1a25`, `32a1571`, and `dadae39` added the
retained f2py harness, generated-material validation, an Abaqus validation
workspace, and Expanse execution. The first benefit of this systematic
campaign was not confirmation. It was failure.

An unguarded write to a second right-hand-side column appeared on a Riks path.
Mixed-order user elements needed corrected DOF declarations. Abaqus smoke
decks needed procedure and activation fixes. These were precisely the defects
that a source-only test was unlikely to expose.

This changed the project's center of gravity. Between the near-May checkpoint
and lab revision `56a6420`, tracked example directories increased from 25 to
39 and tracked `test*.py` modules from 33 to 74. Those counts are not a
capability claim. They show where the work moved: from producing a generator
to exposing it to more formulations, calling paths, and failure mechanisms.

---

## 5. The second phase: validation became the larger project

### 5.1 May 26–29: compilation and Abaqus execution became explicit gates

The first validation workspace separated several questions that had previously
been blended:

```text
Can Python evaluate the model?
Can the generator emit source?
Can a Fortran compiler build it?
Can a direct wrapper call it?
Can Abaqus activate the intended DOFs and procedure?
Can a nontrivial analysis complete?
Does an independent quantity agree?
```

A failure at one level did not erase evidence at lower levels. A source could
compile correctly while a deck used the wrong procedure. A smoke run could
prove field activation while saying little about a long transient. The
validation log later reclassified older runs of an internal port as
pre-correction smoke evidence when generator changes made them inapplicable as
validation of the current source. This was an important move away from
permanent labels such as “validated.”

### 5.2 May 31–June 15: more examples exposed common-mode verification

The project ported corrosion, gel, and additional unpublished coupled
formulations. The scientific value was not the inventory. Each port placed
stress on a different transformation boundary: additional field types,
history ordering, flux signs, local iterations, spectral functions,
node-dependent DOFs, or cross-field tangents.

An adversarial package audit in June found four high-severity defects despite
the existing tests:

- multi-history scalar arguments were ordered incorrectly on a tangent path;
- repeated-eigenvalue handling could erase complex-step derivatives;
- old-state arguments could be fixed at numeric defaults in a symbolic
  tangent; and
- a translated Python loop bound could become an out-of-bounds Fortran loop.

The strongest lesson came from a phase-field flux-sign error. Complex-step
versus finite difference passed. The source compiled. A 120-element solve ran.
All three paths shared the same wrong equation, so none could detect its sign.

The validation harness adopted a sharper rule:

> A gate is not trusted until a known-broken implementation makes it fail for
> the intended reason.

This is stronger than simply adding more tests. A negative control describes
what the gate can falsify.

### 5.3 June 16–20: a non-Abaqus host exposed solver-level defects

The project built a small Python finite-element driver, then added PETSc and
direct execution of compiled `abaqus_ufl` elements. This was an offshoot, not
a replacement for Abaqus. It supplied another host for the same element
contract and exposed failures at a different boundary.

One nonsymmetric tangent was silently transposed because Fortran and C array
memory order were interpreted differently. A mechanics-dominated global
residual norm let a weak transport field satisfy the solver's stopping test
too early. Field-wise convergence control changed the six-hour gel response
to within 0.5% of the comparison target.

These episodes showed why “the Newton solver converged” is incomplete for a
multiphysics problem. Scaling and stopping must be assessed by field, and an
unsymmetric block must survive generation, memory layout, packing, and the
linear-solver path.

### 5.4 Corrosion: solver output and visualization were separate systems

The phase-field stress-corrosion example became the strongest quantitative
code-to-code benchmark. Under the recorded comparison setup, the original and
generated UEL runs reached 903 s with final pit depths of
`46.6408208 µm` and `46.6408216 µm`, respectively. Over the matched history,
the audit reports a mean absolute error of `0.1302 µm`, a maximum absolute
error of `0.6302 µm`, and a normalized $L_2$ error of about `0.64%`. The
nearly identical endpoint should therefore be read with the full-history
errors, not as pointwise identity.

The two paths were also not identical in every condition. The retained
Supplement records different bottom-corner pins, one-increment lagging of
$\mathcal L_n$ in the generated implementation, and different treatment of
the repassivation clock during the initial setup steps. These differences are
part of the benchmark scope rather than details to hide behind the endpoint.

That agreement did not make the workflow complete. A numerically valid ODB
initially contained 12,180 missing or all-zero UVARM records; the surviving
nonzero block was shifted onto incorrect element labels, and integration
points 3 and 4 were reversed. The UEL calculation, the dummy visualization
mesh, the UVARM bridge, ODB extraction, and the published contour were
separate systems. A correct state inside the element could still be
represented incorrectly outside it.

The debugging sequence therefore had to distinguish:

```text
field activation
  ≠ element computation
  ≠ state-to-dummy transfer
  ≠ ODB coverage
  ≠ extraction and plotting
```

The reference-source hashes, the exact submitted source, and the output
coverage record became part of the benchmark evidence. A visually plausible
contour was not enough.

### 5.5 Mixed-order bilayer: solver completion did not validate converted topology

Porting a bilayer from a lower-order mesh to a mixed-order Quad8 UEL exercised
node-dependent DOF maps and boundary-set conversion. Two Abaqus jobs completed
but were rejected because the right-edge set omitted midside nodes. The
corrected job completed 2,160 increments to 21,600 s and reduced the final
edge-straightness residual to $2.27\times10^{-9}$ m.

The scientific lesson is not the job count. It is that a topology conversion
changes the boundary-value problem. A solver can complete a different,
internally consistent problem after a boundary set silently loses nodes.
Converted connectivity, node classes, DOFs, loads, and constraints therefore
need structural audits before field plots are interpreted.

This example established mixed-order mapping and execution at its recorded
scope. It did not automatically become a quantitative reproduction of the
original lower-order formulation, because the pressure treatment,
interpolation, and material compressibility had changed.

### 5.6 Local pressure: the eliminated variable had to be re-solved inside the test

The element-local-pressure gel formulation was the project's most distinctive
untested tangent path. Local pressure $p^\ast(\mathbf{x})$ is found from
$R_p(\mathbf{x},p)=0$, then eliminated through a Schur complement. Checking
the four uncondensed blocks separately does not prove the derivative of the
complete condensed residual:

$$
\frac{d\overline{\mathbf R}_x}{d\mathbf x}
=
\frac{d\mathbf R_x(\mathbf x,p^\ast(\mathbf x))}{d\mathbf x}.
$$

The final black-box test compiled the committed UEL, perturbed every global
element DOF, called the same entry point from the same committed state, and
thereby forced the local pressure solve to run again for every perturbation.
Per-DOF perturbation scales were needed because displacement and chemical
potential differed by several orders of magnitude.

The Quad4 and Hex8 relative errors were $5.4\times10^{-10}$ and
$6.5\times10^{-10}$. More importantly, the test measured the
discriminator: $\max |dp^\ast/dx|$ was nonzero and large enough to show that
the Schur contribution was active. A deliberately frozen-pressure tangent
failed with an error of `0.76`.

Several rounds of careful prose had not closed this gap. One executable test
did, because it crossed the complete compiled-element boundary and included a
negative control.

### 5.7 Morphing: the companion mesh was not mechanically negligible

The three-dimensional morphing deck paired the generated UEL with native C3D8
elements used for output and model coupling. It would be inaccurate to call
that native mesh a negligible visualization overlay. The exact production
deck assigns it a Neo-Hookean material, explicitly states that it contributes
to stress equilibrium, and gives it an initial shear modulus of 200 compared
with 800 in the UEL property set.

The resulting Figure 6 deformation therefore belongs to a mechanically
combined UEL/native-element model. A future claim about the UEL-only response
would need a stiffness/reaction sensitivity study or a rerun with a
mechanically negligible, independently justified output layer. This example
shows why a “dummy” or “visualization” label must be checked against the deck,
material constants, and reaction contribution.

### 5.8 July release work: a public subset created a new verification target

The public repository was created from a positive allowlist rather than by
publishing the private lab history. That choice was driven by scientific,
privacy, and licensing boundaries:

- the full lab contains unpublished research examples and internal notes;
- the corrosion comparison deck retained a mesh derived from the Cui reference
  distribution and therefore required an explicit redistribution review;
- the internal `feacheap` fork did not have a sufficiently complete upstream
  revision and license record for the first public release; and
- a public example must be tested without hidden imports from the lab.

A positive allowlist reduced accidental leakage but did not itself settle the
provenance of artifacts built from external files. The later credit audit
clarified two different cases.
The accepted bilayer deck is our build output for the swell-induced bending
problem of Chester, Di Leo, and Anand; its mesh discretization follows their
supplemental example with attribution, and their original files are not
redistributed. The corrosion comparison mesh comes from a BSD-stated reference
distribution, and its precise notice and redistribution status still need to
accompany an archival release.

The clean-archive paper-example audit also found that the phrase “exact
reproduction packages” was premature at `a1b5825`:

- all four figure scripts retained lab-layout paths and did not run unmodified
  from the clean archive;
- the corrosion pipeline failed after generation and the public inputs did not
  reconstruct the complete Figure 3 comparison;
- the accepted bilayer deck was included, but rerunning its builder required a
  separately obtained Chester–Di Leo–Anand supplemental input to seed the
  mesh;
- the morphing run instructions referenced source outside the stated working
  directory; and
- the public Python suite did not exercise `paper_examples/`.

The packages still preserve useful declarations, submitted sources, decks,
reduced data, and figure inputs. Their presence is evidence of curation, not
yet clean end-to-end reproduction.

This produced another important distinction:

```text
verified in the lab
  ≠ included in the public checkout
  ≠ reproducible from the public checkout
  ≠ archived under an immutable tag and DOI
```

At the July 28 snapshot, the public checkout was clean and its Python suite
passed at commit `a1b5825`. No public Git tag was present locally, and
`CITATION.cff` still marked the release date and DOI as pending. The correct
description is therefore revision-specific; anticipated archival steps should
not be written as completed facts.

---

## 6. Why the examples mattered

The project added many examples after May 24, but “more examples” is not itself
a scientific result. Their durable role was as specification tests for a code
generator.

| Example pressure on the framework | Transformation boundary exercised |
|---|---|
| Stateful plasticity and damage | committed/trial state, branch recomputation, tensor state layout |
| Coupled corrosion and additional coupled transport formulations | residual signs, transport units, cross-field blocks, field scaling |
| Materials requiring spectral functions and additional field types | spectral functions, additional field types, constitutive tangent oracles |
| Mixed-order gels | node-dependent DOFs, connectivity conversion, interpolation contracts |
| Element-local pressure | local Newton solve, cutback behavior, Schur condensation |
| Stabilized tetrahedra | topology-specific quadrature, stabilization terms, element length, and non-affine material/weak-form derivative states with nonzero volumetric-field gradient |
| Abaqus companion meshes and UVARM bridges | state projection, output coverage, and whether a nominal visualization mesh also changes the mechanics |
| Compiled-element Python/PETSc host | ABI, memory order, unsymmetric assembly, field-wise stopping |

This table is a map of validation pressures, not a package capability table.
The full research portfolio continues to evolve, and examples at different
stages support different claims.

A useful new-example policy emerged:

1. identify which generator path or scientific mechanism the example is meant
   to exercise;
2. choose an oracle that does not inherit the same representation;
3. include a broken control that the gate must reject;
4. distinguish material-point, element, solver, benchmark, and physical
   evidence;
5. preserve the exact submitted source and run inputs if results will be
   published; and
6. port the example into a clean release only after its lineage is recorded
   and, if it contains or derives from third-party artifacts, redistribution
   terms are resolved.

Under this policy, porting is not clerical work. A post-generation patch, a
special-case deck edit, or a copied helper is evidence that the declaration
language or package contract may be incomplete.

---

## 7. Durable technical lessons

### 7.1 Validation is a versioned evidence graph, not a green test count

A result should be identified by at least:

```text
model + source revision + state/regime + artifact + probe + tolerance
```

Historical validation can become stale after a source correction. A test
total can grow while important paths remain unexercised. The validation log's
reclassification of pre-correction runs is a stronger practice than preserving
a permanent “validated” badge.

### 7.2 Independence is structural, not social

Two agents, two scripts, or two languages can still inherit the same weak form,
sign, state ordering, or generated source. The flux-sign episode passed
complex-step, compilation, and a full solve because those checks shared one
wrong equation.

Independent evidence means a different plausible failure mode: a closed-form
limit, an analytic tangent, a black-box perturbation across the compiled entry
point, a conservation balance, a mechanism-removing control, or an
independently built deck. A published reference implementation is independent
only at the code-path level if it still shares the governing equations, mesh,
initialization, or deck ancestry. The corrosion UEL comparison is a valuable
implementation oracle, not an independent physical validation.

### 7.3 The state machine is part of the constitutive model

For history-dependent UMATs and UELs, the equations alone do not define the
algorithm. The implementation must distinguish committed state, trial state,
local iteration state, accepted increments, rejected increments, and cutbacks.
A derivative perturbation must replay the trial update from the same committed
state. Writing state too early can make a tangent locally plausible and
globally inconsistent.

### 7.4 Condensation must be verified after elimination

Separate checks of $K_{xx}$, $K_{xp}$, $K_{px}$, and $K_{pp}$ are
useful but insufficient. The complete condensed residual must be perturbed
while the eliminated variable is re-solved. The test must also show that the
eliminated variable actually changes; otherwise a passing result may be
vacuous.

### 7.5 Solver completion is an execution result, not a scientific verdict

The corrosion UVARM failure, the bilayer boundary-set failure, and the
field-wise convergence failure all occurred around solver-complete or
numerically plausible runs. Completion establishes only that the configured
discrete system reached the solver's acceptance condition. The scientific
question may depend on output coverage, field-specific residuals, boundary
topology, or an independent quantitative observable.

### 7.6 Current source is not historical run provenance

A retained PNG may predate today's renderer settings. A generated Fortran file
used by a cluster job may differ from today's generator output. A current deck
may have been repaired after the published run.

The cross-check direction should be downstream:

```text
claim about a figure   → inspect the retained figure and its inputs
claim about a run      → inspect submitted source, deck, log, and ODB
claim about a release  → inspect the files and tests in the released archive
```

An upstream script is evidence about possible lineage, not proof of the
downstream artifact's state.

### 7.7 A post-generation patch identifies a missing declaration primitive

The corrosion workflow once regex-patched a generated residual-stiffness
constant because the generator could not inline a model constant without
changing the runtime property layout. The durable repair extended the
declaration language so a class attribute could be emitted as the same
literal used by the archived run.

The lesson is broader: a reproducible patch is still a breadcrumb. If the
project's promise is declaration-controlled generation, repeated edits to
emitted artifacts identify missing generator vocabulary.

### 7.8 Cross-cutting fixes require semantic sibling enumeration

One dispatch and invalid-state hardening pass found generators by a familiar
source pattern and missed the structurally different local-pressure
generator. An early return also skipped zeroing an additional RHS column.

Before a cross-cutting repair, enumerate siblings by responsibility—every
component that emits `SUBROUTINE UEL`, every state-commit path, every output
bridge—not only by matching the first implementation's syntax. For an early
return, enumerate every output obligation in the code it bypasses.

### 7.9 Validated decks outrank remembered solver conventions

Abaqus field activation, procedure flags, `LFLAGS`, initialization calls, and
dummy elements contain conventions that are easy to remember incorrectly. If
the project has already run a validated case, start from that deck and log.
When one misconception appears in code, search the manuscript and other decks
for the same belief.

### 7.10 Scientific lineage and artifact licensing are different obligations

Scientific lineage matters whether a project uses published equations,
studies a reference implementation, or incorporates an external artifact.
Those relationships are not interchangeable. When prior work is used only as
a publication or reference implementation, record the citation and that
limited role. A separate license and redistribution review is needed when
third-party artifacts or derivatives are incorporated into, modified for, or
distributed with project artifacts.

Credit is not a ceremonial paragraph added after the technical work. It
records where interface conventions, formulations, deck topology, comparison
data, or tangent oracles came from. Artifact provenance additionally identifies
which exact third-party materials, if any, entered a benchmark or release.

---

## 8. Human–AI collaboration after agents could execute the work

The old case study described a chat-assistant workflow in which the AI could
not compile or run code. That statement was true only of the early interaction
mode. By late spring, the project workflow used compilers, direct test
harnesses, cluster execution, ODB extraction, example porting, and
cross-review. Dated records identify agents that built or reviewed many of
these artifacts, but they do not preserve the operator of every run command.

The roles became more useful when they were separated:

- **architecture and formulation:** select fields, stress measures, local
  variables, state contracts, and supported balances;
- **implementation:** extend the translator, generator, helpers, decks, and
  examples;
- **execution:** compile the emitted source and run the intended calling path;
- **falsification:** identify a distinct failure mechanism and build a gate
  that rejects a known-broken control;
- **integration:** propagate accepted changes through source, generated
  artifacts, figures, documentation, and release files; and
- **scientific ownership:** decide what the evidence establishes and what may
  be published.

Named project records illustrate this rotation. Kimi implemented and reviewed
bounded example work and later audited a broad example set. Claude/Fable
designed validation gates, reviewed constitutive and generator paths, and
integrated manuscript and release work. Codex reviewed code and evidence,
implemented or audited several repairs, and also produced an overbroad
manuscript edit that the author and Fable later corrected. GLM completed
bounded code-generation and review handoffs. DeepSeek, Gemini, Qwen, and other
systems supplied reviews or discussions at recorded stages.

These observations do not rank the models. The important pattern is that an
agent's name does not make a check independent, and a confident review does
not authorize an editorial or scientific decision. Useful disagreements ended
in source inspection or executable tests.

Teng's highest-leverage contributions remained scientific and programmatic:

- choosing which formulations and interfaces were worth supporting;
- supplying prior mechanics knowledge and Abaqus experience;
- selecting or rejecting validation oracles;
- refusing to equate visual plausibility or solver completion with
  reproduction;
- distinguishing the full research project from the manuscript and public
  subset;
- deciding what level of evidence was adequate for each claim; and
- retaining responsibility for credit, release, and publication.

That is not a fixed “human thinks, AI codes” boundary. Agents contributed to
formulation, review, execution, and evidence. The durable boundary was
authority and accountability.

---

## 9. Review, authorial authority, and the danger of over-correction

A referee-style AI manuscript review during the internal revision process—not
journal peer review—led to valuable tests and clarifications. The black-box
condensed-tangent test is the strongest example: a repeated concern was
converted into a decisive artifact. Other comments correctly prompted clearer
evidence levels, clearer disclosure and control of the remaining corrosion
deck and implementation differences, and better separation of manuscript
detail from repository detail.

The review also had only a partial view of the project. It saw the manuscript
and a release-facing subset, not the full lab, the larger example portfolio,
or the author's intended framing. During one revision pass, Codex treated
reviewer suggestions as instructions:

- the paper title was changed without author authorization;
- the Discussion and conclusion were shortened into audit-like prose;
- a static capability table made the paper examples look like the package
  boundary;
- repository commands and release logistics were moved into the Supplement;
  and
- provenance caveats were repeated until they displaced the scientific
  narrative.

The author rejected those changes. Fable restored the paper's title and
scientific discussion, removed the capability table and repository sections,
and retained the factual corrections that survived evidence review. A
different table comparing evidence tiers remained in the Supplement; it was
not the removed capability inventory. The episode produced several durable
editorial rules:

1. A reviewer comment is a hypothesis or recommendation, not an author
   decision.
2. Full project knowledge must be used to evaluate a reviewer's partial view.
3. Project capability, manuscript evidence, and public-release contents must
   remain separate.
4. Factual corrections can be made directly; title, framing, scientific
   emphasis, and major structure require author authority.
5. Scientific prose should lead with mechanism, result, and meaning. Job
   counts, forensic history, paths, hashes, and open release checks belong in
   repository records unless they are themselves scientific evidence.
6. A clean LaTeX build proves technical integrity, not authorial approval.
7. Before broad edits in a shared dirty tree, preserve an exact snapshot.

This failure belongs in the case study because it is the documentation analog
of a common-mode numerical test. Evidence control can still distort a project
if the controlling question is wrong. The purpose of review is to improve the
author's scientific claim, not to transfer authorship of the project's scope
to the reviewer.

---

## 10. Scientific lineage and credit

The following ledger records the principal external sources that materially
shaped the architecture or validation discussed here. Studying or citing an
implementation does not mean that its source was copied into `abaqus_ufl`.
The final column states the actual artifact relationship. For this
public-release ledger, detailed redistribution records are relevant when
third-party material or a derivative is included in the public repository.
This is not an exhaustive bibliography of every private example.

| Source or contributor | How it informed this project | Relationship to `abaqus_ufl` artifacts |
|---|---|---|
| FEniCS/UFL and its authors | Inspired the declarative interface and code-generation model | No UFL dependency or UFL source code; `abaqus_ufl` is UFL-inspired but not UFL-compatible |
| Shawn A. Chester; Claudio V. Di Leo; Lallit Anand | Gel theory and supplemental UEL/decks studied as scientific and finite-element references, including the local volume-fraction solve, volumetric treatment, and Abaqus output patterns | Their original UEL and decks are not included. The bilayer uses a project-written deck and generated UEL; its mesh discretization follows their supplemental example, with attribution |
| Shawn A. Chester | Historical UMAT studied for Abaqus state-variable, initialization, and time-step-control conventions | The original UMAT file is not included |
| Bibekananda Datta; Thao D. Nguyen | Published modular hydrogel UEL studied when comparing total-Lagrangian assembly based on second Piola–Kirchhoff (PK2) versus first Piola–Kirchhoff (PK1) stress, centroid F-bar treatment, local volume-fraction solvers, and modular code organization | The `abaqus_ufl` generator and generated Fortran were written separately; no Datta–Nguyen source code, input deck, or documentation is included |
| Allan F. Bower, Brown University | EN234_FEA was extended internally into the `feacheap` execution host used to test Abaqus-compatible subroutines outside Abaqus | Neither `feacheap` nor EN234_FEA is included in the public repository |
| Chuanjie Cui; Rujin Ma; Emilio Martínez-Pañeda | Published formulation, reference UEL, and deck used for the code-to-code corrosion comparison | Contains the project's generated UEL, reduced comparison results, and a comparison deck whose mesh derives from the reference distribution; the original UEL and deck are not included |
| Guglielmo Scovazzi; Rubén Zorrilla; Riccardo Rossi | Published stabilized formulation and block-compression benchmark reimplemented by the project | Contains project-written declarations, deck-generation tools, generated UEL, and results; no source files from the authors |
| Ye Tao, Teng Zhang, and coauthors | Prior coauthored pressure-based gel formulation, grooved-sheet geometry, and solvent-exposure setting used for the morphing example | The declaration and generated UEL are project work, and the Abaqus deck is this group's own prior work; no external implementation is included |

The relevant stable publications and repositories include:

- Chester, Di Leo, and Anand,
  [coupled diffusion–deformation finite-element implementation](https://doi.org/10.1016/j.ijsolstr.2014.08.015);
- Datta and Nguyen,
  [Abaqus UEL hydrogel implementation](https://doi.org/10.5281/zenodo.15725220);
- Cui, Ma, and Martínez-Pañeda,
  [dissolution-driven stress-corrosion formulation](https://doi.org/10.1016/j.jmps.2020.104254);
- Alnæs and coauthors,
  [Unified Form Language](https://doi.org/10.1145/2566630).

Credit also belongs to the discussions that shaped the project. Teng records
in the manuscript acknowledgements the influence of Lallit Anand at MIT on
multiphysics modeling and simulation; Allan Bower at Brown University through
his computational solid and structural mechanics course and shared
`feacheap`/EN234_FEA code; and Kenichi Soga and Yaobin Yang at the University
of California, Berkeley. The project also builds on Teng's earlier gel and
morphing research with Lining Yao's Morphing Matter Lab.

Attribution should state how prior work informed the project. If a future
public example copies, modifies, or distributes a third-party artifact, its
README should also record the exact source, version or hash, license, and
modifications. When only a published formulation or an implementation idea was
studied, state that plainly without implying source-code reuse.

---

## 11. Audited July 28 snapshot

For the audit snapshot used by this case study:

- the private lab revision was `56a6420`;
- the public revision was `a1b5825`;
- the public suite produced `125 passed` under `pytest -q`;
- public generation targets were UMAT and UEL;
- the public examples were a curated allowlist, not the full research
  inventory;
- the Cui-derived comparison mesh still required its precise BSD notice and
  redistribution status to accompany an archival release;
- the manuscript examples spanned quantitative reproduction, element-level
  verification, and execution demonstrations rather than one uniform evidence
  tier;
- the local-pressure condensed tangent had a compiled black-box,
  pressure-resolved finite-difference check with a frozen-Schur negative
  control;
- the four public paper packages were not yet clean-archive reproduction
  workflows: figure paths, corrosion inputs, the external mesh-seed input
  needed to rerun the bilayer builder, and morphing run instructions still
  required repair, and the release suite did not exercise those packages; and
- no public tag or archive DOI was visible in the local public checkout, while
  the citation metadata still marked those fields as pending.

These statements are deliberately revision-specific. The project is active.
The correct future status belongs in release notes and example READMEs, not in
a journal table or a timeless case-study claim.

Several scientific limitations also remain. A code-to-code benchmark verifies
implementation agreement within shared modeling assumptions; it is not an
experiment. Execution demonstrations do not establish stability or accuracy
over every mesh, material ratio, or loading path. Complex-step tangents require
analytic active paths and explicit history semantics. Scaling remains part of
the user's coupled nonlinear problem. Abaqus procedure setup, mesh, contact,
loading, solver control, and physical validation are not generated
automatically.

---

## 12. Summary

The first `abaqus_ufl` achievement was architectural: a mechanics researcher
and AI connected a declarative Python workflow to self-contained Abaqus
Fortran. The original case study documented that insight well.

The larger achievement came later:

```text
architecture
  → generated source
  → compiled calls
  → failure-specific element gates
  → solver and output audits
  → benchmark evidence
  → curated release
```

The post-May campaign showed that every transformation creates a new error
surface. Wrong equations can survive differentiation and compilation. State
ordering can fail only with multiple histories. A nonsymmetric tangent can be
transposed at a language boundary. A solver can stop while one field remains
under-resolved. A completed Abaqus run can carry a defective boundary set or
an incomplete output bridge. A correct lab result can become unreproducible
when its exact source, deck, or raw data is absent from the release.

That is why examples became verification instruments rather than showcases.
Their purpose was to exercise different failure mechanisms and reveal missing
declaration primitives, solver contracts, and provenance edges. Under the
later validation policy, a new example strengthened the verified-benchmark
tier only when it brought a distinct oracle or discriminator; other examples
could remain explicitly labeled execution demonstrations.

The collaboration model changed at the same time. The work no longer consisted
only of an agent suggesting code for a human to run; it included agent
contributions to implementation, example porting, falsification, evidence
review, and integration around compiled and executed artifacts. This made role
separation and authorial authority more important, not less. The human owner
still governed the research program, evidence threshold, scientific meaning,
credit, and release.

The durable lesson is concise:

> For generated scientific software, validate every transformation, preserve
> the exact artifact that supports the claim, and never let a curated example
> set or a reviewer's partial view redefine the full research program.

---

## 13. Evidence record

### Public records

- [`abaqus_ufl` public repository at
  `a1b5825`](https://github.com/tengzhang48/abaqus_ufl/tree/a1b58257763215ce3e151e0ca00d774d38dd4abf),
  the July 28 snapshot used for the public-package audit;
- the public repository's `README.md`, `CITATION.cff`, `examples/README.md`,
  `HOWTO_ADD_AN_EXAMPLE.md`, and paper-example READMEs;
- the historical case-study draft, preserved outside this repository as the
  early-phase account from which Sections 3–4 were reconstructed; and
- [this repository's current agent-era guide](../guides/lessons_human_ai_research_agent_era.md).

### Private research-workspace records named for provenance

- `abaqus_validation/VALIDATION_RUN_LOG.md` — compiled and Abaqus validation
  chronology, including later reclassification of stale evidence;
- `WORK_SUMMARY_2026-06-12.md`, `BUG_AUDIT_2026-06-10.md`, and
  `CLAUDE_WORK_REVIEW_2026-06-12.md` — package defects, MRE oracle, and
  cross-review record;
- `abaqus_ufl/testing/README.md` and `docs/lessons_learned.md` — validation
  gate definitions and incident-based lessons;
- the Cui run audit and UVARM handoff under
  `examples/phasefield_corrosion_cui/abaqus_test_from_cui/`;
- the mixed-order boundary audit under
  `examples/gel_chester_anand/u_p_mu_quad8/`;
- `tests/test_local_pressure_condensed_tangent.py` and the manuscript
  Supplement — compiled condensed-tangent test and reported errors;
- `RELEASE_PLAN_2026-07-21.md` — positive-allowlist, privacy, lineage, and
  licensing rationale for the public split; and
- `EML_paper/CODEX_LESSONS_FROM_OVEREDITING_2026-07-28.md` plus Fable's
  restoration record — manuscript authority and over-editing episode.

### Source hierarchy

For numerical claims, exact submitted source, input, log, raw output, and
comparison script outrank a later prose summary. For release claims, the
public revision and a clean checkout outrank the private lab. For historical
collaboration claims, dated signed notes and commits outrank model memory.
Public release contents do not define the full project's capability, and test
counts do not define the strength of a scientific claim.

- **Version:** 2.0
- **Last updated:** 28 July 2026
- **Evidence window:** March–July 2026
- **Research framing and responsibility:** Teng Zhang
- **Evidence audit and rewrite:** Codex (GPT), 28 July 2026
- **Factual and public-boundary review:** Fable (Claude), 28 July 2026
