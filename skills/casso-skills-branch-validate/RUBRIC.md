# L1 review rubric: casso-skills-branch-validate

Use this list against the **PASS/FAIL report**, **candidate merged-tree identity**, **test-runner logs** (suite/pass counts, run ids), and **mutation evidence**. Pass each line or record fail with evidence (test name, log excerpt, sha).

1. **Candidate tree** — Branch integrated onto current main in disposable workspace; tree identity recorded; proofs run on that tree (SKILL.md Process §1).
2. **Proof commands named** — Test-runner entry, exact new test names, regression scope named (SKILL.md Process §2).
3. **Full regression** — Full regression (or brief scope) through project test runner; one log per run; run integer id when assigned; poll loop with poll errors reported as finished (SKILL.md Process §3).
4. **New tests by name** — Each new test executed by name with asserted pass counts for the named set (SKILL.md Process §4).
5. **Mutations** — Per new test: temporary mutation → RED → revert clean; mutation breaks two independent places; compiler error count if mutation does not compile (SKILL.md Process §5).
6. **Touched-surface regression** — Branch-touched surfaces checked vs main with named proofs or scoped suites as project defines (SKILL.md Process §6).
7. **External oracle** — At least one check that can disagree with code (lint, diff-vs-spec, etc.) (SKILL.md Process §7).
8. **Verdict** — PASS/FAIL with candidate identity, suite count, pass count, named mutations, blocking vs known-accepted gaps; strengths after proofs; blocking findings cite file:line or test name, why, remedy (SKILL.md Process §8).
9. **Five-axis review** — Correctness, readability, architecture, security, performance; diff sizing ~100 lines when splitting (SKILL.md Five-axis review).
10. **Terminology** — **work item** used for pipeline activities (SKILL.md Review checklist).
11. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. PASS/FAIL report, logs, or other judged-important validation artefacts are not all committed.
2. Suite count, pass count, candidate identity, or oracle result appears without runner logs or command output for that tree.
3. A new test is claimed proven without mutation RED and clean revert matched by name, or without compiler error count when the mutation fails to compile.
4. Regression scope, mutations, or checks go beyond the brief and project's defined blast radius for this branch.
5. Junk unrelated to the report is committed with it.
6. A brief-required proof, gap category, or verdict element is missing with no honest known-accepted or blocked statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: the candidate tree is not integrated onto current main, full regression is skipped where required, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: polling, failures, or mutations are abandoned without the finished reporting the skill expects.
9. Verdict and proof set are incomplete so another run must finish before merge.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
