# Start Here

Five lessons from a few months of using AI in mechanics research. Each one was learned the hard way. The full details, case studies, and examples are in the rest of this repository.

---

**1. Develop the plan with AI before writing any code.**

The most productive workflow is not "describe the task, get code." It's: discuss the physics and requirements extensively with AI → have AI write a detailed implementation plan with explicit equations and numerical framework → send the plan to other AIs for adversarial review → refine until multiple reviewers converge → only then implement. The plan is more important than the code. A good plan enables everything that follows; a bad plan produces fast, wrong code.

**2. Use multiple AIs, and make them disagree.**

One AI as your primary development partner. Other AIs (different models) to review the plan and the code. Don't ask "is this good?" — ask "what's missing?" and "find the errors." Different models catch different things because they have different training biases. When two AIs disagree, the disagreement itself is informative. Ask AI to push back on your own ideas too — "what's wrong with my approach?" produces deeper analysis than "what do you think?"

**3. AI-generated code that runs without errors can still be wrong.**

This is the most dangerous failure mode in scientific computing. Code compiles, executes, produces plausible-looking numbers — but the numbers don't match physical reality. A 2.3× error from a unit mismatch. An integer division bug that silently zeros a term. Gradients that produce NaN only at edge cases. No AI review catches these. You need independent reference solutions — analytical results, simpler prototype codes, commercial software comparisons — for every testable claim. If you can't validate it, you can't trust it.

**4. Know when to force a change of approach.**

When AI's fixes keep failing — three or more attempts on the same error, each introducing new problems, all variations within the same family — the problem is usually not in the details but in the approach itself. AI generates variations within a paradigm. It cannot recognize when the paradigm is wrong. That's your job. Say: "Stop. This family of approaches has failed repeatedly. Propose something fundamentally different."

**5. AI lowers the implementation barrier, not the thinking barrier.**

AI lets you explore more approaches, test alternatives faster, and implement ideas that would have taken months by hand. But it doesn't replace the physics understanding, the mathematical formulation, or the judgment to know whether results are correct. The researchers who benefit most from AI are those who already have strong domain foundations — AI amplifies what you bring. Invest in understanding the physics deeply; AI handles the rest.

---

**Want more?** Read the [full methodology](guides/lessons_human_ai_research.md) for detailed patterns and examples. Read the [case studies](case_studies/) to see these lessons in action — including the failures.
