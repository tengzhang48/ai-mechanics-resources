# Review Note: `guides/` Materials

- **Review status:** Review only; no source guide was edited
- **Review date:** 2026-07-20 (UTC)
- **Reviewer:** Codex (GPT-5)
- **Repository snapshot:** `9688f26cdf07d74e79b1e95972417f31da8c0791` (`main`, one commit ahead of `origin/main`)
- **Additional workspace evidence:** `case_studies/symplectic_wrinkle_period_doubling.md` was untracked at the time of review and is therefore treated as current workspace evidence, not yet as committed public evidence.

> **Snapshot navigation:** All guide line ranges, word counts, and hashes in
> this note refer to commit `9688f26` before the July historical banners were
> added. That exact guide generation is preserved on
> `archive/guides-march-2026`. The banners on the current branch shift raw line
> numbers but do not change the audited historical text.

## 1. Overall verdict

The central lessons of these guides still hold:

- a plausible numerical answer is not enough;
- equations, implementation, artifacts, figures, and prose must agree;
- method substitution can survive ordinary output checks;
- corrections need rationale and downstream propagation;
- independent checks must target different failure modes;
- human scientific accountability and domain judgment remain essential.

The guides nevertheless need a substantive update before they are presented as current, evergreen guidance. They were mostly written in March 2026, with one guide last changed in April. They describe a chat-assistant workflow in which a human supplies every file, runs every command, pastes every traceback, and must personally initiate every challenge or pivot. The repository's later agent-mode work records a different operating environment: agents inspect live workspaces, edit and execute code, run parallel reviews, preserve or lose state across handoffs, detect method substitution, retract hypotheses, and build evidence chains. This does **not** make the old risks disappear. It changes where the controls must sit: authorization, live-state checks, method contracts, executable discriminators, artifact provenance, and accountable release decisions.

Recommended disposition:

1. Preserve the scientific core of all four guides.
2. Correct the live numerical and technical contradictions before publication.
3. Either label the March-era observations as historical snapshots or rewrite them for agent mode.
4. Replace categorical claims about what “AI can never do” with claims about reliability, evidence, authority, and accountability.
5. Do not propagate any quantitative performance correction until its benchmark artifact has been checked.

## 2. Scope and provenance

The review covered all four files in `guides/`:

| File | Lines | Words | Last content commit |
|---|---:|---:|---|
| [`information_to_knowledge.md`](information_to_knowledge.md) | 247 | 1,676 | 2026-03-30 |
| [`lessons_ai_risks_and_mitigation.md`](lessons_ai_risks_and_mitigation.md) | 326 | 2,283 | 2026-03-29 |
| [`lessons_from_conversation.md`](lessons_from_conversation.md) | 292 | 1,842 | 2026-03-30 |
| [`lessons_human_ai_research.md`](lessons_human_ai_research.md) | 430 | 4,397 | 2026-04-16 |

The review also cross-checked the later case studies, repository entry documents, relevant git history, and current first-party documentation for agent memory and subagent capabilities. Current tools do provide persistent instruction files, automatic or assisted memory, plans, isolated subagents, and direct repository execution. Their own documentation also makes clear that memory is context rather than an enforcement mechanism. Thus the correct update is not “memory solved scientific knowledge”; it is “the old statement that systems can only retain isolated facts is obsolete, while reliable scientific dependency propagation remains unsolved.” See [Claude Code memory](https://code.claude.com/docs/en/memory), [Gemini CLI memory](https://geminicli.com/docs/tools/memory/), and [Gemini CLI subagents](https://geminicli.com/docs/core/subagents/).

No guide file was changed during this review.

## 3. Corrections to log before any rewrite

These are the highest-priority findings because they are contradictions, unsafe prescriptions, or unsupported statements presented as facts.

| Priority | Location | Finding | Recommended disposition |
|---|---|---|---|
| Critical | [`lessons_ai_risks_and_mitigation.md`, lines 63–64](lessons_ai_risks_and_mitigation.md#L63-L64); [`information_to_knowledge.md`, lines 71–75](information_to_knowledge.md#L71-L75) | The first guide still says CoupLAM has a `10–50×` matvec advantage; the later guide says that claim was corrected to about `3×` after recognizing that FEM can also use matrix-free multiplication. This is a direct failure of correction propagation. | Treat both values as provisional until the benchmark source, comparator, hardware, matrix-free assumptions, and timing definition are recovered. Then update every dependent occurrence together. Do not merely replace one number with the other on the strength of prose alone. |
| High | [`lessons_human_ai_research.md`, lines 260–264](lessons_human_ai_research.md#L260-L264) | “Complete files over incremental patches” is unsafe in a dirty or shared version-controlled workspace and can erase user or concurrent-agent work. The 500-line and two-to-three-function thresholds are arbitrary. | Default to scoped, reviewable diffs after checking branch, worktree, and ownership. Use full replacement only for an intentional rewrite of a clean or generated file. |
| High | [`lessons_human_ai_research.md`, lines 238–250](lessons_human_ai_research.md#L238-L250) | The debugging loop assumes a chat assistant: the human runs code and pastes tracebacks. This is no longer representative of repository agents. | Replace with: inspect environment and live state → reproduce → state acceptance gate → make a scoped change → rerun → inspect diff and artifacts → report uncertainty. Human approval remains necessary for consequential scope or external actions. |
| High | [`lessons_ai_risks_and_mitigation.md`, lines 166–172](lessons_ai_risks_and_mitigation.md#L166-L172) | “Methodologically correct” tests are said to miss nothing if comprehensive. A suite can test the wrong copy, share a flawed oracle, skip a guard, or omit a release path. | Say that discriminating tests support the claims they actually exercise; they do not certify untested assumptions or shared failure modes. |
| High | [`lessons_human_ai_research.md`, line 194](lessons_human_ai_research.md#L194) | A NumPy prototype is called “ground truth.” A second implementation can share the same conceptual error. | Call it a reference implementation until both paths are checked against analytical invariants, exact limits, or a genuinely disjoint benchmark. |
| High | [`lessons_human_ai_research.md`, lines 226–228](lessons_human_ai_research.md#L226-L228) | The LAMMPS ghost-force prescription is written as universal. Pair ownership depends on neighbor-list mode, `newton_pair`, hook ordering, and the force component involved; indiscriminately clearing ghost `f[]` can erase other contributions. | Scope the incident to the exact fork, call path, and configuration. Replace the universal fix with an ownership/communication audit. |
| High | [`lessons_ai_risks_and_mitigation.md`, lines 26–35](lessons_ai_risks_and_mitigation.md#L26-L35) | “SIMP does not apply to MMC” is too broad. The evidence can show that an extra `rho^3` penalty was unjustified for the project’s tested geometric-density formulation, not that SIMP/MMC hybrids or ersatz-material MMC formulations do not exist. | Preserve the causal-chain lesson but scope the scientific claim to the implementation and objective actually tested. |
| High | [`lessons_ai_risks_and_mitigation.md`, lines 318–320](lessons_ai_risks_and_mitigation.md#L318-L320) | “All examples are documented in the case studies” is not supported by the public tree. The CoupLAM/MMC, 256-case Hex8, and related incidents are not documented in the four case-study files currently present. | Add traceable records later, or say that some examples come from internal project records not included here. |
| High | [`lessons_human_ai_research.md`, lines 81–95](lessons_human_ai_research.md#L81-L95) | “No existing method” and “no existing MPM paper” are negative novelty claims without a dated search protocol or citations. | Record a reproducible literature search and cutoff date, or soften to “we had not identified.” |
| High | [`lessons_from_conversation.md`, lines 150–181](lessons_from_conversation.md#L150-L181) | “Prompt Design Dominates Model Choice” is inferred from a small qualitative prompt swap without a scoring rubric, repetitions, blinding, or uncertainty. | Report it as a project observation: prompt framing mattered in that small comparison. Review quality depends jointly on specification, context, tools, model, sources, and verification gates. |
| High | [`lessons_ai_risks_and_mitigation.md`, lines 71–75 and 122–125](lessons_ai_risks_and_mitigation.md#L71-L75) | The `~100,000`, `~10`, and `<100 papers` counts, and conclusions about private training exposure, are unsupported false precision. | Remove the numbers unless a reproducible bibliometric method exists. Describe the observed mainstream-method bias as a hypothesis, not a known training-data mechanism. |
| High | [`lessons_human_ai_research.md`, lines 383–387](lessons_human_ai_research.md#L383-L387) | “From Opus 4.5” and “tools are materially better now” are rapidly aging product claims embedded in an evergreen guide. | Either remove model branding or date-lock the observation with exact model, interface, tools, permissions, and evaluation task. |
| Medium | [`lessons_human_ai_research.md`, lines 428–429](lessons_human_ai_research.md#L428-L429) | The footer says “Last Updated: March 2026,” but git records a content change on 2026-04-16. | Correct the metadata when the guide is revised, or add a separate historical-source date and review date. |

## 4. Claims that are stale because the workflow changed

### 4.1 Memory and knowledge persistence

[`information_to_knowledge.md`](information_to_knowledge.md) has the strongest enduring conceptual structure, but its product-level claims at lines 63–69, 71–77, 88–110, 123–135, 176–180, and 201–215 need qualification.

Persistent instruction files, repository memory, auto-memory, plans, compaction summaries, and skills can now retain corrections, rationale, procedures, and failure gates. Therefore statements such as “memory stores facts but not corrections,” “skills cannot encode failure histories,” and “no current system tracks dependencies” are false when read literally and universally.

The deeper claim remains valid and should be stated more precisely:

> No system used in these projects has demonstrated automatic, reliable propagation of a scientific correction through its causal dependents across equations, code, configuration, data, figures, and manuscript claims.

That is a much stronger and more defensible lesson than a capability claim about memory products. The July wrinkle evidence supplies a practical partial architecture: live workspace state outranks remembered state, and evidence should flow through `runner → artifact → claims ledger → figure/manuscript → manifest`. It is not a complete automatic solution.

The guide should also scope the claim that the neo-Hookean `I1` term is exactly quadratic in positions and has a deformation-independent stiffness matrix. As written at lines 30–46, it can be mistaken for a universal constitutive statement. It should identify the particular position-based CoupLAM discretization and constitutive split.

### 4.2 What AI “cannot” do

Categorical inability claims appear throughout:

- [`lessons_ai_risks_and_mitigation.md`, lines 191–209 and 238–254](lessons_ai_risks_and_mitigation.md#L191-L209): AI never stops, cannot challenge a paradigm, and cannot detect method substitution.
- [`lessons_from_conversation.md`, lines 113–120 and 240–250](lessons_from_conversation.md#L113-L120): AI has no mechanism to report that it found nothing and cannot detect its own overstatement.
- [`lessons_human_ai_research.md`, lines 115–152 and 393–422](lessons_human_ai_research.md#L115-L152): error identification, validation, and pivots are assigned almost exclusively to the human.

The later wrinkle work is a direct counterexample to the capability boundary: an agent detected that a method labelled symplectic was actually using depth-FE machinery; another agent retracted a failed route and rebuilt the analytical-depth method; further agents identified source, physics, convergence, guard-scope, and release defects. Agents can also stop, ask, or escalate when explicit gates exist.

The enduring distinction is **authority**, not an exclusive capability split. Agents may inspect, hypothesize, implement, execute, critique, validate, and propose pivots. The human scientific owner remains accountable for objectives, unstated physical constraints, risk tolerance, publication claims, acceptance, and irreversible or external decisions. Self-review by either a human or an agent is not an adequate independent gate.

### 4.3 Same-thread and repeated-prompt advice

Advice to state the method in every prompt, attach the theory document every session, and keep follow-up review in the same thread is chat-era guidance. In agent mode, the stronger control is a versioned project-level method contract containing required sources, forbidden substitutions, invariants, writable scope, approval gates, and acceptance tests. The agent should identify the exact path and revision read.

Same-thread continuity can help, but it can also preserve stale assumptions, while long threads can compact away details. Isolated reviewers can be valuable. Corrections should therefore live in authoritative repository artifacts and be checked against the live workspace, not depend on conversational continuity.

## 5. Claims that need evidence or narrower wording

### 5.1 Unsupported rates, rankings, and universals

The following are useful anecdotes but not established general rates:

- the `30/40/30` reviewer-finding split in [`lessons_from_conversation.md`, lines 81–85 and 230–232](lessons_from_conversation.md#L81-L85);
- the related `30/40/20/10` split in [`lessons_human_ai_research.md`, lines 333–339](lessons_human_ai_research.md#L333-L339);
- “MPI-correct about 70% of the time” in [`lessons_human_ai_research.md`, line 230](lessons_human_ai_research.md#L230).

The two review distributions are arithmetically compatible after aggregation, but neither gives item count, inclusion rule, model/version, adjudication procedure, or uncertainty. They should be labelled as a dated internal tally with the underlying record or removed.

Likewise, “API hallucination is the #1 code bug,” “silent substitution is the most dangerous risk,” and similar rankings conflict across the guides and are not supported by a common denominator. Use “recurring” or “one of the hardest to detect” unless a defined incident dataset supports a ranking.

### 5.2 Review independence

“Ask a different AI” is neither necessary nor sufficient for independence. Different models can share sources, assumptions, prompts, equations, code paths, or oracles; same-model agents can still examine isolated failure modes. The useful unit is not a model vote but a disagreement converted into a falsifiable artifact.

For consequential claims, review should be separated along axes such as:

- theory and source fidelity;
- equation and convention audit;
- actual assembly/call path;
- numerical convergence and exact limits;
- data and figure lineage;
- shipped-path and clean-clone behavior;
- manuscript claim scope.

Every finding should be dispositioned against current source and executable evidence. Agreement does not close a claim unless implementation, artifact, and physical interpretation agree.

### 5.3 Technical incidents

Several incidents remain valuable but must not be generalized beyond their evidence:

- The eigendecomposition incident at [`lessons_human_ai_research.md`, lines 160–168](lessons_human_ai_research.md#L160-L168) correctly warns about naive eigenvector derivatives at repeated eigenvalues. It should not imply that the matrix function itself lacks a finite derivative or that Denman–Beavers/scaling-and-squaring is universal.
- FEniCSx examples at lines 268–280 should be pinned to the actual installed release. A `[VERIFY]` marker is not verification; use the locked environment, versioned official documentation, and a minimal executable API probe.
- LAMMPS examples at lines 286–303 appear to involve a custom CoupMPM fork and `atom_style mpm`. They need fork/commit/configuration provenance and must be distinguished from upstream LAMMPS behavior.
- “Never reorganize before code works” and “replace the approach entirely after three failures” are overly rigid. Repeated failure should trigger a root-cause and method-family audit while preserving the validated baseline; replacement needs evidence that the architecture, rather than a local defect, is the cause.

## 6. Per-guide disposition

### `information_to_knowledge.md` — retain and modernize

This is the strongest guide conceptually. Keep the distinctions among facts, reasons, corrections, dependencies, bounds, and evidence. Keep the warning that more context is not equivalent to reliable knowledge. Modernize the descriptions of memory, skills, compaction, and dependency tracking. Change “solvable” to “mitigable” where documentation is proposed as a solution, and change “we do not have a solution” to “we do not have a complete automatic solution.”

The speedup correction is useful evidence of the guide's thesis, but only after the underlying benchmark is recovered.

### `lessons_ai_risks_and_mitigation.md` — retain the taxonomy; correct claims

Keep the risks of plausible-but-inapplicable advice, silent method substitution, mainstream-method drift, plausible scaling errors, and debugging spirals. Keep theory-to-code mapping, distinctive-behavior tests, component signatures, numerical references, mode checks, and analytical energy checks.

Correct the CoupLAM speed claim, scope the MMC/SIMP claim, remove invented paper counts, weaken universal model rankings, and replace “what AI cannot replace” with “what the human must own.” Expand the three-layer defense to include authorization, live state, shipped-path guards, execution evidence, provenance, and release checks.

### `lessons_from_conversation.md` — historical case note or substantive reframe

Keep bounded challenge, explicit correction integration, reviewer triage, and the observation that disagreement exposes assumptions. Retain the particular escalation chronology as a case, not a universal mechanism.

Reframe the claims that permission is always required for criticism, prompt design dominates model choice, a different model has “no stake,” broad questions should not be asked, and follow-up must remain in one thread. The original comparison is a small qualitative observation, not controlled evidence for a field-wide result. Broad synthesis remains useful when the objective, sources, alternatives, uncertainty, falsification criteria, and stop condition are explicit.

### `lessons_human_ai_research.md` — substantial agent-mode update

Keep cross-field synthesis as a possible contribution, but replace “broad and balanced knowledge potentially as deep as the best literature” with “broad but uneven proposal generation that requires primary-source verification.” Keep edge-case testing, dimensional analysis, reference implementations, expected-versus-actual reporting, context with rationale, reviewer triage, and a mistake log.

Revise the chat-era debugging loop, complete-file rule, rigid three-failure rewrite rule, product-version claims, unsupported success rates, and binary human/AI diagram. Expand the mistake log to include exact model/surface/tools, repository path, branch/commit/dirty state, environment versions, command/input, artifact, affected claim, correction, guard, and open/superseded status.

The attribution reference at line 75 is **not broken**: Section 14 exists in [`large_deformation_contact.md`](../case_studies/large_deformation_contact.md#L272). It should remain unless the intended source has changed. This was explicitly rechecked because one audit pass incorrectly flagged it.

## 7. Missing agent-era layer

A future revision should add a short layer common to all four guides:

1. **Authorization and method contract:** define writable scope, required method, prohibited substitutions, external side effects, approval points, and stop gates.
2. **Live state before memory:** record repository path, branch, HEAD, dirty state, active process, artifact location, and current accepted claim. Memory and summaries are aids, not authority.
3. **Method identity at the assembly loop:** labels, filenames, and function names do not establish the method. Trace the equations into the executed assembly/call path and add a discriminator that an impostor method cannot pass.
4. **Execution-state honesty:** launched, still running, completed, validated, and published are different states. Preserve commands, logs, return codes, checkpoints, and artifact hashes.
5. **Test the shipped copy:** a guard that imports a mirror, silently skips, or is absent from a clean clone cannot protect the publication artifact. Treat every skip as a scientific verification decision.
6. **Artifact graph:** connect source/configuration to runner, raw artifact, claims ledger, figure/table, manuscript statement, and manifest. A change upstream must invalidate or recheck its dependents.
7. **Independence by failure mode:** diversify equations, implementations, exact limits, data paths, and review roles—not merely model names.
8. **Retractions as evidence:** preserve failed hypotheses, why they failed, what changed, and which downstream claims were withdrawn.
9. **Release audit:** reproduce from a clean clone, inspect full git history and tracked assets, remove private paths or internal identifiers, and verify that public instructions generate the claimed artifacts.
10. **Authority split:** agents can contribute throughout the loop; the human scientific owner retains responsibility for scope, acceptance, publication, and consequential decisions.

## 8. Repository-wide propagation to check later

No files outside this note were edited, but a future revision cannot stop at `guides/`:

- `README.md` repeats the unsupported training-data/paper-count explanation.
- `START_HERE.md` says reviewer convergence is the goal and makes categorical claims that AI cannot catch certain failures; the later case studies show that consensus is not proof and that agents can catch some of them.
- The case-study inventory and evidence links should be updated only after the new wrinkle case study is committed and its public-facing provenance is settled.
- A single claims ledger should identify the authoritative value and evidence for quantitative statements such as the CoupLAM speed comparison.

## 9. Final assessment

The guides should **not** be deleted. Their best material is unusually concrete and remains useful. The update should preserve the recorded incidents while separating three layers that are currently mixed together:

1. durable scientific and software-engineering principles;
2. dated observations about particular models, interfaces, and projects;
3. current operating guidance for autonomous repository agents.

The most important correction is conceptual: the March guides often divide work by capability—what humans can do versus what AI cannot do. The later evidence supports a more precise division by **evidence and authority**—what an agent is permitted to do, what artifact is sufficient to close a claim, and who is accountable for accepting and publishing it.

---

**Reviewed by:** Codex (GPT-5)

**Date:** 2026-07-20 (UTC)
