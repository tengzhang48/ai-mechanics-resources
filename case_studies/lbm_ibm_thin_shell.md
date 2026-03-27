# Case Study: Extending into an Adjacent Field with AI — LBM-IBM for Thin Shells

**How a mechanics researcher and AI built a fluid-structure solver from scratch, and what it teaches about human-AI collaboration in unfamiliar territory.**

---

## 📖 Table of Contents

- [Overview](#overview)
- [1. Starting Point](#1-starting-point)
- [2. The Paradigm Shifts](#2-the-paradigm-shifts)
- [3. The Chirality Debugging Saga](#3-the-chirality-debugging-saga)
- [4. Where AI Helped](#4-where-ai-helped)
- [5. Where AI Failed](#5-where-ai-failed)
- [6. The Human's Irreplaceable Contributions](#6-the-humans-irreplaceable-contributions)
- [Summary](#summary)

---

## Overview

The `taichi_lbm_ibm` project set out to simulate samara (maple seed) autorotation — a free-flight fluid-structure interaction problem where a thin, cambered wing spontaneously develops stable rotation as it falls through air. This is a challenging problem in computational biomechanics.

The researcher (Teng) is an expert in solid mechanics who had prior experience running LBM-IBM simulations using others' code, but had not built a solver from scratch or engaged deeply with IBM formulation-level details. The AI (Claude) has broad knowledge of LBM and IBM methods but no ability to run simulations. Together, over approximately four months, the project went through several major paradigm shifts, abandoned dead-end approaches, and produced a working framework for thin-shell aerodynamics.

This case study focuses on the collaboration patterns — how AI helped bridge the gap from code user to method developer, where AI failed, and what the human contributed that AI could not.

---

## 1. Starting Point

Teng came to the project with deep expertise in continuum mechanics and prior experience using LBM-IBM codes developed by others. He had run LBM-IBM simulations before and made minor modifications, but had not built a solver from scratch or deeply engaged with formulation-level details of IBM force computation and sub-grid thin-shell aerodynamics. The goal was to build a new GPU-accelerated solver in Taichi.

**What the human brought:** Physical intuition about forces and torques, rigorous validation habits, the ability to identify when results were physically implausible, deep understanding of thin-shell mechanics, and working familiarity with LBM-IBM from running others' codes.

**What AI brought:** Broad knowledge of LBM variants, IBM methods, the relevant literature, and the ability to generate complete simulation codes in Taichi.

**What AI did not have:** The ability to run any code, physical intuition about whether results "looked right," or experience with production-scale simulations.

---

## 2. The Paradigm Shifts

The project did not proceed linearly. It went through several fundamental changes of approach, each driven by the discovery that the current method had an unfixable limitation for thin shells.

### Cut-Cell → IBM

The initial approach used a cut-cell method for the solid-fluid boundary. But the wing is much thinner than the lattice spacing — both surfaces fall within the same lattice cell, causing double-counting of momentum exchange.

**Who identified it:** The human suspected the method was "using some trick to get good looking results without solving the real physics." The AI confirmed the double-counting mechanism analytically. IBM was adopted as the correct approach for sub-grid thin structures.

### Velocity Correction → Stress-Based Methods

The standard IBM velocity correction smears across both surfaces of a thin shell, over-predicting forces. The AI proposed switching to stress tensor interpolation, where force is computed from the stress field rather than velocity corrections. The human validated by comparing force magnitudes.

### Iterating Through Stress Variants

The two-sided stress method still under-predicted forces for zero-thickness shells. The AI proposed a directionally-split variant, and further iterations followed, each attempting to improve force recovery on thin shells.

**The collaboration pattern across all shifts:** AI proposed alternatives rapidly — a new IBM variant within the same session when the previous one failed. The human ran each variant, compared against references, and judged whether the results were physically reasonable. The speed of testing alternatives was the key advantage: the project explored more approaches in weeks than traditional development would allow in months.

---

## 3. The Chirality Debugging Saga

This episode illustrates multi-AI cross-checking in action.

**The problem:** A blending parameter that should be positive came out negative. The IBM torque was opposing the prescribed rotation rather than driving it.

**What happened:**
- Claude proposed two hypotheses (sign error in code, double-negation bug). Both were wrong — the code was correct.
- The human sent the problem to Gemini. Gemini proposed a different hypothesis: the prescribed rotation direction was wrong (chirality mismatch). This turned out to be correct.
- Gemini also made a wrong sub-claim about the torque magnitude. Claude correctly identified this error.
- The definitive test was physical: a free-flight simulation confirmed the natural rotation direction. The fix was a one-line configuration change.

**What this teaches:**
- Configuration errors can masquerade as algorithmic bugs. AI looks for code bugs because that's what it's trained to find.
- Multiple AI systems give conflicting diagnoses. The human must evaluate each claim independently.
- The definitive diagnostic was running the simulation and observing the physics. No amount of code tracing substitutes for this.
- Neither AI alone was reliable. The human's judgment across both produced the correct answer.

---

## 4. Where AI Helped

**Literature navigation.** The AI identified relevant papers that the human would not have found through keyword searches in an unfamiliar field, and could assess which papers were methodologically relevant vs. merely topically related.

**Method generation.** The AI generated complete LBM-IBM simulation codes in Taichi — collision operators, streaming, boundary conditions, IBM coupling. For a researcher building an LBM-IBM solver from scratch, this would have taken months by hand.

**Derivations on demand.** When the project needed mathematical derivations in IBM theory, the AI performed them rapidly. The human verified the results but would have needed significant time to derive them independently in an unfamiliar field.

**Rapid prototyping of alternatives.** When one IBM variant failed, the AI generated the next within the same session. The speed of generating alternatives was the primary advantage — testing multiple approaches in weeks rather than months.

---

## 5. Where AI Failed

**Initial method selection was wrong.** The AI's first approach (cut-cell) was fundamentally inappropriate for sub-grid thin shells. The AI did not flag this until the human asked "what happens if the wall is only 0.1 lattice units thick?" The AI had the knowledge to explain why after being asked, but did not spontaneously apply it as a design constraint.

**Fabricated configuration fields.** The AI hallucinated YAML fields that don't exist in the codebase. Always verify field names against actual code.

**The chirality mislabel.** Claude spent two rounds proposing code bugs when the real issue was a configuration error. A different AI (Gemini) identified the correct hypothesis.

**The practitioner blind spot.** The standard engineering approach for sub-grid aerodynamic corrections on coarse grids — blade element theory — was not suggested until late in the project. A CFD expert with rotorcraft experience would have suggested it in the first conversation. The AI had the knowledge (it could derive and implement BET once prompted) but never spontaneously proposed it. AI approached the problem as a numerical methods challenge (how to measure forces better) rather than a physics modeling challenge (what forces are missing). This distinction — between improving measurement and adding missing physics — is the kind of framing that domain practitioners contribute and AI systems miss.

---

## 6. The Human's Irreplaceable Contributions

**Running simulations and judging results.** Coding agents can increasingly run scripts and iterate on errors autonomously. But in mechanics simulation, running the code is only the beginning — the harder part is judging whether the output is physically correct. Inspecting a flow field in ParaView, recognizing that a wake structure looks wrong for the Reynolds number, comparing a deformed mesh against physical intuition — these require domain understanding that execution agents don't have. As agents become more capable at running and debugging code, the human's role shifts further toward interpreting and validating results rather than executing commands.

**Physical plausibility checks.** Recognizing when results don't match expected physical behavior requires knowing what the answer should approximately be. AI could not identify implausible results without being told the expected range.

**Forcing paradigm shifts.** When the cut-cell method failed, the AI would have continued patching it. The human recognized "the authors used some trick to get good looking results." Each time, the human recognized when an approach was fundamentally limited, not merely buggy.

**Experimental validation.** Physical experiments, comparisons against published data, and judgment about experimental uncertainty all required the human.

**Strategic direction.** Deciding which problems to prioritize, which validation tests matter, when to write up vs. keep developing — these research management decisions require judgment about the field that AI does not possess.

---

## Summary

This project would not have been feasible at the formulation level without AI assistance. A solid mechanics researcher who had previously used LBM-IBM codes built a new solver from scratch — going from code user to method developer. AI provided the formulation-level knowledge, code generation, and literature awareness that bridged the gap.

Every major breakthrough came from the human: the suspicion about cut-cell error cancellation, the insistence on physical validation, the recognition of when to abandon a failed approach. AI accelerated exploration within paradigms but could not identify when a paradigm was wrong.

The key asymmetry: the human could not have done this project alone at the formulation level — it would have required deep specialization that prior code-usage experience did not provide. AI could not have done it alone — it cannot run code, cannot perform experiments, and does not recognize when its own approaches are fundamentally flawed. The combination produced results that neither could achieve independently.

The distinction between "using a tool" and "developing a tool" matters. AI helped the human become someone who develops methods, not just someone who runs others' code. In adjacent fields where one has working familiarity but not formulation-level depth, AI can bridge the gap to enable original contributions.

---

*This case study documents the development of the taichi_lbm_ibm package during 2025–2026. The project remains under active development.*

**Version:** 2.0
**Last Updated:** March 2026
**Project:** taichi_lbm_ibm (https://github.com/tengzhang48)
