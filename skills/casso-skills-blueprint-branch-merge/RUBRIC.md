# L1 review rubric: casso-skills-blueprint-branch-merge

Use this list against the **merge record**, the **merge commit**, the **blueprint-branch-validate report** it cites, and the **downstream impact list**. Pass each line or record fail with evidence (sha, tool output, commit message, unit ids).

1. **Preconditions** — blueprint-branch-validate PASS cited with its report path and validated tree identity (SKILL.md Preconditions).
2. **Merges since validation** — Blueprint merges that landed after the validation run are listed; if any, a fresh validation run is cited for the new tree (SKILL.md Process §1).
3. **Identity match** — Merged tree equals the validated tree, or a byte-identical successor; no post-validation edits (SKILL.md Process §2).
4. **Changed units** — Every added, changed and removed spec unit is listed by id (SKILL.md Process §3).
5. **Content approval** — The requirements owner's approval of the content is recorded with who and when; no agent approved its own text (SKILL.md Process §3).
6. **Supersession and ids** — No unit replaces another without an explicit statement naming it; no removed id is reused (SKILL.md Process §3).
7. **Structure re-check** — Id presence, duplicate-id and reference checks re-run on the merged tree, each with command and exit status (SKILL.md Process §4).
8. **Downstream impact list** — Every artefact citing a changed unit is listed and marked needs re-check, or the list states that none exist and how that was searched (SKILL.md Process §5).
9. **Merge record** — Timestamp, merging work identity, content approver, sha, changed-unit list and impact list recorded atomically, via the project command or a stated manual procedure (SKILL.md Process §6).
10. **Commit message** — Carries report path, validated identity, changed unit ids, approver, impact list or its path, known gaps (SKILL.md Process §7).
11. **Worker commit** — The worker's judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. The merge went ahead without the requirements owner's approval of the content, or an agent approved its own text.
2. The merge used a validation PASS that predates another blueprint merge.
3. A changed unit is missing from the changed-unit list, or a removed id was reused.
4. The downstream impact list is missing, or misses an artefact that cites a changed unit.
5. Structure re-check results are claimed without command output for the merged tree.
6. Code merge criteria (test counts, mutation proofs) were offered in place of the blueprint checks.
7. Junk unrelated to the merge evidence is committed with the record.
8. It broke a standing rule: environment variables, hand-rolled git, or another standing project rule.
9. It stopped early or looped without reporting why; or merge fields stay incomplete so another run must finish the record.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "60: items 2 and 4, a blueprint merged after validation was not checked and the impact list skipped the test plan").
