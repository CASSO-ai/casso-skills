# L1 review rubric: casso-skills-blueprint-branch-validate

Use this list against the **PASS/FAIL report**, the **disposable integrated blueprint tree**, and named **commands and outputs**. Pass each line or record fail with evidence (sha, command, path, quoted finding).

1. **Integrated candidate tree** — Blueprint branch integrated onto current blueprint main in a disposable workspace; resulting tree identity (sha or equivalent) recorded; all checks run on that tree vs merged main (SKILL.md Process §1).
2. **Proof commands named** — Every mechanical checker and document roots in scope (functional specs, data model, design docs) named (SKILL.md Process §2).
3. **Mechanical checks** — Scripted checks run fresh: every spec unit has spec ID; no duplicate IDs; every in-set reference resolves; each check records name, command, exit status, failure list (SKILL.md Process §3).
4. **Project owner four checks** — Judgment review documents **contradictions**, **omissions**, **extras not clearly defined**, **structural gaps** (including missing spec ID, duplicate IDs, unresolved references the mechanics did not already catch); each blocking finding cites path/unit/id, why merge is blocked, remedy (SKILL.md Process §4).
5. **Fresh evidence** — Identify → run → read → verify for proving commands; no PASS from prior run or confidence alone (SKILL.md Process §5).
6. **Verdict** — PASS/FAIL with candidate-tree identity, mechanical table, blocking vs known-accepted; strengths after proofs; two-way gap lists rebuilt immediately before verdict (SKILL.md Process §6, Clean-room §2).
7. **Clean-room** — Boolean validation claims; blueprint reconstructability/change-spec-first/domain-truth items reflected in report where the skill requires them (SKILL.md Clean-room §1–5).
8. **Reviewer / analyze / oracle** — Requirements checklist not silently self-approved; read-only cross-artifact analyze run; your project's strict mechanical validation command (or equivalent) recorded (SKILL.md Reviewer-owned checklist, Read-only cross-artifact analyze, External mechanical validator).
9. **Terminology** — Delivered narrative uses **work item** for pipeline activities (SKILL.md Preconditions).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. PASS/FAIL report, mechanical table, or judged-important validation artefacts are not all committed.
2. Check command names, exit status, or candidate identity appear without log or command output for that tree.
3. Structural gap is claimed closed while duplicate IDs, unresolved references, or missing spec IDs would still pass the mechanical table unchanged.
4. Judgment review or document scope goes beyond the branch and merged-main comparison the brief names.
5. Junk unrelated to the report is committed with it.
6. Four-check findings, gap lists, Clean-room items, or the mechanical validation command line is missing with no honest known-accepted statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: integrated tree is not onto current blueprint main, evidence is reused from a prior run without fresh identify-run-read-verify, or checklist boxes are self-approved.
8. It stopped early or looped without reporting why; or, in this activity: two-way gap lists or mechanical reruns stop mid pass without honest blocker reporting.
9. Verdict and proof set are incomplete so another run must finish before merge.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
