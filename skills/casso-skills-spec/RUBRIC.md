# L1 review rubric: casso-skills-spec

Use this list against the **delivered spec proposal** (files under the project proposed-spec area) and the worker’s report. Pass each line or record fail with evidence (path, line range, or quoted text).

1. **Minted IDs** — Every new unit id is unique: obtained with `casso rex get spec id` or recorded in the project's id ledger file; no invented, reused, or renumbered ids (SKILL.md Process §1).
2. **Unit shape** — Each unit has `[C-SPEC-<PROJECT>-<n>]` on its own line, the requirement, and **exactly one** `[CHECK]`; context lines use only `[WHY]` / `[WHY-NOT]` / `[COUNTEREXAMPLE]` / `[EXAMPLE]` / `[NOTE]` at line start (SKILL.md Process §3).
3. **Proposed only** — Draft changes live under the proposed area; the live spec tree was not treated as done without project owner authorization (SKILL.md Process §4).
4. **Committed proposal** — Proposed-spec drafts are committed per project VCS policy so audit-spec [TBD (In Dev)] can see them (SKILL.md Process §4).
5. **No invented scope** — Ambiguities are asked; contradictions are surfaced, not auto-resolved; gaps the project owner never ruled are listed, not filled with new units (SKILL.md Process §5).
6. **Self-review clean** — No TBD/TODO/incomplete units or vague `[CHECK]` text left unaddressed; new units do not contradict each other or cited authorized rulings (SKILL.md Process §6).
7. **Non-negotiables** — Project constitution / non-negotiables were consulted before hardening, or the gap is recorded for the project owner (SKILL.md Process §7).
8. **Clarify loop** — If material ambiguity remained, at most five targeted questions total, one per project owner turn, answers encoded into units (SKILL.md Process §8).
9. **Constraints bar** — Proposed requirements do not silently weaken the project constraints / quality-bar document; checks name cost and where they run (SKILL.md Process §9).
10. **Review checklist** — SKILL.md “Review checklist” items are satisfied (ids, single CHECK, markers, scope flags, proposed-only, committed drafts, self-review, gaps, non-negotiables, clarify loop, constraints) (SKILL.md Review checklist).
11. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Proposed-spec changes the skill treats as judged-important are not all committed per project VCS policy.
2. A claim about minted ids, unit shape, or repository state appears without path, command output, or other primary evidence in the delivered artefacts.
3. Not applicable to this activity.
4. New units or resolutions go beyond project-owner-ruled scope, or contradictions and gaps are handled by invention instead of surfacing or asking.
5. The commit includes material that is not part of the proposed-spec draft, such as build artefacts or scratch files.
6. A required Process element is missing from the delivered proposal or report with no honest limit or gap statement, such as skipped non-negotiables consultation, clarify loop, or listed project owner gaps.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: the live spec tree is edited without authorization, proposed requirements silently weaken the project constraints or quality bar, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: material ambiguity remains while the clarify loop rules are abandoned without an honest stop or limit statement.
9. The delivered proposal still needs another run to complete units, self-review, or handoff shape the skill requires.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
