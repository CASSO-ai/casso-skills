---
name: casso-skills-impl-tests
description: Use when implementing tests before production code — ATDD; write failing proofs first and stop before greening with product code
---

# Implement Tests (casso-skills-impl-tests)

## Overview

Implement the tests declared in the validated test plan **before** production code. The tests define done.

**Iron law:** No production code changes in this work item except test code and test-only helpers.

RED and GREEN are separate work items: complete failing tests in casso-skills-impl-tests before production implementation in casso-skills-impl-code; do not collapse both into one continuous session.

**Method sources:** test-driven development (RED before GREEN, verify failure modes, refactor stay-green)

## Preconditions

- Test plan on the brief, and its review scored 100. (Once `casso-skills-audit-plans` [TBD (In Dev)] ships, its PASS is required instead.)
- Stay in the assigned workspace; do not touch the main working copy.

## Process

### 1. Track plan rows as todos

Track each plan Testing row as a todo; mark in progress then complete only after RED is read.

### 2. RED — failing test first

For each scenario, write the minimal failing test and run it through **the project's test runner** until it fails for the expected reason.

A good test is minimal (one behavior), has a clear behavioral name matching the plan row, and shows the intended API.

Assert real behavior; never assert that a mock exists. Prefer real dependencies unless the plan names a double.

Do not add test-only methods to production types; keep helpers under test utilities.

Before mocking, name the side effect you are avoiding; if unsure, run against real impl first.

When a mock response is required, mirror the full real schema, not only fields this test reads.

If the scenario is hard to test, simplify the interface or report DONE_WITH_CONCERNS — do not paper over with heavy mocks.

While iterating RED, run the focused test for the scenario; reserve full suite for once before handoff if the brief requires.

When the brief requires it, prove RED against the integration base (named test fails or filters to zero on the default branch).

Required tests: when a prerequisite is missing, fail the test or the required group (for example `t.Fatal` or an explicit not-run marker the runner treats as failure) — never `skip` (or equivalent) for a test the plan marks required, which lets the suite stay green with zero assertions run.

Assert failures using structured error fields (type, code, constraint name) from the error value or database driver — never `Contains` on `.Error()` text alone.

Every query, helper call, or existence check must feed an assertion. Remove dead calls; assigning a check result to `_` or ignoring it is a defect.

### 3. Verify failure mode

Confirm the failure is the missing behavior, not a typo or wrong filter.

Violating the letter of RED-first is violating the spirit — greening with product code here is a defect even if "temporary."

If production code was written early in this work item, delete it and restart from the failing test.

### 4. Stop at test scope

Do not implement production code to green the tests here — that is `casso-skills-impl-code`.

### 5. Self-review traceability

Map each new test to a plan Testing row and C-SPEC `[CHECK]`.

### Doubt-driven in-flight review (high-stakes)

For high-stakes decisions in this work item, run **CLAIM → EXTRACT → DOUBT → RECONCILE**:

1. **CLAIM** — state the claim and why it matters
2. **EXTRACT** — isolate the smallest reviewable artifact/contract, stripped of surrounding reasoning
3. **DOUBT** — adversarial review (fresh context when available)
4. **RECONCILE** — classify every finding against the artifact text; fix or escalate

### Converge append-only

After implementation evidence exists, gap-finding is **append-only**: add gap tasks / scenarios; do not edit or delete existing implementation to "make the report look clean" inside a converge pass. Re-run implement/tests work items to clear appended gaps.

### Review on two axes

When reviewing plans or code under this skill, evaluate in parallel:

- **Standards** — repo rules, naming, engineering conventions
- **Spec** — originating CR/spec/PRD acceptance

A change can pass one axis and fail the other; report both.

### Adversarial plan stress-test

Before locking a plan (or a high-stakes test/code approach), run a short adversarial interview that attacks assumptions, failure modes, and missing acceptance. Stop when remaining questions are cosmetic. Do not treat polite agreement as confirmation.

## Common mistakes

- Greening tests with product code inside this work item (letter or spirit).
- Leaving premature production code instead of deleting it and restarting from RED.
- Claiming RED without reading the failure.
- Mismatched names vs the test plan.
- Asserting that a mock exists instead of real behavior.
- Adding test-only methods onto production types.
- Mocking without naming the side effect being avoided.
- Incomplete mock schemas that only stub fields this test reads.
- Papering over a hard-to-test interface with heavy mocks instead of simplifying or reporting concerns.
- Running the full suite on every RED iteration instead of the focused scenario test.
- Skipping required tests when setup is missing so the suite reports success with no runs.
- Matching `.Error()` substrings instead of structured error or constraint fields.
- `_ =` or ignored results on calls that look like verification.

## Review checklist

- [ ] Each plan Testing row tracked as a todo; completed only after RED is read
- [ ] Each test RED-verified via the project's test runner before impl-code
- [ ] Tests are minimal, behaviorally named to the plan row, and show the intended API
- [ ] Assertions target real behavior (not mock existence); doubles only when the plan names them
- [ ] No test-only methods on production types
- [ ] Mocks (when required) mirror the full real schema; side effect named before mocking
- [ ] Hard-to-test scenarios simplified or reported DONE_WITH_CONCERNS
- [ ] Focused test used while iterating RED
- [ ] Required tests fail when prerequisites missing; handoff reports run and skip counts per required group
- [ ] Error assertions use structured fields, not message text alone
- [ ] No discarded check results (`_ =` or ignored return on verification calls)
- [ ] Test names match plan scenarios
- [ ] No production behavior implemented here; premature product code deleted
- [ ] Limits stated if push or the test runner is blocked
- [ ] High-stakes decisions ran CLAIM→EXTRACT→DOUBT→RECONCILE when applicable
- [ ] Converge/gap handling is append-only (no silent delete/edit to clear gaps)
- [ ] Review considered Standards and Spec axes
- [ ] Adversarial stress-test run before locking high-stakes plan/approach
