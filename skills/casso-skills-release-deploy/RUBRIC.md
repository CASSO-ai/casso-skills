# L1 review rubric: casso-skills-release-deploy

Use this list against **release records**, **deploy logs**, **published-artefact smoke**, and **sha identity** evidence. Pass each line or record fail with evidence (sha, command output, table row).

1. **Project owner gate** — Explicit project owner approval naming candidate sha (SKILL.md Process §1).
2. **Identity match** — Deployed tree equals `casso-skills-release-validate` PASS sha; stop if rebuilt/retagged (SKILL.md Process §2).
3. **Release record** — Environment, version pointer, approver, deploying work item, deployed sha appended via CLI or stated manual procedure (SKILL.md Process §3).
4. **Execute deploy** — Project release script only when brief names scope; limits stated honestly (SKILL.md Process §4).
5. **Quick live check** — Smoke/health on **published artefact**, not branch/scratch; pass/fail and limits recorded (SKILL.md Process §5).
6. **Skills bundle** — When in scope: installed skill folder names match skill table names (SKILL.md Process §6).
7. **Post-release table** — Per-artifact: producing job, validation/smoke, status passed/failed/blocked; version-bump PR state explicit; missing infra = blocked not passed (SKILL.md Process §7).
8. **Ship lifecycle** — Pre-launch, monitor/rollback readiness, clear success signal — not only pipeline green (SKILL.md Process §8).
9. **Terminology** — **work item** for pipeline activities (SKILL.md Review checklist).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Release record fields or other judged-important deploy artefacts are not all committed per project policy.
2. project owner approval, deployed sha match to release-validate PASS, smoke result, or post-release table rows are claimed without evidence in the delivered logs or records.
3. Not applicable to this activity.
4. Deploy commands or record fields go beyond the brief scope, or the deployed tree is not the release-validate PASS identity.
5. Build artefacts, scratch files, or other junk are committed as part of the deliverable.
6. A brief-required record row, smoke check, ship lifecycle element, or skills-bundle check is missing with no honest blocked or limit statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: deploy proceeds without project owner approval, without matching the release-validate PASS sha, or breaks another standing project rule.
8. It stopped early or looped without reporting why; or, in this activity: deploy or recording stops mid flow with no honest limit or cause statement.
9. The release event and table remain incomplete so another run must finish the deploy handoff.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
