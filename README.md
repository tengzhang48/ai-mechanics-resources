# ai-mechanics-resources

*Human‑in‑the‑loop guides for AI‑assisted computational research*

A curated knowledge base for graduate students and researchers—tools, methods, lessons, and practical guides for using AI effectively in computational mechanics, with a strong emphasis on validation, documentation, and the critical role of human judgment.

Maintained by the [Zhang Research Group](https://github.com/tengzhang48), Department of Mechanical and Aerospace Engineering, Syracuse University.

---

## 🚀 Goal

Provide a structured, validated collection of best practices for integrating AI into computational mechanics research. The repository focuses on:

- **Human‑in‑the‑loop workflows** – AI amplifies, but does not replace, researcher expertise.
- **Practical, tested guides** – every document includes version information, failure case documentation, and validation steps.
- **Reusable templates** – for AI context files, validation checklists, and error logging.

The ultimate goal is to reduce the learning curve for new researchers and help the broader community adopt AI tools safely and effectively.

---

## 🔧 Installation

This repository is entirely documentation‑based; no software installation is required to read the guides. To clone the repository for offline access:

```bash
git clone https://github.com/yourusername/ai-mechanics-resources.git
cd ai-mechanics-resources
```

All guides are written in Markdown and can be viewed directly on GitHub or with any Markdown reader.

---

## 📖 Usage

The repository is organized by topic. Start with the sections that match your immediate need:

### 1. AI‑Assisted Workflow
- Read `LLMs/Prompt_Engineering_Guide.md` for practical tips.
- Read `LLMs/Lessons_Human_AI_Research.md` to understand the capabilities and limits of AI in research.

### 2. Software Setup
- Navigate to `software/` for version‑pinned installation and usage guides (e.g., `fenicsx.md`, `jax.md`).
- Use the HPC setup guide in `hpc_resources/` for cluster‑agnostic configuration.

### 3. Theory & Methods
- Reference documents in `theory/` (contact mechanics, constitutive models, LBM‑IBM, etc.) for derivations and implementation strategies.

### 4. Scientific Writing
- Consult `writing/` for paper structuring, peer review, and proposal writing.

### 5. Templates
- Reuse `templates/project_context_file.md` to create AI context files for your own projects.
- Use `templates/simulation_validation.md` to systematically validate simulations.

---

## 🧩 API (Content Structure)

This repository does not provide a code API, but the “API” of the knowledge base is its directory structure and the metadata inside each document. All documents follow a consistent pattern:

- **Front matter** (optional) – status, version, last updated.
- **Purpose** – what problem the guide solves.
- **Validated steps** – version‑pinned instructions.
- **Common pitfalls** – documented failures and solutions.
- **References** – related papers, software documentation.

### Directory Tree

```
ai-mechanics-resources/
├── README.md                        ← You are here
├── LLMs/                            ← AI‑assisted research guides
│   ├── Prompt_Engineering_Guide.md      Practical prompt tips (validated)
│   ├── Lessons_Human_AI_Research.md     Framework: Can AI do science?
│   ├── Case_Study_CFD_Samara.md         Deep dive: LBM-IBM thin-shell project
│   ├── Case_Study_Contact_Scroll.md     Deep dive: bilayer scroll contact
│   └── contributing.md                  How to contribute
│
├── software/                        ← Software installation and usage
│   ├── fenicsx.md                       FEniCSx setup, tips, common pitfalls
│   ├── jax.md                           JAX for scientific computing
│   ├── lammps.md                        LAMMPS compilation, packages, scripting
│   ├── abaqus.md                        ABAQUS scripting, validation workflows
│   ├── taichi.md                        Taichi for GPU simulation
│   └── paraview.md                      Visualization and post‑processing
│
├── theory/                          ← Method references and derivations
│   ├── contact_mechanics.md            Contact methods survey + implementation plan
│   ├── constitutive_models.md          Hyperelasticity, viscoplasticity, log strain
│   ├── lbm_ibm.md                      Lattice Boltzmann + Immersed Boundary
│   ├── mpm.md                          Material Point Method essentials
│
├── writing/                         ← Scientific communication
│   ├── paper_writing.md                How to write papers (structure, style)
│   ├── peer_review.md                  Transparent peer review guide
│   └── proposals.md                    Proposal writing tips
│
├── templates/                       ← Reusable templates
│   ├── project_context_file.md         Template for AI context files
│   ├── simulation_validation.md        Validation checklist template
│   └── error_log.md                    AI mistake logging template

```

**Note:** Not all folders may be fully populated in the public version. Some sections are under active development; contributions are welcome.

---

## 🤝 Contributing

See `LLMs/contributing.md` for detailed guidelines. The short version:

1. Every contribution should be **tested and validated**, not theoretical.
2. Include **which software version** you tested with.
3. Include **what went wrong** as well as what worked — failure documentation is as valuable as success documentation.
4. Use Markdown for all documents (renders on GitHub, searchable, diff‑friendly).

---

## 📄 License

This work is shared under [MIT License](LICENSE). If you use these guides in your own research group, a citation or acknowledgment is appreciated.

---

*“In the AI era, the bottleneck shifts from finding information to validating it. These documents exist to help you validate faster—with you in the loop.”*
