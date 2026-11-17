# L1 review rubric: casso-skills-blueprint-release-validate

Use this list against the **PASS/FAIL report**, the **pinned merged-blueprint candidate sha**, and **mechanical check outputs** on that exact tree. Pass each line or record fail with evidence (sha, command, failing item list).

1. **Pin sha** — Exact merged-blueprint tree identity recorded; every mechanical result cites that sha; restart if tree moves (SKILL.md Process §1).
2. **Rerun mechanics (no reuse)** — All blueprint structural checks rerun on that tree — spec ID on every unit; no duplicate spec IDs; every in-set reference resolves — with name, command/script, exit status, failures (path + id + reason); no reuse of branch-validate evidence for a different sha (SKILL.md Process §2).
3. **Fresh evidence** — Identify → run → read → verify; no PASS from confidence or prior run (SKILL.md Process §2).
4. **Verdict** — PASS/FAIL names candidate sha, mechanical table, known gaps; any FAIL refuses release and names each failing item — blocks `casso-skills-blueprint-release-publish` until fixed or false alarm accepted (SKILL.md Process §3).
5. **Conformance scorecard** — Required rows gate release; no profile waiver marking required optional; evidence per row or unknown (SKILL.md Conformance scorecard).
6. **Per-artifact inventory** — Each published artifact has its own validation command run and recorded; job success not equated to artifact pass (SKILL.md Per-artifact validation inventory).
7. **blocked ≠ passed** — Missing checks/credentials/infra recorded as blocked, not passed (SKILL.md blocked ≠ passed).
8. **Terminology** — Delivered narrative uses **work item** where pipeline activities are discussed (SKILL.md Review checklist).
9. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. PASS/FAIL report, scorecard, or inventory rows are not all committed.
2. Candidate sha or mechanical exit status appears without command output and failure list tied to that sha.
3. A structural rule is reported clean while duplicate IDs or unresolved references would still fail the same rerun commands.
4. Validation reuses branch-validate logs for a different sha or expands beyond the merged blueprint tree on the brief.
5. Junk unrelated to the report is committed with it.
6. Conformance row, per-artifact row, or blocked-vs-passed treatment is missing with no honest unknown or blocked statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: mechanics are skipped where Process §2 requires the full rerun set on this tree.
8. It stopped early or looped without reporting why; or, in this activity: tree moves without restart while results still cite the old identity.
9. Verdict and named failing items remain incomplete so another run must finish before release.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
