# L1 review rubric: casso-skills-impl-tests

Use this list against **test code**, **runner output**, the **validated test plan on the brief**, and the worker’s report. Pass each line or record fail with evidence (test name, todo id, path).

1. **Workspace** — Work stayed in the assigned workspace; main working copy untouched (SKILL.md Preconditions).
2. **Plan todos** — Each plan Testing row tracked as a todo; marked complete only after RED failure is read (SKILL.md Process §1; Review checklist).
3. **RED first** — For each scenario, minimal failing test exists and is run through the project test runner until it fails for the **expected** reason (SKILL.md Process §2; Review checklist).
4. **Test quality** — Tests are minimal, behaviorally named to the plan row, show the intended API; assertions target real behavior (not mock existence) unless the plan names doubles (SKILL.md Process §2; Review checklist).
5. **Production boundary** — No production code except test code and test-only helpers; premature production code deleted and RED restarted if it appeared (SKILL.md Overview; Process §4; Common mistakes).
6. **Failure mode** — Failure verified as missing behavior, not typo/filter error; letter-of RED-first honored (SKILL.md Process §3).
7. **Mocks** — No test-only methods on production types; mocks mirror full real schema when required; side effect named before mocking (SKILL.md Process §2; Common mistakes).
8. **Hard cases** — Hard-to-test scenarios simplified or reported DONE_WITH_CONCERNS, not papered over with heavy mocks (SKILL.md Process §2; Common mistakes).
9. **Traceability** — Each new test maps to a plan Testing row and a C-SPEC `[CHECK]` (SKILL.md Process §5).
10. **Limits** — Limits stated if push or test runner was blocked (SKILL.md Review checklist).
11. **Converge** — Gap-finding is append-only; no silent delete/edit to clear gaps (SKILL.md Converge append-only; Review checklist).
12. **Required runs, not skips** — Required tests fail when prerequisites are missing; report includes run and skip counts for required groups (SKILL.md Process §2).
13. **Structured error assertions** — Failures asserted via type, code, or constraint fields — not error message substring match (SKILL.md Process §2).
14. **No discarded checks** — Every verification call feeds an assertion; no blank-identifier or ignored results on checks (SKILL.md Process §2).
15. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Judged-important test changes are not all committed.
2. RED completion or runner results are claimed without readable output tied to the named test and scenario.
3. No evidence the failure is missing behavior for the expected reason, or letter-of RED-first is violated so the test would not prove the scenario.
4. Production code appears outside test code and allowed test-only helpers, or scope grows beyond the plan Testing rows.
5. The commit includes build artefacts, scratch files, or other junk.
6. A plan Testing row, todo discipline, or brief requirement is skipped with no honest limit statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: assigned workspace or test-runner rules are broken, or another standing project rule is violated.
8. It stopped early or looped without reporting why; or, in this activity: iteration stops or repeats without explaining limit or cause while RED or failure-mode rules are unfinished.
9. Tests or todos are left incomplete so another run is needed to finish the work item.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
