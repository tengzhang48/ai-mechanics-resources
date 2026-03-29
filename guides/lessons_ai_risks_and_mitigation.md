# AI Risks and Mitigations in Research

**Concrete risks identified from practice, with specific prevention strategies.**

Part of the [AI-Mechanics-Resources](../README.md) collection.  
For the full methodology guide, see [Lessons from Human-AI Collaboration](lessons_human_ai_research.md).  
For the debate methodology, see [How Debate with AI Produces Understanding](lessons_from_conversation.md).

---

## Why This File Exists

The lessons guide documents what works. This file documents what goes wrong
and how to prevent it. Every risk here was discovered in real research projects,
not hypothesized. The examples come from computational mechanics, but the
patterns are general.

---

## Risk 1: The Confident Wrong Answer

**What happens:** AI recommends a technique with correct math, proper
terminology, specific implementation details — but the technique doesn't
apply to your specific problem.

**Real example:** An AI recommended SIMP penalization (ρ³) for MMC topology
optimization. The recommendation included the correct formula, the correct
derivative (3ρ²), and a plausible physical explanation. But MMC generates
density through geometric SDFs, not independent element variables — SIMP
penalization would suppress legitimate boundary information and create
vanishing gradients in void regions.

**Why it happens:** AI pattern-matches: "blurry density in topology
optimization → apply SIMP." SIMP is the dominant technique in the field
(thousands of papers). MMC is a different paradigm where SIMP doesn't apply.
The AI recognized the symptom but not the mechanism.

**How to detect:**
- Ask "WHY does this problem occur in my specific method?" If the AI's
  explanation references the general problem rather than your specific
  mechanism, the recommendation may be pattern-matching.
- Ask a different AI to critique the recommendation.
- Check whether the technique's assumptions hold for your method.

**How to prevent:**
- When receiving technical recommendations, require the AI to explain
  the causal chain: what causes the problem → why this fix addresses
  that cause → what assumptions the fix requires → whether those
  assumptions hold for your method.
- Compare against your working reference. The 2D numpy code used
  `ρ_e × K0` (no SIMP) and produced clear topologies — this
  immediately disproved the claim that SIMP was needed.

---

## Risk 2: The Silent Methodology Substitution

**What happens:** AI replaces your specific methodology with the mainstream
approach without flagging the change. The code runs correctly, all tests pass,
but the method described in your paper is not the method implemented in
your code.

**Real example:** The project uses a lattice model (CoupLAM — I1 springs +
area penalty) with specific computational advantages (10-50× cheaper matvec).
The theory document describes lattice springs. An existing implementation
correctly uses lattice springs. But when multiple AIs implemented the VEN
simulation engine, they ALL wrote standard FEM (B^T D B) instead. No AI
mentioned the substitution. The code produced physically correct results
and passed all validation tests.

**Why it happens:** AI training data contains vastly more FEM code (~100,000
papers) than lattice model code (~10 papers). When asked to "implement
element stiffness," the statistically dominant answer is B^T D B. The AI
doesn't distinguish between "implement a correct method" and "implement
YOUR method."

**Why this is the most dangerous risk:** Unlike the confident wrong answer
(Risk 1), which is a visible recommendation that can be evaluated and
rejected, the silent substitution is invisible. There is no error signal.
The code compiles, runs, produces correct physics, and passes tests. The
only way to detect it is to compare the implementation against the theory
document — which requires understanding both deeply.

**How to detect:**
- **Dry-run prompts:** Ask the AI to explain the code's computational
  backbone step by step: "Walk me through exactly how the element stiffness
  is computed. What energy does it correspond to? What constitutive model
  does it use?" If the explanation describes FEM when your method uses
  lattice springs, you've found the substitution.
- **Methodology-specific tests:** Don't just test "does this produce correct
  mechanical behavior." Test "does this produce the SPECIFIC behavior that
  distinguishes my method from the standard approach." For example: compute
  the Q4 stiffness both ways and compare — if they differ (as they do for
  the volumetric part), the test reveals which formulation is actually used.
- **Name things after the methodology.** `q4_lattice_stiffness()` instead
  of `q4_stiffness()`. The name itself signals what the function should
  contain.

**How to prevent:**
- State the methodology explicitly in EVERY prompt. Not "implement element
  stiffness" but "implement CoupLAM lattice stiffness: I1 springs from
  partition of unity + area penalty, NOT standard FEM B^T D B."
- Include the theory document as context for every implementation session.
- When reviewing AI-generated code, compare against the theory document,
  not just against test results.

---

## Risk 3: Training Data Bias Toward Mainstream Approaches

**What happens:** AI systematically favors well-represented approaches over
niche ones. This isn't a single error — it's a persistent pull toward
the most common solution in the training data.

**Confirmed instances from our work:**
1. FEM B^T D B instead of CoupLAM lattice springs (Risk 2)
2. SIMP penalization applied to MMC (Risk 1)
3. Every stiffness function defaulted to the standard formulation
4. No AI spontaneously suggested the lattice formulation even when the
   existing lattice code (couplam_jax.py) was in the context

**The broader pattern:** If your research contribution involves a niche
methodology (fewer than ~100 papers), AI will default to the mainstream
alternative unless explicitly constrained. This isn't a bug — it's a
fundamental property of how language models learn from data distributions.

**Implications for research creativity:**

AI creativity falls into categories that differ in reliability:

| Type of creativity | AI capability | Why |
|---|---|---|
| **Cross-field connections** | Strong | Both fields are in the database; AI bridges them faster than human search |
| **Known solutions to known problems** | Strong | 24-tet decomposition, MC33, etc. — well-documented in literature |
| **Combining existing components in new ways** | Moderate | Architecture proposals, framework unification |
| **Niche methodology applied to new problems** | Weak | If the niche method has few papers, AI defaults to mainstream |
| **Challenging the dominant paradigm** | Very weak | AI reflects the consensus; it cannot judge that the consensus is wrong for your specific case |

**How to prevent:**
- Use AI for cross-field connections (where it's strong) and human judgment
  for methodology choices (where AI is biased toward mainstream).
- When your method differs from the mainstream, treat every AI implementation
  as potentially substituted until verified against the theory.
- Maintain a "methodology checklist" that lists the specific features that
  distinguish your approach from the standard one. Review every AI-generated
  implementation against this checklist.

---

## Risk 4: "Tests Pass" Does Not Mean "Method Is Correct"

**What happens:** The standard practice of validating code through test
suites fails to catch methodology substitutions because the tests verify
physical correctness, not methodological correctness.

**Real example:** The VEN simulation with FEM stiffness passed ALL tests:
- Full solid compliance matched Q4 FEM reference ✓
- Single bar compliance was finite and reasonable ✓
- Parameter sweep showed monotonic convergence ✓
- Optimizer reduced compliance from 256 to 95 ✓

Yet the code used FEM instead of lattice. The tests verified "does this
solve the mechanics correctly" but not "does this use the CoupLAM
formulation."

**The three levels of correctness:**

| Level | What it verifies | What it misses |
|-------|-----------------|----------------|
| **Runs** | No crashes, produces output | Everything |
| **Physically correct** | Results match known solutions | Methodology substitution |
| **Methodologically correct** | Implementation matches the paper's claimed method | Nothing (if tests are comprehensive) |

**How to design methodology-specific tests:**
- **Distinctive behavior test:** Find a case where your method gives a
  DIFFERENT answer from the mainstream approach. Use that as a test.
  For CoupLAM: the Q4 lattice stiffness differs from FEM by ~6% in the
  volumetric part. A test that checks for this difference confirms which
  formulation is used.
- **Component signature test:** Verify that intermediate computations
  match the theory. For lattice: check that spring constants for a unit
  square are μ/6 (edge) and μ/3 (diagonal). This is impossible to satisfy
  with FEM B^T D B.
- **Parameter sensitivity test:** If your method has different sensitivities
  than the mainstream approach, test those sensitivities.

---

## Risk 5: The Debugging Spiral

**What happens:** AI generates a fix that breaks something else, leading
to a cycle of fix-break-fix that never converges. The AI never stops itself.

**Real example:** Three iterations attempting to fix a 256-case hex lookup
table. Each fix addressed one symptom but revealed a new failure. The
fundamental problem (hex face ambiguity) was architectural, not implementational.

**How to detect:**
- You've patched the same function 3+ times
- Each fix introduces a new failure
- The failure count doesn't decrease monotonically
- You're adding special cases (if-else branches, heuristics)

**How to prevent:**
- After 2 failed attempts at the same problem, STOP. Summarize what works,
  what's broken, and why. Then design a new approach from scratch.
- AI will never suggest stopping. This judgment is purely human.
- Ask a different AI to propose alternatives rather than asking the same
  AI to fix its own approach.

---

## Risk 6: Plausible Results Hide Systematic Errors

**What happens:** AI-generated code produces results that look physically
reasonable but contain systematic errors (e.g., a constant factor off).

**Real example:** DeepSeek wrote a Hex8 stiffness function that was exactly
4× too small. The optimization still ran, compliance still decreased, the
topology still looked reasonable. The error was only caught by comparing
eigenvalues against a validated reference.

**Why it's dangerous:** Topology optimization is forgiving of stiffness
scaling errors — the optimizer finds the same topology, just with different
compliance values. The shapes look right. Only quantitative validation
catches the error.

**How to prevent:**
- Always compare against validated reference NUMBERS, not just qualitative
  behavior.
- For element stiffness: check eigenvalues (3 zero for 2D, 6 zero for 3D),
  check rigid body modes, check strain energy for known analytical cases.
- For optimization: compare final compliance against a known solution, not
  just "does it look like a truss."

---

## The Human Role: What AI Cannot Replace

Based on all risks above, these specific functions require human judgment:

| Function | Why AI fails | What human provides |
|---|---|---|
| **Methodology choice** | Training bias toward mainstream | Deep knowledge of niche method |
| **Detecting silent substitution** | AI doesn't know it substituted | Compare code vs theory document |
| **Deciding when to stop and rethink** | AI never stops itself | Pattern recognition: "this isn't converging" |
| **Testing methodology, not just physics** | AI writes tests for correctness | Tests for methodological distinctiveness |
| **Evaluating whether results are "right enough"** | AI doesn't know what matters | Physical intuition + domain expertise |
| **Defining the research question** | AI explores, human directs | Taste, constraints, strategic judgment |

**The key insight:** AI is a powerful tool within a paradigm defined by the
human. It cannot challenge the paradigm, detect when it's been silently
replaced, or judge when the paradigm itself is wrong. These are the core
functions of a researcher.

---

## The Dry-Run Prompt: A Specific Mitigation Tool

One practical technique that addresses Risks 2 and 4:

After AI generates code, before running it, ask:

```
Walk me through this code's computational backbone step by step.
For each major function:
1. What mathematical operation does it perform?
2. What physical/engineering model does it correspond to?
3. How does it differ from the standard textbook approach?
```

If the AI's explanation reveals standard FEM when you expected lattice
springs, standard SIMP when you expected MMC, or any other mainstream
substitution — you've caught Risk 2 without reading every line of code.

This works because explaining code requires less domain knowledge than
writing it. The AI can accurately describe what B^T D B computes even if
it doesn't understand why you wanted springs instead. The human recognizes
the mismatch.

**Limitation:** The dry-run prompt catches substitutions where the human
KNOWS what to expect. It doesn't catch cases where the human doesn't know
the correct methodology well enough to recognize the difference. This is
why domain expertise comes first — AI amplifies expertise but cannot
replace it.

---

## Summary: The Three Layers of Defense

```
Layer 1: PROMPT DESIGN
  → State methodology explicitly in every prompt
  → Name functions after the methodology
  → Include theory document as context

Layer 2: CODE REVIEW (dry-run + methodology check)
  → Ask AI to explain the computational backbone
  → Compare explanation against theory document
  → Check: does the implementation match the CLAIMED method?

Layer 3: TESTING (methodology-specific, not just physical correctness)
  → Design tests that distinguish your method from the mainstream
  → Compare against reference NUMBERS, not just qualitative behavior
  → Verify intermediate computations match theory
```

All three layers are needed. Prompt design reduces the frequency of
substitution. Code review catches substitutions that slip through.
Methodology-specific testing catches anything the review misses.

No single layer is sufficient. Tests alone failed (Risk 4). Code review
alone requires understanding both code and theory. Prompts alone don't
prevent AI from defaulting to training bias.

---

*Based on real errors from computational mechanics research, 2025-2026.
All examples documented in the case studies. Some patterns (training data
bias, silent substitution, debugging spirals) appear general across fields;
others may be specific to computational mechanics. The mitigations assume
the researcher has domain expertise — the risks are higher for those still
developing that expertise.*

**Version:** 1.0  
**Date:** March 2026
