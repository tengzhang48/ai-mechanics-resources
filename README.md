# ai-mechanics-resources

*Integrating domain expertise, physics, and AI in mechanics research.*

Maintained by the [Zhang Research Group](https://github.com/tengzhang48), Department of Mechanical and Aerospace Engineering, Syracuse University.

---

## About

The bottleneck in mechanics research is not just writing code — it's integrating the physics, mathematical formulation, algorithmic design, and implementation into a coherent whole. AI has shifted the ratio of effort, but both the thinking and the coding matter. What changed is that AI can now be a genuine collaborator in both — helping develop the plan, not just executing it.

Collaboration has always been how good research gets done. A CFD colleague might suggest blade element theory in the first conversation; a student might spot a sign error; an AI might recognize a structural connection across subfields. AI is one more perspective to integrate, and we should all be thinking about how to adapt.

This repository documents what I've learned from integrating AI into my research workflow over the past year across multiple mechanics simulation projects. I document failures as carefully as successes, and I hope others will contribute their own experiences.

**Last updated:** March 2026. Guides reflect practice with Claude Opus 4.6, Gemini 2.5, DeepSeek, and Qwen as of early 2026. AI tools change fast; the methodology here is more stable than the specific tools.

---

## Contents

### Guides

| Guide | What it covers |
|---|---|
| [Lessons from Human-AI Collaboration](guides/lessons_human_ai_research.md) | The main document. One year of daily AI-assisted development. The plan-first workflow, iterative debugging, context management, multi-AI review with triage, when to force a change of approach. What AI contributes to scientific reasoning and where it fails. |
| [How Debate with AI Produces Understanding](guides/lessons_from_conversation.md) | Three modes of productive human-AI debate. How to break the agreement equilibrium. Why asking AI to push back — and bringing one AI's output to another for review — produces deeper analysis than asking for answers. |

### Case Studies

Real project experiences — what happened, what worked, what didn't. Released as projects reach publication milestones.

| Case Study | What it shows |
|---|---|
| [LBM-IBM for Thin Shells in Fluid](case_studies/lbm_ibm_thin_shell.md) | Extending from solid mechanics into CFD with AI assistance. Five paradigm shifts, practitioner blind spots, multi-AI debugging. |
| [Large-Deformation Self-Contact](case_studies/large_deformation_contact.md) | Where fast iteration cannot overcome fundamental numerical difficulty. Plasticity succeeded; contact struggled. Four frameworks, five formulations. |
| CoupLB: LBM+IBM for LAMMPS | Building a production MPI-parallel package.|
| CoupMPM: MPM for LAMMPS | Complex package, scalable architecture. *(planned)* |

### Repository Structure

```
ai-mechanics-resources/
├── README.md
├── LICENSE
├── contributing.md
├── guides/
│   ├── lessons_human_ai_research.md
│   └── lessons_from_conversation.md
└── case_studies/
    ├── lbm_ibm_thin_shell.md
    └── large_deformation_contact.md
```

---

## How to Use This

**Starting an AI-assisted project?** Read `guides/lessons_human_ai_research.md` for the full methodology.

**Want to understand limits?** Read the case studies, especially the contact one.

**Want to contribute?** See [contributing.md](contributing.md). Requirement: real, tested experience only.

---

## Related Projects

- [CoupMPM](https://github.com/tengzhang48/CoupMPM) — Material Point Method package for LAMMPS
- [taichi_lbm_ibm](https://github.com/tengzhang48) — LBM+IBM solver for thin-shell aerodynamics

---

## License

[MIT License](LICENSE). If useful, a citation is appreciated:

```
Zhang, T. (2026). AI-Mechanics-Resources: Integrating domain expertise, physics,
and AI in mechanics research. https://github.com/tengzhang48/ai-mechanics-resources
```
