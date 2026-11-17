# L1 review rubric: casso-skills-cr

Use this list against the **Change Request artefact** at the brief path and the **commit** containing it. Pass each line or record fail with evidence (path, section, quoted text).

1. **Frame** — WHAT HAPPENS, WHY IT MATTERS, THE FIX in problem–solution form; mechanism kept under evidence (SKILL.md Process §1).
2. **Scope before detail** — Multi-subsystem request flagged for project owner decomposition before detailed acceptance (SKILL.md Process §2).
3. **Acceptance** — Observable acceptance checks named; no requirements the project owner did not state (SKILL.md Process §3).
4. **Intake boundary** — CR at brief path when given; committed per VCS policy; no unapproved edits to the live spec (SKILL.md Process §4).
5. **Self-review** — No TBD/TODO/vague acceptance/contradiction left; fixed or escalated (SKILL.md Process §5).
6. **Handoff** — Open contradictions/ambiguities listed for project owner, not resolved unilaterally; at most one clarifying question per project owner turn (SKILL.md Process §6).
7. **Requirement deltas** — When living specs touched: ADDED/MODIFIED/REMOVED delta shape per skill; no edits to the live spec here (SKILL.md Process §7).
8. **Ops tables** — When deployments/process/multi-stakeholder: Rollback, Approvals, Communication tables with specific rows (SKILL.md Process §8).
9. **Mid-stream correction** — Significant late change produces sprint change proposal across artifacts before rewrites (SKILL.md Process §9).
10. **Terminology** — **work item** used for pipeline activities (SKILL.md Preconditions).
11. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. CR artefact or other judged-important paths are not committed at the brief path per VCS policy.
2. WHAT, WHY, THE FIX, acceptance, or evidence pointers are asserted without matching text in the delivered CR.
3. Not applicable to this activity.
4. Acceptance or detail expands beyond project-owner-stated requirements, or multi-subsystem detail ships before decomposition is flagged.
5. Junk unrelated to the CR is committed with it.
6. Ops tables, deltas, contradiction list, or brief elements are missing with no honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: the live spec is edited here, or deltas replace the project owner-authorized promotion paths.
8. It stopped early or looped without reporting why; or, in this activity: multiple unanswered clarifying questions land in one turn, or contradictions are cleared without listing them for the project owner.
9. A significant late change lands without the sprint change proposal Process §9 requires before downstream rewrites.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
