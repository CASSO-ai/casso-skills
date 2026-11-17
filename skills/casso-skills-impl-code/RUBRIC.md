# L1 review rubric: casso-skills-impl-code

Use this list against **production code**, **test results**, and the worker’s report. Pass each line or record fail with evidence (test name, runner output reference, file:line).

1. **Scope** — Implementation is limited to assigned C-SPEC units from the plan and authorized spec; no extra scope beyond the assigned work item (SKILL.md Preconditions; Common mistakes).
2. **GREEN evidence** — Named tests pass in the project test runner; any GREEN/completion claim is backed by **fresh** runner output (or cited artefact) showing those tests pass (SKILL.md Overview; Process §1; Review checklist).
3. **Verification gate** — Before claiming GREEN/completion: proving command identified → run fresh → output read → named tests verified pass (SKILL.md Process §1).
4. **Bugfixes** — Defect fixes reproduce with a failing test first (or cite impl-tests proof), RED then GREEN on the same named test, one change at a time (SKILL.md Process §2; Review checklist).
5. **Failed greening** — On failure: root cause before more edits; no symptom-only stacks; after three failed fix attempts, stop and escalate (SKILL.md Process §3; Common mistakes).
6. **Refactor** — Refactors stay green; only code touched is improved; no restructure outside the plan unless reported; tests use condition-based waits (SKILL.md Process §4; Common mistakes).
7. **Product rules** — No silent error swallows; user-facing text via project helpers; diagnostics via tracing/logging; errors include remedy; new domain errors update exhaustive API mappings; product identity uses project branded name (SKILL.md Process §5).
8. **Traceability** — Requirement-traceability self-review against plan + spec before submit (SKILL.md Process §6; Review checklist).
9. **Commit report** — Only the worker’s paths committed (never whole-tree blind stage); **local** commit sha from `git rev-parse` reported; no false push claims (SKILL.md Process §7; Common mistakes; Review checklist).
10. **Converge** — Gap-finding after evidence is append-only (add tasks/scenarios; no silent delete/edit to clear gaps) (SKILL.md Converge append-only; Review checklist).
11. **Worker commit** — Uncommitted judged-important changes count as incomplete and lower usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Judged-important implementation paths are not all committed.
2. A GREEN or completion claim appears without fresh runner output or cited artefact showing the named tests pass.
3. No proof that breaking the implementation turns the named tests red where the skill requires RED then GREEN or the verification gate.
4. Code or scope goes beyond the assigned C-SPEC units and work item, or adds restructuring or features the plan did not call for.
5. The commit includes build output, scratch files, or other junk not part of the implementation.
6. Part of the brief or assigned work item is skipped with no honest limit statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: silent error handling, logging, remedy, API mapping, or naming rules from Process §5 are broken, or another standing project rule is violated.
8. It stopped early or looped without reporting why; or, in this activity: greening fails repeatedly while the worker stacks blind fixes past the stop rule, patches symptoms only, or stops without escalate and honest reporting.
9. Implementation or traceability self-review is incomplete enough that another run is required to finish the work item.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
