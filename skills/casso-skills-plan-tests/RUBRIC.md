# L1 review rubric: casso-skills-plan-tests

Use this list against the **test plan artefact** (Testing tables / path named on brief) and **named test proofs**. Pass each line or record fail with evidence (scenario row, test name, runner command).

1. **Preconditions** — Code plan audited; spec units provide single `[CHECK]` per test obligation (SKILL.md Preconditions).
2. **Test files first** — Test files to create/modify listed before scenario decomposition (SKILL.md Process §1).
3. **Checks → scenarios** — Each `[CHECK]` has ≥1 When/Expected scenario; one behavior per scenario; Expected asserts observable product behavior; runner invocation + pass/fail signal per scenario; optional skeleton embedded (SKILL.md Process §2).
4. **Negative cases** — Where spec says "must NOT", scenarios fail if forbidden behavior appears (SKILL.md Process §3).
5. **Named proofs** — Exact test names or runner script invocations named (SKILL.md Process §4).
6. **Authoritative tables** — Testing tables stable for downstream copy; path stated if sibling/section (SKILL.md Process §5–6).
7. **High-stakes** — CLAIM→EXTRACT→DOUBT→RECONCILE when applicable (SKILL.md Doubt-driven in-flight review).
8. **Converge** — Post-implement gaps appended only, not silent rewrite (SKILL.md Converge append-only).
9. **Review axes** — Standards and Spec axes both considered (SKILL.md Review on two axes).
10. **Adversarial** — Adversarial stress-test before locking high-stakes plan (SKILL.md Adversarial plan stress-test).
11. **Required runs, not skips** — Required tests and integration groups are named; pass/fail signals include run and skip counts; missing prerequisites fail or mark required group not run (SKILL.md Process §4b).
12. **Structured error expectations** — Failure scenarios name structured outcomes (type, code, constraint field), not error message substrings (SKILL.md Process §2).
13. **No decorative lookups** — Every helper or query in the skeleton ties to an Expected assertion (SKILL.md Process §2).
14. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Test plan file or judged-important table sections are not all committed.
2. CHECK-to-scenario mapping or named proof is claimed without the Testing table rows and invocations that show them.
3. A forbidden-behavior row is missing where the spec forbids behavior, or a scenario cannot fail when the product violates Expected.
4. Scenarios, proofs, or files appear outside the brief scope or invent tests the spec never required.
5. Scratch tables or junk are committed as if authoritative.
6. Runner invocation, pass/fail signal, negative row, or brief placement is missing with no honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: converge rewrites locked tables silently, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: high-stakes or adversarial passes are skipped where applicable without recording limit or cause.
9. Testing tables or gap handling remain incomplete so another run must finish the test plan work item.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
