# L1 review rubric: casso-skills-blueprint-release-publish

Use this list against the **release record**, the **blueprint-release-validate report** it cites, the **published copy** and the **downstream notice**. Pass each line or record fail with evidence (sha, tool output, unit ids).

1. **Preconditions** — blueprint-release-validate PASS cited with its report path and pinned identity (SKILL.md Preconditions).
2. **Approval gate** — Explicit approval to publish recorded with who, when and the candidate identity (SKILL.md Process §1).
3. **Identity match** — Published identity equals the validated identity; re-validation cited if anything changed (SKILL.md Process §2).
4. **Change summary** — Every unit added, changed or removed since the previous official version is listed by id with its merge record (SKILL.md Process §3).
5. **Publish** — The official pointer moved via the project's command; earlier official versions are intact (SKILL.md Process §4).
6. **Read-back** — Done on the published copy with command output: pointer resolves to the candidate, index opens, references resolve; anything that could not run is recorded as blocked (SKILL.md Process §5).
7. **Downstream notice** — Open work built on the previous version that cites a changed unit is listed and marked needs re-check, or the notice states none exist and how that was searched (SKILL.md Process §6).
8. **Release record** — All fields recorded atomically, via the project command or a stated manual procedure (SKILL.md Process §7).
9. **Worker commit** — The worker's judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Published without approval, or published an identity other than the validated one.
2. The read-back used the local tree instead of the published copy, or a blocked check was reported as passed.
3. An earlier official version was rewritten or removed.
4. The change summary misses a changed unit.
5. The downstream notice is missing, or misses open work that cites a changed unit.
6. Junk unrelated to the release evidence is committed with the record.
7. It broke a standing rule: environment variables, hand-rolled git, or another standing project rule.
8. It stopped early or looped without reporting why; or release fields stay incomplete so another run must finish the record.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "65: items 2 and 5, read back from the local tree and the notice skipped two open plans").
