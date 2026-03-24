AI-Mechanics-Resources

Human‑in‑the‑loop guides for AI‑assisted computational research.

A curated knowledge base for graduate students and researchers—tools, methods, lessons, and practical guides for using AI effectively in computational mechanics, with a strong emphasis on validation, documentation, and the critical role of human judgment.

Maintained by the Zhang Research Group, Department of Mechanical and Aerospace Engineering, Syracuse University.

Visit the Documentation Website (Update with your actual URL)

🚀 Goal

Provide a structured, validated collection of best practices for integrating AI into computational mechanics research. The repository focuses on:

Human‑in‑the‑loop workflows: AI amplifies, but does not replace, researcher expertise.

Practical, tested guides: Every document includes version information, failure case documentation, and validation steps.

Reusable templates: For AI context files, validation checklists, and error logging.

The ultimate goal is to reduce the learning curve for new researchers and help the broader community adopt AI tools safely and effectively.

🔧 Installation

This knowledge base is entirely documentation-based and designed to be viewed as a searchable website. You do not need to install any software to read these guides.

Online Website: Read the guides here (Provides the best reading experience)

Directly on GitHub: You can also browse the Markdown files natively in this repository.

Offline Access & Contributing

To clone the repository for offline access, using with a local Markdown editor, or to contribute:

git clone [https://github.com/yourusername/ai-mechanics-resources.git](https://github.com/yourusername/ai-mechanics-resources.git)
cd ai-mechanics-resources


📖 Usage

The repository is organized by topic. Start with the sections that match your immediate need:

AI‑Assisted Workflow

Read LLMs/Prompt_Engineering_Guide.md for practical tips.

Read LLMs/Lessons_Human_AI_Research.md to understand the capabilities and limits of AI in research.

Software Setup

Navigate to software/ for version‑pinned installation and usage guides (e.g., FEniCSx, JAX).

Theory & Methods

Reference documents in theory/ (contact mechanics, constitutive models, LBM‑IBM, etc.) for derivations and implementation strategies.

Scientific Writing

Consult writing/ for paper structuring, peer review, and proposal writing.

Templates

Reuse templates/project_context_file.md to create AI context files for your own projects.

Use templates/simulation_validation.md to systematically validate simulations.

🧩 API

This repository does not provide a code API, but the "API" of the knowledge base is its directory structure and the metadata inside each document. All documents follow a consistent pattern:

Front matter (optional) – Status, version, last updated.

Purpose – What problem the guide solves.

Validated steps – Version‑pinned instructions.

Common pitfalls – Documented failures and solutions.

References – Related papers, software documentation.

Directory Tree

ai-mechanics-resources/
├── README.md                        ← You are here
├── LLMs/                            ← AI‑assisted research guides
│   ├── Prompt_Engineering_Guide.md  # Practical prompt tips (validated)
│   ├── Lessons_Human_AI_Research.md # Framework: Can AI do science?
│   ├── Case_Study_CFD_Samara.md     # Deep dive: LBM-IBM thin-shell project
│   ├── Case_Study_Contact_Scroll.md # Deep dive: bilayer scroll contact
│   └── contributing.md              # How to contribute
├── software/                        ← Software installation and usage
│   ├── fenicsx.md                   # FEniCSx setup, tips, common pitfalls
│   ├── jax.md                       # JAX for scientific computing
│   ├── lammps.md                    # LAMMPS compilation, packages, scripting
│   ├── abaqus.md                    # ABAQUS scripting, validation workflows
│   ├── taichi.md                    # Taichi for GPU simulation
│   └── paraview.md                  # Visualization and post‑processing
├── theory/                          ← Method references and derivations
│   ├── contact_mechanics.md         # Contact methods survey + implementation
│   ├── constitutive_models.md       # Hyperelasticity, viscoplasticity, log strain
│   ├── lbm_ibm.md                   # Lattice Boltzmann + Immersed Boundary
│   └── mpm.md                       # Material Point Method essentials
├── writing/                         ← Scientific communication
│   ├── paper_writing.md             # How to write papers (structure, style)
│   ├── peer_review.md               # Transparent peer review guide
│   └── proposals.md                 # Proposal writing tips
└── templates/                       ← Reusable templates
    ├── project_context_file.md      # Template for AI context files
    ├── simulation_validation.md     # Validation checklist template
    └── error_log.md                 # AI mistake logging template


Note: Not all folders may be fully populated in the public version. Some sections are under active development; contributions are welcome.

🤝 Contributing

See LLMs/contributing.md for detailed guidelines. The short version:

Every contribution should be tested and validated, not theoretical.

Include which software version you tested with.

Include what went wrong as well as what worked — failure documentation is as valuable as success documentation.

Use Markdown for all documents (renders on GitHub, searchable, diff‑friendly).

📄 License & Citation

This work is shared under the MIT License.

If you use these guides in your own research group, a citation or acknowledgment is greatly appreciated.

"In the AI era, the bottleneck shifts from finding information to validating it. These documents exist to help you validate faster—with you in the loop."
