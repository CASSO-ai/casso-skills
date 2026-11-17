# L1 review rubric: casso-skills-plan-code

Use this list against the **delivered plan file(s)** at the path named on the brief and the worker’s report. Pass each line or record fail with evidence (path, excerpt, or work-item id).

1. **Trace to spec** — Every C-SPEC `[CHECK]` in scope maps to at least one plan work item (SKILL.md Review checklist).
2. **Explicit files** — File paths to create or modify are explicit, not vague (“update the API”) (SKILL.md Review checklist; Common mistakes).
3. **Work items** — Plan prose uses **work item** for decomposable units; each work item is one problem domain with ordered, alone-verifiable actions and exact runner commands where known (SKILL.md Process §3; Review checklist).
4. **Interfaces** — Each work item states **Consumes** / **Produces** with exact signatures neighbors rely on (SKILL.md Process §3).
5. **Code-shaped work** — Where a work item changes code, the plan shows intended code or equivalent exact patch shape (SKILL.md Process §3; Review checklist).
6. **Self-contained items** — Each work item stands alone for a confined agent (scope, goal, constraints, expected report shape); fixes paste failing names or error text and state hard constraints (SKILL.md Process §3; Review checklist).
7. **Wire obligations** — If the plan touches remote-call / server-response code, `## Wire contract obligations` lists endpoints/fields and cites `casso-skills-audit-code` [TBD (In Dev)] Phase 6 at impl audit (SKILL.md Process §4; Review checklist).
8. **Removals** — If the spec removes behavior, every removal location is enumerated (SKILL.md Process §5).
9. **Type consistency** — Names/types agree across work items after drafting (SKILL.md Process §6; Review checklist).
10. **Structure** — Vertical slices, phases (Setup → Foundational → per-story → Polish), sizing XS–XL with XL broken down, checkpoints every 2–3 tasks; existing incomplete plan not overwritten without asking (SKILL.md Vertical feature slices; Phase template; Sizing; Never overwrite).
11. **No invented scope** — Plan does not add requirements the spec never required (SKILL.md Common mistakes; Review checklist).
12. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Judged-important plan changes are not all committed on the task branch.
2. A statement about file paths, interfaces, runner commands, or traceability is not backed by the delivered plan file or other primary evidence.
3. Not applicable to this activity.
4. The plan adds work items, files, or requirements outside the spec and brief scope, or omits enumerations and wire obligations the skill requires when triggered.
5. The commit includes build artefacts, scratch files, or other noise not part of the plan deliverable.
6. Part of the brief or a required plan element is missing with no honest gap or limit statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: an existing incomplete plan is overwritten without the stop-and-ask rule, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: work on a work item stops or loops without reporting limit or cause while the skill expects ordered alone-verifiable actions.
9. The plan leaves work items or traceability incomplete such that another run is needed to finish the slice.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
