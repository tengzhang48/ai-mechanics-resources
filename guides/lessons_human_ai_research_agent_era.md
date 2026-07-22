# Human–AI Research in the Agent Era

**From division of labor to division of authority**

This is a July 2026 companion to the [March–April 2026 field
guide](lessons_human_ai_research.md). The earlier guide records a chat-assistant
period in which the human usually supplied the plan, ran the code, pasted the
error, and decided when the AI had become stuck. That record remains useful.
It no longer describes the full collaboration observed in the two most recent
projects.

This guide is based principally on one human–multi-agent computational
mechanics program. It distinguishes four kinds of statement:

- **observations** documented in the project record;
- **author reflections** about how the work changed the human researcher's
  role;
- **working hypotheses** that have not yet been demonstrated by these
  projects; and
- **proposed practices** inferred from the evidence.

Model names are historical coordinates, not permanent capability rankings.
The evidence is what each participant actually contributed to a particular
artifact and what survived verification.

---

## Contents

1. [Technical summary](#1-technical-summary)
2. [The collaboration model changed](#2-the-collaboration-model-changed)
3. [Capability is shared; authority is assigned](#3-capability-is-shared-authority-is-assigned)
4. [Research taste constructs a program](#4-research-taste-constructs-a-program)
5. [Agents expanded the mathematics we could pursue](#5-agents-expanded-the-mathematics-we-could-pursue)
6. [From a known answer to a verified discovery engine](#6-from-a-known-answer-to-a-verified-discovery-engine)
7. [What must converge when the answer is unknown](#7-what-must-converge-when-the-answer-is-unknown)
8. [Independent evidence is not a model vote](#8-independent-evidence-is-not-a-model-vote)
9. [Verification and validation are different](#9-verification-and-validation-are-different)
10. [From fear to evidence-governed trust](#10-from-fear-to-evidence-governed-trust)
11. [Question validity comes before answer validity](#11-question-validity-comes-before-answer-validity)
12. [An operating model for agent-era research](#12-an-operating-model-for-agent-era-research)
13. [What remains uncertain](#13-what-remains-uncertain)
14. [Practical questions before accepting a result](#14-practical-questions-before-accepting-a-result)
15. [Conclusion](#15-conclusion)

---

## 1. Technical summary

The old division—human thinks, AI codes, human checks—is no longer an adequate
description of this work. In the nonlinear wrinkle and crack-tip projects,
agents proposed and repaired mathematical architectures, derived higher-order
fields, implemented solvers, ran numerical campaigns, designed convergence
tests, challenged other agents, withdrew provisional claims, and assembled
publication evidence. In several local tasks, the agents' mathematics and
coding exceeded what the human researcher would probably have selected or
implemented unaided.

The durable distinction is therefore not an assumed boundary between human
and AI capability. It is a division of **authority, evidence, and
accountability**. Humans and agents may contribute at every technical level.
The human scientific owner chooses and sustains the research program, accepts
the governing assumptions and method boundary, decides what evidence is
adequate for a claim, interprets the result physically, and remains responsible
for release and publication.

This does not reduce the human role to project management. Choosing to pursue
a reusable nonlinear symplectic framework when a conventional method could
answer one immediate problem is itself a scientific contribution. It expresses
research taste: a judgment about which structure is worth developing across a
family of problems, which result is meaningful, and which open direction
deserves continued attention.

A known final answer is useful but not required for trustworthy discovery.
Mathematics and mechanics can provide a different foundation: governing
equations, variational or Hamiltonian structure, exact symmetries, limiting
solutions, branch identities, independently checked derivatives, and exposed
refinement of each approximation axis material to the stated claim. When the
chain is controlled and its remaining sensitivities are reported, a framework
can generate a credible answer that no participant knew beforehand. The
period-four wrinkle calculation and the higher-order crack-tip construction
are examples at their explicitly stated evidence levels.

Convergence alone is not enough. A calculation can converge to the wrong
model, a substituted method, an incomplete basis, or the wrong bifurcation
branch. Verification must attach convergence to method identity, appropriate
residuals, conditioning, branch classification, error scale, and provenance.
Validation then asks a different question: whether the verified model
describes physical reality. For claims about physical reality, experiments or
observations are indispensable, but the current record does not yet contain a
complete human–agent experimental research case.

Finally, increasingly capable execution may move some risk upstream. A
misleading or scientifically unimportant question can receive a coherent and
well-converged answer. This is a **working hypothesis**, not yet an observed
failure in these projects. Question formulation should itself become a
human–agent activity, with a separate challenge to the premise before a large
technical campaign begins.

---

## 2. The collaboration model changed

The March guide described a productive workflow for the tools available at the
time:

```text
human specifies → AI proposes → human runs → human returns error
    → AI repairs → human validates
```

The newer projects used agents with direct access to repositories, command
execution, persistent work products, and other agents. The observed loop was
closer to:

```text
research program and question
    → method and evidence contract
    → agent derivation, implementation, and execution
    → independent source/physics/artifact review
    → correction, rerun, and claim propagation
    → human acceptance, scoping, or rejection
```

This is not merely faster code generation. The role assignments in the
crack-tip project rotated: Fable initially served as revision executor and
infrastructure builder, while Codex served as structural reviewer; later,
Codex led several derivation rounds and Fable became the adversarial verifier
and shipping executor. The invariant was not the model assigned to each role.
It was that the deriver did not sign off alone
([crack-tip case, §15](../case_studies/symplectic_mooney_rivlin_crack_tip.md#15-the-multi-ai-review-loop)).

The wrinkle project went further operationally. Agents ran calculations,
edited files, maintained handoffs, made or inspected commits, archived
superseded modules, and dispositioned reviews. This accelerated the work and
created new failure surfaces: remembered paths differed from the live
workspace; a test guarded a corrected copy while a broken copy still shipped;
and detailed agent-to-agent notes failed to give the human owner a concise
method-boundary update
([wrinkle case, §13](../case_studies/symplectic_wrinkle_period_doubling.md#13-agent-autonomy-made-provenance-and-communication-scientific-requirements)).

The agent era therefore changes both productivity and epistemic risk. More
autonomy makes repository state, authorization, method identity, and artifact
lineage part of the scientific method rather than clerical support.

### 2.1 Why conversation remains a powerful research interface

The transition from chat assistant to workspace agent does not make
conversation obsolete. Dialogue is a low-friction steering interface between
participants with different roles and authority. A human can intervene when
a calculation becomes physically unconvincing, a method crosses an intended
boundary, or an apparently successful number feels too easy. The intervention
does not need to arrive as a complete alternative derivation. It can begin as
“that is not the method I asked for,” “this residual is being interpreted
incorrectly,” or “the agreement may be accidental.” An agent can then turn
that constraint or discomfort into a source trace, derivation, discriminating
test, refinement ladder, or revised claim.

Conversation also externalizes part of the reasoning that would otherwise
remain tacit. The human can state physical taste, priorities, forbidden
substitutions, and stopping judgments; the agent can expose assumptions,
propose consequences, and report what the live calculation does. Repeated
challenge and response, when written into durable project records, can
preserve why a route was accepted, demoted, or withdrawn. In the two case
studies, this record mattered because several decisive corrections began
neither as a theorem nor as a bug report, but as a short objection that was
subsequently converted into an auditable artifact. This is an observed benefit
of the interface in this program, not evidence that every long conversation
improves research.

The wrinkle residual discussion gives a precise example. The selected finite
state is a stationary point of the unexpanded energy **against the retained
Ritz test space**. That is the equilibrium equation the method actually
solves. It is not a claim that the corresponding first Piola stress has zero
pointwise divergence or that every boundary traction is already exact. Stress,
`Div P`, and traction fields are derived from the retained displacement field
and remain valuable strong-form diagnostics. After implementation, convention,
quadrature, and boundary-condition errors have been excluded, their spatial
spectra can show where the retained representation lacks resolution. They are
not, however, independent solution variables or the Newton residual of this
global variational method.

This distinction prevents a second numerical overreach. A reported
strong-residual ratio of, for example, 0.22 is not by itself a 22% error bar on
a bifurcation threshold. No such conversion follows without an error estimate
linking that residual norm, the omitted approximation directions, the parent
state, and the stability eigenvalue. In this calculation, threshold sensitivity
was therefore assessed through matched enrichment of the parent and
perturbation spaces, mode tracking, and movement of the neutral crossing. The
strong diagnostics still matter: large or structured values limit any claim
of pointwise continuum equilibrium and, after other error sources are
excluded, identify where further enrichment is needed. The defensible
statement is therefore neither “stationarity proves the continuum solution”
nor “a 22% strong residual makes the threshold 22% wrong.”
It is that the state is stationary in a named retained space, with separately
reported strong-form limitations and observable-specific convergence evidence
([wrinkle case, §6](../case_studies/symplectic_wrinkle_period_doubling.md#6-independent-audit-and-retained-space-closure)
and [§11](../case_studies/symplectic_wrinkle_period_doubling.md#11-coupled-approximations-must-be-closed-together)).

The chat transcript is not the warrant for any of those statements.
Conversational fluency, apparent memory, confidence, persistence, and agreement
between a human and an agent are not scientific evidence. Memory can preserve
an obsolete path; agreement can preserve a shared error; and a persuasive
explanation can describe code that never ran. Dialogue becomes effective for
research when it is coupled to live workspace access, executable derivations
and tests, explicit method and evidence contracts, provenance, appropriate
convergence studies, and a claims ledger that survives beyond the session.
The human scientific owner retains publication authority and responsibility.
Conversation supplies unusually responsive steering and a challenge-response
record; the scientific warrant comes from the evidence graph it helps create.

---

## 3. Capability is shared; authority is assigned

The old binary table reserved research questions, error identification,
validation, and pivots for humans, while assigning plans and code to AI. The
new cases contradict that capability boundary. Agents identified method
substitution, discovered errors between individually correct equations,
designed exact and numerical falsification routes, derived new mathematical
responses, and retracted their own provisional results. Humans also continued
to contribute technical constraints and physics corrections.

A more durable allocation is:

| Research activity | Who may contribute | What confers authority |
|---|---|---|
| Propose questions and mechanisms | Human and agents | Explicit assumptions, relevance to the research program, and human acceptance |
| Choose a long-horizon program | Human and agents may argue for alternatives | Human commitment of attention, resources, and publication responsibility |
| Select a mathematical formulation | Human or agents | Derivation, applicability, method contract, and discriminating checks |
| Derive mathematics | Human or agents | Independent algebraic, structural, dimensional, and numerical evidence |
| Implement and execute | Human or agents | Scoped authorization, live-state checks, tests, and reproducible artifacts |
| Challenge and verify | Human or agents | A route capable of falsifying the claim without sharing its decisive failure mode |
| Select manuscript claims | Human with agent analysis | A closed evidence path and explicit treatment of open dependencies |
| Release or submit | Agents may prepare the package | Human author accepts responsibility |

This is a division of authority, not a claim that humans alone possess taste or
that agents alone possess technical power. Agents can propose broad research
directions. Humans can perform deep derivations. The point is that contribution
and acceptance are different acts.

The wrinkle project made this distinction concrete by assigning computational
routes the statuses

```text
paper method | referee | diagnostic | oracle | superseded
```

These labels described authority, not quality. A strong depth-FE oracle could
answer a numerical question and still be ineligible to support a manuscript
claim about a no-depth-node analytical method. Conversely, the selected paper
method needed that oracle because its errors differed
([wrinkle case, §8](../case_studies/symplectic_wrinkle_period_doubling.md#8-exploratory-freedom-and-publication-eligibility-are-different)).

Attribution should follow the same layered logic. Useful categories include
scientific owner, method architect, derivation lead, implementation executor,
falsifier, convergence contributor, and release integrator. A filename or the
agent occupying a session does not establish authorship. The wrinkle record,
for example, does not identify the original author of the inherited depth-FE
solver; it does establish Fable's later analytical-depth architecture and
rebuild
([wrinkle case, §15](../case_studies/symplectic_wrinkle_period_doubling.md#15-attribution-and-the-multi-ai-review-loop)).

---

## 4. Research taste constructs a program

Research taste is sometimes described as the ability to select an elegant
problem. In agent-era work it has a broader meaning:

- choosing a phenomenon worth sustained attention;
- distinguishing an immediate calculation from a long-horizon research
  program;
- deciding which mathematical structure is worth preserving across problems;
- recognizing when a more accurate number answers the wrong methodological
  question;
- deciding what belongs in the current paper and what should remain an open
  program; and
- interpreting why the result matters physically.

The wrinkle project provides the clearest example. A Fourier × depth-FE route
could estimate the period-doubling strain. Teng's larger objective was to
extend a 2017 Hamiltonian–Stroh onset theory into a finite-amplitude nonlinear
framework and use period doubling as the first secondary bifurcation. A
numerically useful threshold did not complete that objective if it came from a
different through-depth method
([wrinkle case, §§1 and 4](../case_studies/symplectic_wrinkle_period_doubling.md#1-the-problem-stability-about-a-finite-amplitude-wrinkle)).

This was not a claim that symplectic methods are universally superior. A
non-symplectic method may be the most efficient way to solve a particular
problem. The research choice was to ask a different, longer question:

> Can a reusable symplectic framework organize and compute a wider family of
> nonlinear bifurcations?

> **Author reflection (edited for clarity).** I know that a non-symplectic
> method can solve the immediate wrinkle problem. I still choose to explore
> the symplectic route because I want to learn whether it can become a coherent
> framework for a wider range of nonlinear bifurcations. That long-horizon
> choice is part of my scientific contribution.

That is presently a research-program hypothesis, not a conclusion already
proved across nonlinear mechanics. Its first demonstrated reach is narrower:
the framework was developed through period doubling and then extended into a
retained-space period-four calculation. Each new class of problem will create
new constitutive, boundary, symmetry, branch, and validation obligations.

Human research taste appeared similarly in the crack-tip project through the
distinction between **program and result**. The general constrained symplectic
operator remained an important program, but the manuscript could establish a
smaller leading result without claiming the unfinished operator. Teng chose
the stopping line and preferred a weaker supported statement to a more
impressive unsupported one
([crack-tip case, §18](../case_studies/symplectic_mooney_rivlin_crack_tip.md#18-the-humans-critical-contributions)).

Research taste is therefore not simply “having the big picture.” It is choosing
and sustaining a scientific direction under uncertainty, including the right
to reject an expedient answer that does not advance the intended program.

---

## 5. Agents expanded the mathematics we could pursue

The most consequential change in the new projects is that agents did not
merely accelerate mathematics the human had already selected. They developed
constructions that the human researcher reports he would have been unlikely to
choose or implement alone.

> **Author reflection (edited for clarity).** The Gram construction in the
> wrinkle project and the higher-order crack-tip mathematics went beyond
> methods I would probably have selected and implemented alone. I do not see
> that as a reason to reject them. I see it as a reason to require explicit
> mechanics, independent checks, convergence evidence, and honest scope before
> I accept them.

### 5.1 The wrinkle stability instrument

Fable's analytical-depth state used global coefficients multiplying explicit
Hamiltonian–Stroh depth functions and product-rate enrichments; it did not use
nodal displacement values through depth. The coefficients came from stationarity
of the unexpanded finite-strain energy
([wrinkle case, §5](../case_studies/symplectic_wrinkle_period_doubling.md#5-fables-analytical-depth-turnaround)).

The difficult work was not just building that solver. The first stability
basis saturated under an ordinary mass-norm Gram reduction. Fable changed the
conditioning metric to a gradient/energy seminorm, reported retained rank, and
tested whether small Gram directions were roundoff or physical span. The soft
mode occupied combinations of nearly degenerate exponentials in that Gram
tail. Deleting them because their eigenvalues looked small would have deleted
the physical mode
([wrinkle case, §5](../case_studies/symplectic_wrinkle_period_doubling.md#5-fables-analytical-depth-turnaround)).

The Gram reduction was a crucial conditioning and span-preservation component,
not the entire physical method and not evidence of a universally new algorithm.
Its importance here is what it reveals about contribution: the agent connected
the energy metric, confluent basis behavior, roundoff testing, and the physical
soft mode into a working numerical instrument.

Fable then replaced heuristic mode scores with a reflection-sector
construction anchored to the measured wrinkle crest. It withdrew thresholds
when the mode identity or parent-state ladder was inadequate and rebuilt the
convergence argument. Codex later identified a missing parent-state harmonic
axis, and the value was suspended again until that ladder was run
([wrinkle case, §5](../case_studies/symplectic_wrinkle_period_doubling.md#5-fables-analytical-depth-turnaround)).

### 5.2 The higher-order crack-tip construction

The crack-tip campaign also exceeded a code-assistance model. A generic
second-variation theorem initially seemed to justify a specific five-row
symplectic operator. Agent-led action-level analysis showed that the printed
in-plane momentum omitted reaction content. The opening block remained exact,
while the other rows were demoted to a useful spectral scaffold
([crack-tip case, §4](../case_studies/symplectic_mooney_rivlin_crack_tip.md#4-the-symplectic-promise-and-the-missing-operator)).

After Teng reassigned roles, Codex led several higher-order `Q_k` derivation
rounds and Fable served as adversarial verifier and shipping executor. The
surviving work includes specifically scoped constrained-action reactions,
canonical momenta, slaved openings, first-material-order blocks, and later
companions. It does **not** establish a closed infinite tower, the full
finite-compliance operator, normalized higher-parameter extraction integrals,
the finite-compliance axis-layer match, higher material orders, or the
generated `k + 3` rung
([crack-tip case, §5](../case_studies/symplectic_mooney_rivlin_crack_tip.md#5-where-the-defensible-scope-now-stops)
and [§19](../case_studies/symplectic_mooney_rivlin_crack_tip.md#19-attribution-carefully)).

The leading crack-tip field is itself a reduced plane-stress asymptotic with an
overlap regime. It is not a description of the sub-thickness three-dimensional
tip.

This combination—advanced agent contribution and strict limitation of its
claim—is central. Technical reach is not self-validation. The higher-order
work became admissible only after action, constraint, traction, amplitude,
endpoint, and independent differentiation gates were applied.

### 5.3 Beyond narrow task execution

The record also contains agents doing things the old guide described as
human-only: questioning a route, detecting a method boundary, retracting a
provisional conclusion, building a replacement framework, and connecting a
local defect to a larger verification architecture. This does not prove that
every agent maintains research taste or a coherent long-horizon program. It
does show that “AI can only execute the task it was given” is no longer a safe
universal assumption.

The human role should not be defended by understating the agent. It should be
defined by the authority and responsibility the research actually requires.

---

## 6. From a known answer to a verified discovery engine

The phrase *ground truth* often collapses several distinct ideas. At least
three truth anchors matter in computational mechanics:

1. **Known-answer reference.** A value, field, or theorem is available for
   comparison, preferably withheld from the builder when used as a benchmark.
2. **Model-conditional mathematical and structural constraints.** The final
   answer is unknown, but the selected governing equations, variational
   structure, boundary conditions, symmetries, exact limits, identities, and
   approximation route provide falsifiable constraints. Whether that selected
   model is physically adequate remains a validation question.
3. **Empirical truth.** Experiment or observation tests whether the model and
   its verified solution describe the physical system.

The first is powerful but not necessary for discovery. Mathematics and
mechanics can make a previously unknown result trustworthy by decomposing it
into auditable steps. The trusted object is not a target decimal known in
advance; it is the chain from governing assumptions to a converged claim.

The wrinkle project illustrates the transition. Known or strong-reference
checks were used while the method was being established: independent finite
differences checked derivatives; the flat state supplied a dense
one-dimensional referee; the two reflection sectors had to recompose the
unprojected spectrum; and exact carrier lifting into a daughter cell had to
preserve the parent eigenvalue and field. Agreement with a lattice or a broader
experimental/FEM window was not accepted by itself.

The resulting framework was then used beyond the original period-doubling
target. A verified retained-space parent and neutral-mode construction were
lifted into a period-four cell through an exact carrier map. A physical
amplitude constraint crossed the local branch, the constraint was released,
and stationarity, symmetry, and coupled parent/stability refinements were
checked
([wrinkle case, §§6 and 11](../case_studies/symplectic_wrinkle_period_doubling.md#6-independent-audit-and-retained-space-closure)).
The period-four result retained a substantial strong residual and was not
called a pointwise-converged continuum solution. Its threshold also inherits
the substantial strong-residual limitation of the doubled parent branch. It is
evidence of verified discovery at a stated retained-space level, not unlimited
certification.

The higher-order crack-tip constructions provide another route. They were not
verified in this project by comparison with a previously tabulated final
family. At their distinct stated scopes, they were constrained by the action,
exact constraint, equilibrium and total-traction rows, dimensional scaling,
endpoint class, stable integration direction, and direct differentiation of
the relevant action stress. Some attractive claims failed those checks and
were removed. The surviving constructions are results of this project within
the formal leading constrained action or stated first-material-order block;
their literature novelty and physical excitation are separate questions.

The practical conclusion is:

> A previously unknown answer can be scientifically credible when it is
> produced inside a verified framework whose model assumptions are explicit
> and whose derivation, method identity, implementation, approximation errors,
> branch identity, and claim scope are controlled.

Once established, such a framework becomes a **verified discovery engine**.
It can be applied to problems without known answers, but it does not transfer
its credibility automatically. Every new problem must reopen the gates affected
by its material law, geometry, boundary conditions, spectrum, and observable.

---

## 7. What must converge when the answer is unknown

“Every step converges” is a strong principle only after the steps and their
targets are named. In nonlinear bifurcation research, the relevant chain is:

```text
physical phenomenon
  → research question
  → governing model and boundary conditions
  → mathematical derivation
  → claimed numerical method
  → executed assembly or call path
  → approximation spaces and conditioning
  → mode and branch identity
  → numerical artifact and error budget
  → scientific interpretation
  → comparison with physical reality
```

A smooth ladder near the end cannot repair a substitution near the beginning.
The wrinkle depth-FE route could converge numerically while remaining the
wrong authority for a no-depth-node method claim. A Hamiltonian or Hermitian
operator could pass its structural identities while omitting a dressed Fourier
channel. A lowest unclassified eigenvalue could belong to the wrong physical
branch or reflection class. A stable perturbation ladder could be paired with
an under-resolved parent state.

For an unknown bifurcation result, the verification plan should address at
least the following.

### Model and derivation

- Are material assumptions, kinematics, constraints, and boundary conditions
  explicit?
- Do dimensions, signs, gauges, symmetries, and exact limiting cases agree?
- Is a general theorem actually derived for the concrete reduced system, or
  merely invoked by analogy?

### Method identity

- What are the unknowns?
- What basis multiplies them?
- What is assembled and differentiated?
- Which conditions are exact, weak, penalized, or sampled?
- Does the executed generator implement the method named in the paper?

### Approximation and conditioning

- Which axes are truncated: harmonics, depth functions, product rates,
  quadrature, domain size, precision, continuation step, or mesh?
- Are retained rank and discarded directions reported?
- Is the instrument's absolute error smaller than the residual or eigenvalue
  change that determines the claimed crossing?
- Are coupled spaces refined at matched levels?

### Physical identity

- Is the tracked eigenmode in the correct symmetry sector?
- Is the branch local to the bifurcation or a distant lower-energy state?
- Is the residual notion appropriate to the method—for example, weak
  Rayleigh–Ritz stationarity rather than an incorrectly imposed collocation
  residual?
- If strong-form stress, divergence, or traction diagnostics are reported,
  have implementation and convention errors been excluded before they are
  interpreted as indicators of unresolved field content rather than direct
  percentage errors in an eigenvalue or bifurcation threshold?

### Artifact and claim

- Can the runner regenerate the artifact from the stated revision and
  configuration?
- Does the claims ledger identify the generator, evidence level, and open
  dependencies?
- Do figures and manuscript statements read the governing artifact rather than
  an old summary?

The wrinkle case shows why these axes must close jointly
([wrinkle case, §§9–11](../case_studies/symplectic_wrinkle_period_doubling.md#9-verification-must-resolve-the-scale-of-the-claimed-observable)).
The crack-tip case adds a different warning: individually correct equations
can still form a contradictory hierarchy, and a unit gauge can hide a missing
amplitude factor
([crack-tip case, §§6–7](../case_studies/symplectic_mooney_rivlin_crack_tip.md#6-correct-equations-can-still-form-a-contradictory-paper)).

Convergence is therefore neither a decorative plot nor an all-purpose proof.
It is a claim about a named mathematical object, approximation family, norm,
observable, and branch. Within that scope, it is what allows mechanics to move
beyond answers known in advance.

---

## 8. Independent evidence is not a model vote

Using several agents increased coverage in both projects, but agreement did not
establish truth. Different models may share the same source, equation, code,
fixed gauge, basis, or cultural assumption. Conversely, two routes produced by
the same model can be meaningfully independent when their decisive failure
modes differ.

Useful separations in these projects included:

- automatic differentiation versus finite differences;
- symbolic identities versus full numerical evaluation;
- exact flat-state or endpoint limits versus finite-amplitude computation;
- variational energy checks versus strong-form residual indicators;
- asymptotic predictions versus a separately discretized FEM specimen;
- a mechanism-removing material control versus another fit of the same case;
- source and call-path tracing versus manuscript-language review;
- fresh solver execution versus deterministic regeneration from curated data;
  and
- byte hashes versus semantic checks that the files support the stated claim.

The crack-tip workflow formalized four roles: deriver, verifier, executor, and
human meta-reviewer. Algebraic disagreements were converted into tests such as
varying an amplitude hidden by a unit gauge, differentiating the complete
nominal stress, running a material control, reconstructing endpoint series, and
decomposing the energy flux. The number of checks was explicitly not treated
as a number of independent proofs
([crack-tip case, §15](../case_studies/symplectic_mooney_rivlin_crack_tip.md#15-the-multi-ai-review-loop)).

The wrinkle project used a similar closure rule:

1. the builder named the method and its weakest points;
2. a reviewer traced the actual generator and tried to falsify a claim;
3. an executor changed the code and produced a new artifact;
4. the finding closed only when implementation, artifact, and physical
   interpretation agreed; and
5. Teng decided whether the result could enter the paper.

No reviewer was self-authenticating. Codex corrected an initial overbroad
criticism after tracing the real-valued production basis, while several
confident “ready” assessments preceded genuine source-level findings
([wrinkle case, §15](../case_studies/symplectic_wrinkle_period_doubling.md#15-attribution-and-the-multi-ai-review-loop)).

Late cross-review added the converse warning: a critical review finding is
also provisional until its evidence path is checked. A reported byte-hash
mismatch may prove only that an internal raw artifact and a sanitized release
artifact occupy different package roles. Sanitizing provenance-only fields can
legitimately change the hash without changing the configuration or numerical
payload. The research ledger and the public package's own claims
ledger/manifest should each hash the file they actually govern, the release
transformation should be documented, and semantic fields should be compared
explicitly. Paper-facing public ledgers should use repository-relative source
paths. Historical raw generation records may retain machine-local paths when
they are labeled as nonportable metadata rather than presented as public entry
points. A hash certifies byte identity inside a named package; it does not
certify scientific equivalence across a documented transformation.

Claims that evidence is absent require the same care. In the wrinkle
cross-review, intermediate strong-residual ratios described as unstored were
already present in tracked JSON under
`.states["0.24"].gate_report.strong_divp`. The stored `residual_l2` and
`gradient_l2` components also reproduced every `relative_l2` ratio exactly.
Before an absence claim changes a paper or starts a costly rerun, search the
schema and candidate paths, inspect neighboring fields, and recompute the
claimed quantity from stored components when possible.

Reviewer identity is provenance too. Record the model or person named in the
artifact header or verified execution metadata; do not infer authorship from
which reviewer was expected, from a filename, or from surrounding chat. If
identity cannot be reconciled, label it unknown. Conversational multi-agent
review is powerful because it generates competing hypotheses rapidly and
lets one participant test another's assumptions. It remains non-self-
certifying: the reviewer, attribution, hash interpretation, and absence claim
all pass through the same validation circuit as the scientific result.

The final wrinkle-paper reviews supplied a particularly clear example. Several
agents focused on the same large strong-form ratio and implicitly mapped it
onto uncertainty in `T45`. Their agreement measured the salience of the table,
not several independent validations: they read the same diagnostic and shared
the same unstated premise. Artifact review preserved the valid conclusion
that continuum adequacy remained open, but separated it from the physical
observable. The retained `T45` is the compression at which the lowest
quarter-wavenumber Hessian eigenvalue of the doubled parent vanishes. The
strong ratio is an `L2`-normalized measure of the derived stress-divergence
imbalance over the represented domain. The review campaign therefore produced
a disposition by claim, premise, evidence path and action. Findings that share
a premise count as one hypothesis until a distinct test is supplied
([wrinkle case, §13](../case_studies/symplectic_wrinkle_period_doubling.md#final-ai-pre-submission-review-agreement-had-to-be-decomposed)).

The reviews strengthened the audit trail, but the organizing physics remained
the repeated subharmonic mechanism. Diagnostics govern the scope of a claim;
they should not replace the mechanism as the scientific narrative.

The useful unit of multi-agent review is therefore **a disagreement converted
into a falsifiable artifact**, not a vote.

---

## 9. Verification and validation are different

The terms are often mixed in informal AI discussions.

**Verification** asks whether the intended equations and method were derived,
implemented, and solved correctly at the claimed numerical accuracy.

**Validation** asks whether the mathematical model and its verified solution
adequately represent the physical phenomenon for the intended use.

Exact identities, convergence ladders, manufactured solutions, and independent
implementations can make a numerical result highly credible **within a model**.
They cannot by themselves establish that the material law, dimensional
reduction, boundary conditions, imperfections, or experimental observable
represent reality.

The crack-tip strip FEM is a strong independently discretized, within-model
check of the asymptotic crack-tip reduction: it does not impose the crack-tip
field, the remote loading fixes the amplitude without fitting, and a `c2 = 0`
control removes the proposed mechanism. The disk is correctly described as a
consistency cross-check rather than a second specimen-level check
([crack-tip case, §3](../case_studies/symplectic_mooney_rivlin_crack_tip.md#3-from-local-theory-to-parameter-free-tests)).
Both calculations solve the same reduced plane-stress material model. They do
not validate the constitutive law or dimensional reduction against laboratory
reality.

The wrinkle result is compared with a broader experimental/FEM interval and a
separate single-grid lattice discretization. Those comparisons matter, but
agreement with the interval was deliberately not used to define correctness.
The analytical route still had to establish method identity, mode identity,
and joint convergence.

For claims about physical reality, experiments or observations are essential
because they can falsify a modeling assumption that perfect numerical
convergence cannot see. They also introduce their own agent-era problems:
apparatus design, calibration, measurement uncertainty,
uncontrolled variables, image and signal processing, safety, data lineage, and
the distinction between exploratory and confirmatory analysis. The present
repository does not yet document enough human–agent experimental work to turn
those issues into an evidence-based guide. They should be treated in a
separate future document rather than filled with generic advice here.

For now, every computational claim should state its evidence level, for
example:

```text
algebraically checked
verified implementation
converged within the stated model and space
cross-checked by a distinct numerical route
experimentally validated for the stated regime
publication-eligible with named limitations
```

These states are not interchangeable.

---

## 10. From fear to evidence-governed trust

When an agent derives mathematics beyond the human collaborator's working
expertise, fear about correctness is reasonable. The wrong adaptation would be
either to reject every result the human cannot reproduce unaided or to accept
the result because the agent sounds confident and its plots are smooth.

> **Author reflection (edited for clarity).** I have felt this fear directly:
> how can I know an agent's result is correct when parts of the mathematics are
> beyond what I would have attempted myself? My answer is not blind trust, and
> it is not retreat. It is to make the verification structure stronger and the
> limits of every claim more visible.

Modern research already depends on epistemic delegation. Experimentalists,
analysts, numerical specialists, and instrument builders rarely reproduce
every part of one another's work. Trust is made responsible through methods,
records, calibration, replication, peer challenge, and bounded claims. Agent
collaboration needs a stronger version of the same institutional structure
because generation and revision are unusually fast.

The human researcher does not need to remain the strongest local mathematician
or programmer. The human does need enough understanding to govern:

- what physical question the calculation answers;
- which assumptions and boundaries define the model;
- what method is actually running;
- which evidence could falsify the central claim;
- which approximation and validation gaps remain;
- whether the result's importance exceeds its uncertainty; and
- what may responsibly be published.

This is **evidence-governed trust**. It replaces the expectation of complete
line-by-line personal mastery with a deliberately constructed evidence system.
It does not weaken the standard of proof.

An acceptable handoff for an advanced result should make the following visible
without reconstructing a long conversation:

- the governing claim and its status;
- the exact source revision and live execution route;
- the method identity and prohibited substitutions;
- the decisive tests and what each can falsify;
- the coupled convergence or error budget;
- independent comparisons and their shared dependencies;
- retracted or superseded alternatives;
- remaining open questions; and
- the artifact used by the figure or manuscript.

In the wrinkle project this became the directed chain

```text
runner → numerical artifact → claims ledger → figure/manuscript → manifest
```

([wrinkle case, §13](../case_studies/symplectic_wrinkle_period_doubling.md#13-agent-autonomy-made-provenance-and-communication-scientific-requirements)).
The chain allows a human to accept work beyond individual technical reach
without accepting an unauditable conclusion.

---

## 11. Question validity comes before answer validity

The following proposition is important but not yet established by a clean
project example:

> **Working hypothesis:** As agents become more reliable at solving specified
> technical tasks, a larger share of research risk may move upstream into
> problem formulation. A false premise, misleading proxy, incomplete physical
> question, or locally convenient objective may produce a coherent and
> converged answer to the wrong problem.

This remains a hypothesis because the work documented here has mostly stayed
inside problems the human researcher already knows well. The wrinkle project
is a near-example, not a complete demonstration: substantial effort could
improve a threshold while the governing research question—whether it came
from the requested analytical symplectic framework—remained unresolved.

A wrong or misleading question can take several forms:

- assuming the mechanism that should instead be tested;
- optimizing a proxy that is only weakly related to the phenomenon of
  interest;
- prescribing a method whose approximation space excludes the relevant
  behavior;
- omitting a scale, boundary condition, imperfection, or competing branch;
- asking for one precise number when the scientifically relevant result is a
  regime, structure, or uncertainty; or
- solving a local task that does not advance the intended long-horizon
  program.

The answer is not to require the human to pose a perfect question alone.
Question formation should itself be collaborative:

1. The human states the physical phenomenon, motivation, and long-horizon
   interest.
2. Agents expose hidden assumptions and propose alternative formulations.
3. A separate reviewer attacks the premise, observable, and validation route
   rather than the proposed solution.
4. The human chooses or revises the scientific objective using physical
   judgment and research taste.
5. The campaign records what evidence would make the question answerable before
   large-scale implementation begins.

Agents may also originate valuable questions and broader connections. Human
authority lies in choosing which program to pursue and accepting the
consequences, not in claiming a monopoly on imagination.

This hypothesis should be tested prospectively. Future project logs should
record major question reformulations, who initiated them, why the earlier
formulation was inadequate, and whether a premise-focused review changed the
result. Until such evidence exists, the guide should not present upstream risk
as an observed frequency or as a failure unique to AI.

---

## 12. An operating model for agent-era research

The following model combines the strongest practices from the two projects. It
is a proposed operating framework, not a guarantee.

### 12.1 Write a research and evidence contract

Before a major campaign, record:

- the physical phenomenon and why it matters;
- the immediate question and its relation to the long-horizon program;
- governing assumptions and intended regime;
- required method identity and prohibited silent substitutions;
- allowed exploratory routes and their status;
- writable scope, external side effects, and approval boundaries;
- known-answer, structural, numerical, and experimental truth anchors;
- approximation axes and intended convergence evidence;
- claim states and publication eligibility; and
- who can stop, redirect, accept, and release the work.

The document can be short. Its purpose is to keep a technically successful
agent from silently optimizing a different scientific objective.

### 12.2 Separate roles, then rotate them when useful

At minimum, distinguish:

- **architect or deriver:** constructs the mathematics or method and names its
  weakest points;
- **executor:** implements, runs, and records the exact state;
- **verifier or falsifier:** attacks the weak points through routes with
  different failure modes;
- **integrator:** propagates accepted changes through code, artifacts, figures,
  and text; and
- **human scientific owner:** governs scope, evidence, meaning, stopping, and
  publication.

One participant may occupy several roles at different times. A load-bearing
derivation should not be accepted solely by the participant that produced it.

### 12.3 Keep exploratory freedom without losing method identity

Agents should be free to try conventional solvers, finite elements, surrogate
models, symbolic experiments, or alternative bases. Each route must be labeled
before its output approaches a paper figure:

```text
paper method | referee | diagnostic | oracle | superseded
```

A method-boundary crossing should trigger a concise update to the human owner:

```text
What method is actually running?
Why was the boundary crossed?
What claim can this route support?
What remains exploratory?
```

### 12.4 Close evidence as a graph

The working sequence is:

```text
choose and audit the question
  → fix the model and method contract
  → name falsification routes
  → derive, implement, and explore
  → verify the executed method
  → close coupled approximation axes
  → compare through independent physics and experiment
  → propagate source into artifact, claim, and figure
  → human accepts, narrows, redirects, or rejects
```

A correction upstream should invalidate or reopen its dependent claims. A test
that imports a non-shipping copy, silently skips, or only restates a definition
does not close the graph. A hash proves byte identity, not scientific meaning
or public availability. For a transformed public package, use portable paths
in the paper-facing release ledger, regenerate that ledger and the manifest
from the files that actually ship, and separately confirm that the scientific
payload agrees with the internal source artifact. Historical raw generation
records may retain machine-local paths when clearly labeled as nonportable
metadata.

### 12.5 Separate stopping from completion

The crack-tip campaign distinguished three decisions:

- **review again** when a promoted result lacks a falsification route adequate
  to its scope;
- **continue** when an unresolved item lies on the dependency path of a claim
  the paper needs; and
- **release** when the bounded claim graph passes its circuit and remaining
  work is explicitly outside the shipping claims.

Research completion is different. A symplectic nonlinear-mechanics program may
continue across many papers even when one bounded result is ready
([crack-tip case, §18](../case_studies/symplectic_mooney_rivlin_crack_tip.md#18-the-humans-critical-contributions)).

---

## 13. What remains uncertain

The evidence supports a major revision of the labor model, but not a universal
theory of human–AI science.

### Evidence base

The observations come from one human-led program in computational mechanics,
principally two intensive projects during January–July 2026. They are not a
controlled comparison of models, researchers, disciplines, or workflows. The
same human supplied the scientific program and much of the physical context in
both cases.

### Agent capability

The record establishes that particular agents made substantial mathematical,
computational, and verification contributions. It does not establish that AI
generally outperforms humans in mathematics or coding. The author's statement
that he would have been unlikely to select or implement some constructions
alone is a first-person reflection, not a benchmark.

### Symplectic generalization

The wrinkle framework has been extended from period doubling into a
period-four retained-space calculation. The crack-tip project demonstrates a
different nonlinear symplectic program with carefully scoped higher-order
results. Together they motivate a broader framework; they do not prove that
one symplectic method already covers a wide class of nonlinear problems.

### Unknown-answer discovery

The projects support the methodological conclusion that a known final value is
not required when a verified mathematical route exists. The credibility of
each future unknown answer will still depend on problem-specific gates. No
general procedure can guarantee that all relevant branches, model errors, or
physical mechanisms have been anticipated.

### Physical validation

The projects' generated evidence is computational and mathematical. FEM,
lattice, controls, and published experimental ranges provide valuable
comparisons, but the repository does not yet document an agent-era laboratory
campaign. Claims about physical reality remain bounded by the constitutive and
dimensional models.

### Upstream question risk

The proposition that stronger execution shifts risk toward question
formulation is plausible and consequential, but not yet directly demonstrated
here. It must remain labeled as a working hypothesis until future records
provide examples or counterexamples.

---

## 14. Practical questions before accepting a result

### About the question

- What phenomenon are we actually trying to understand?
- Why is this quantity or structure scientifically important?
- Which premise would most change the project if it were false?
- Does the immediate task advance the intended research program?

### About the model and method

- What equations, material assumptions, and boundary conditions define the
  claim?
- What are the executed unknowns and assembly operations?
- Has an oracle or diagnostic been mistaken for the claimed paper method?
- Which exact, weak, numerical, or empirical conditions are being used?

### About verification

- What could falsify the derivation rather than merely reproduce it?
- Has every coupled approximation axis been refined?
- Is the verifier accurate on the absolute scale of the observable?
- Is the correct mode, symmetry sector, and branch being followed?
- Do the independent checks actually have different failure modes?

### About validation

- Which comparison tests the model rather than another implementation of the
  same assumptions?
- Are there mechanism-removing controls?
- What experiment or observation could falsify the prediction?
- Is the intended physical regime inside the model's applicability range?

### About evidence and authority

- Can another participant reproduce the exact artifact from the current tree?
- Was each review finding checked against the actual schema, call path, or
  package role before it changed the claim?
- Do hashes govern the files that actually ship, with repository-relative
  paths in the public claims ledger and semantically checked transformed
  artifacts?
- Is reviewer identity taken from the artifact or verified metadata rather
  than inferred from the surrounding conversation?
- Which claims were retracted or superseded, and why?
- Did the latest correction reopen downstream claims?
- What remains provisional, open, or outside the paper?
- Who accepts responsibility for release?

---

## 15. Conclusion

The agent era does not eliminate the human role in research. It makes the old
defense of that role—humans think while AI codes—untenable.

Agents can contribute mathematics, architectures, code, execution, criticism,
and even broader synthesis. Humans need not remain the strongest local
mathematician or programmer. Their highest-leverage work increasingly lies in
choosing worthwhile questions, constructing and sustaining research programs,
governing assumptions and method boundaries, building a credible path to
warranted belief, interpreting results physically, and accepting responsibility
for what enters the scientific record.

Verification is what allows this partnership to move beyond answers known in
advance. A verified framework can become a discovery engine when its
derivation, implementation, approximation spaces, branch identity, error scale,
and provenance are controlled. Validation—ultimately including experiment—is
what connects that verified answer to reality.

The central adaptation is therefore not “trust AI more.” It is:

> Ask better questions, permit deeper technical contribution, and require
> stronger evidence than either participant's confidence.

That combination makes it possible to pursue mathematical programs that the
human might not execute alone without surrendering scientific judgment or
responsibility.

---

## Evidence record

The principal public records used for this guide are:

- [Symplectic wrinkle period-doubling and quadrupling case
  study](../case_studies/symplectic_wrinkle_period_doubling.md)
- [Symplectic Mooney–Rivlin crack-tip case
  study](../case_studies/symplectic_mooney_rivlin_crack_tip.md)
- [March–April 2026 human–AI research field
  guide](lessons_human_ai_research.md)
- [July 2026 guide review note](GUIDES_REVIEW_NOTE_2026-07-20.md)

At the 20 July 2026 audit, both companion scientific repositories were release
candidates. The wrinkle companion is now public; the crack-tip companion
remains a release candidate:

- [nonlinear-symplectic-wrinkle-bifurcations](https://github.com/tengzhang48/nonlinear-symplectic-wrinkle-bifurcations)
  — public companion release
- `nonlinear-symplectic-mooney-rivlin-crack-tip` — public visibility pending

- **Version:** 1.1 (conversation and cross-review update)
- **Last updated:** 22 July 2026
- **Evidence window:** January–July 2026
- **Scope:** One human–multi-agent computational-mechanics research program
- **Research framing and responsibility:** Teng Zhang
- **Evidence synthesis and draft:** Codex (GPT-5), 20–22 July 2026
