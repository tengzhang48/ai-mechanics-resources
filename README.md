# ai-mechanics-resources

*Integrating domain expertise, physics, and AI in mechanics research.*

Maintained by [Teng Zhang](https://github.com/tengzhang48), Department of Mechanical and Aerospace Engineering, Syracuse University.

**New here?** Read [START_HERE.md](START_HERE.md) for the six essential lessons in five minutes.

---

## About

The bottleneck in mechanics research is not just writing code. It is keeping the physical question, mathematical formulation, executed method, numerical evidence, and scientific claim coherent. AI agents have shifted the distribution of work more dramatically than earlier coding assistants: they can contribute to derivation, architecture, implementation, execution, review, and evidence integration. The durable boundary is no longer “human thinks, AI codes.” It is the assignment of scientific authority, evidence, and accountability.

Good research has always come from combining different perspectives. Agents add mathematical and computational reach, but their confidence does not authorize a claim. The human scientific owner still chooses and sustains the research program, governs assumptions and method boundaries, interprets physical meaning, and accepts responsibility for publication. Verification and validation must become stronger as technical work is delegated more deeply.

**But AI collaboration carries specific risks that differ from human collaboration.** Through extensive practice, we identified failure modes that are subtle, reproducible, and dangerous for research integrity:

- **AI gives confident wrong answers** — correct math, proper terminology, plausible reasoning, but the technique doesn't apply to your specific problem. Detected only by understanding *why* a technique works, not just *when* it's used.
- **AI can silently substitute a familiar method for the requested methodology** — the code runs and the result may be physically plausible, but the executed assembly does not support the paper's method claim.
- **“Tests pass” does not mean “the claim is established”** — a test may exercise the wrong copy, share the same flawed oracle, skip a guard, or verify a structural property while missing the mechanism of interest.

These risks are documented with real examples and specific mitigations in the [AI Risks and Mitigation](guides/lessons_ai_risks_and_mitigation.md) guide.

**An important caveat:** No individual may understand every agent-derived equation or implementation equally deeply. The response cannot be blind trust or a demand that the human reproduce everything unaided. It must be evidence-governed trust: explicit assumptions, method identity, falsifiable gates, coupled convergence, independent failure modes, provenance, bounded claims, and accountable acceptance.

This repository documents one researcher's experience across several mechanics projects. The evidence is case-based, not a measurement of how often any model or failure occurs. Failures, retractions, open claims, and successful verification routes are retained so that proposed lessons can be challenged rather than repeated as slogans.

**Current release:** July 2026 agent-era update. The March–April guide
generation is retained on branch
[`archive/guides-march-2026`](https://github.com/tengzhang48/ai-mechanics-resources/tree/archive/guides-march-2026).
Model names are treated as dated provenance rather than permanent capability
rankings.

---

## Contents

### Guides

| Guide | What it covers |
|---|---|
| [Human–AI Research in the Agent Era](guides/lessons_human_ai_research_agent_era.md) | **Current guide.** Division of authority rather than capability; human research taste; verified discovery without a known final answer; verification versus validation; nuisance-aware observable design; premise and boundary-value-problem audits; evidence-governed trust; and artifact-specific stopping and submission. |
| [Lessons from Human-AI Collaboration](guides/lessons_human_ai_research.md) | **Historical March–April 2026 field guide.** Plan-first chat workflow, numerical and software lessons, context management, and the earlier human/AI labor model. Retained for provenance with a current-status banner. |
| [How Debate with AI Produces Understanding](guides/lessons_from_conversation.md) | Historical conversation experiments on challenge, correction, disagreement, and review triage. |
| [AI Risks and Mitigation](guides/lessons_ai_risks_and_mitigation.md) | Historical risk taxonomy covering plausible inapplicability, method substitution, inadequate tests, debugging spirals, and plausible quantitative errors. Read with its July qualification banner. |
| [From Information to Knowledge](guides/information_to_knowledge.md) | Historical analysis of corrections, dependency propagation, validity bounds, and persistent knowledge. Product-level memory claims predate the agent-era update. |
| [July 2026 Guide Review Note](guides/GUIDES_REVIEW_NOTE_2026-07-20.md) | Claim-by-claim audit of outdated statements, internal contradictions, technical qualifications, and recommended propagation work. |

### Case Studies

Real project experiences — what happened, what worked, what didn't. Released as projects reach publication milestones.

| Case Study | What it shows |
|---|---|
| [Symplectic Wrinkle Period Doubling and Quadrupling](case_studies/symplectic_wrinkle_period_doubling.md) | Method substitution and recovery, analytical-depth construction, coupled convergence, review findings treated as hypotheses, physics-first evidence layers, provenance, and human/agent contributions. |
| [Symplectic Mooney–Rivlin Crack Tip](case_studies/symplectic_mooney_rivlin_crack_tip.md) | Unknown nonlinear fields made auditable through asymptotics, constrained action, FEM controls, multi-agent falsification, claim graphs, and an explicit program/result boundary. |
| [LBM-IBM for Thin Shells in Fluid](case_studies/lbm_ibm_thin_shell.md) | Extending from solid mechanics into CFD with AI assistance. Five paradigm shifts, practitioner blind spots, multi-AI debugging. |
| [Large-Deformation Self-Contact](case_studies/large_deformation_contact.md) | Where fast iteration cannot overcome fundamental numerical difficulty. Plasticity succeeded; contact struggled. Four frameworks, five formulations. |
| CoupLB: LBM+IBM for LAMMPS | Building a production MPI-parallel package. *(available after review)* |
| CoupMPM: MPM for LAMMPS | Complex package, scalable architecture. *(planned)* |

### Repository Structure

```
ai-mechanics-resources/
├── README.md
├── START_HERE.md
├── contributing.md
├── guides/
│   ├── README.md
│   ├── lessons_human_ai_research_agent_era.md
│   ├── lessons_human_ai_research.md
│   ├── lessons_from_conversation.md
│   ├── lessons_ai_risks_and_mitigation.md
│   ├── information_to_knowledge.md
│   └── GUIDES_REVIEW_NOTE_2026-07-20.md
└── case_studies/
    ├── symplectic_wrinkle_period_doubling.md
    ├── symplectic_mooney_rivlin_crack_tip.md
    ├── lbm_ibm_thin_shell.md
    └── large_deformation_contact.md
```

---

## How to Use This

**Starting an agent-assisted research project?** Read [Human–AI Research in the Agent Era](guides/lessons_human_ai_research_agent_era.md) for the current methodology.

**Studying the transition from chat assistants?** Read the [March–April field guide](guides/lessons_human_ai_research.md) together with the [July review note](guides/GUIDES_REVIEW_NOTE_2026-07-20.md).

**Want to understand AI risks?** Read the historical [AI Risks and
Mitigations guide](guides/lessons_ai_risks_and_mitigation.md) for specific
failure modes and their mitigations, together with its July qualification
banner.

**Thinking about AI memory and knowledge persistence?** Read the historical
[Information to Knowledge guide](guides/information_to_knowledge.md) for the
earlier observations on why longer context alone may not solve the real
problem.

**Want to understand verified discovery?** Read the two symplectic case studies. For a case where rapid iteration could not overcome the numerical formulation, read the contact study.

**Want to contribute?** See [contributing.md](contributing.md). Observations
must come from real, tested experience; reflections and hypotheses must be
labeled clearly.

---

## Related Projects

- [CoupMPM](https://github.com/tengzhang48/CoupMPM) — Material Point Method package for LAMMPS
- [CoupLB](https://github.com/tengzhang48/CoupLB) — Lattice Boltzmann + Immersed Boundary Method for LAMMPS
- [taichi_lbm_ibm](https://github.com/tengzhang48) — LBM+IBM solver for thin-shell aerodynamics
- [nonlinear-symplectic-wrinkle-bifurcations](https://github.com/tengzhang48/nonlinear-symplectic-wrinkle-bifurcations)
  — Public companion release for the analytical-depth wrinkle bifurcation
  framework
- [nonlinear-symplectic-mooney-rivlin-crack-tip](https://github.com/tengzhang48/nonlinear-symplectic-mooney-rivlin-crack-tip)
  — Public companion for the nonlinear crack-tip theory, verification code,
  curated data, and figure reproduction

---

## Citation

If useful, a citation is appreciated:

```
Zhang, T. (2026). AI-Mechanics-Resources: Integrating domain expertise, physics,
and AI in mechanics research. https://github.com/tengzhang48/ai-mechanics-resources
```
