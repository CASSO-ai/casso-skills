# plan-tests

**Skill folder:** `casso-skills-plan-tests`

## Purpose

Write the test plan before any tests are written: the scenarios, the failure cases and the exact named tests that will prove each requirement. Every acceptance check in the requirements becomes at least one test.

## When to use

- After [plan-code](plan-code.md), before audit-plans [TBD (In Dev)] and [impl-tests](impl-tests.md).

## What you give it

- The approved requirements and the code plan.
- Where your tests live and how they are run.
- Where to save the test plan.

## What it produces

- **A test file map**: which test files hold which scenarios.
- **Scenarios**: for each acceptance check, a *When* (the situation) and an *Expected* (the result).
- **Negative cases**: what must not happen, such as an expired code being accepted.
- **Named runnable tests**: the exact test names to run, so "done" is a run anyone can repeat.

Expected failures are stated as a structured result, such as an error kind or status code, never as a piece of message text that might change. Tests the plan requires must actually run; a test that is skipped does not count. The test tables in this plan are the authority later stages check against.

## Example

> Use casso-skills-plan-tests for `docs/plans/discount-codes-L2-code.md`. Tests are in `tests/`. Save to `docs/plans/discount-codes-L2-tests.md`.

```markdown
| Check  | When                                  | Expected                   | Test                       |
|--------|---------------------------------------|----------------------------|----------------------------|
| SHOP-1 | order 50.00, valid 10% code           | total 45.00                | discount_applies_percent   |
| SHOP-3 | second valid code on a coded order    | result = AlreadyHasCode    | discount_refuses_second    |
```

## Related skills

- audit-plans [TBD (In Dev)]: check the test plan against the requirements and code plan.
- [impl-tests](impl-tests.md): write these tests.
