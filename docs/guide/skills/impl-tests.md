# impl-tests

**Skill folder:** `casso-skills-impl-tests`

## Purpose

Write the tests from the test plan before any product code. The tests define "done". Each test must fail first, and fail for the right reason: because the feature is missing, not because of a typo or a broken setup.

## When to use

- After the plans' reviews score 100 (audit-plans [TBD (In Dev)] once it ships), before [impl-code](impl-code.md).
- Writing the tests and writing the code are separate steps. Do not do both in one session.

## What you give it

- The test plan.
- The workspace or branch to work in.
- How to run the tests.

## What it produces

- The test code, and test-only helpers. No product code.
- A run showing each new test failing, with the failure reason, which should be the missing feature.
- A check that every row of the test plan has a test.

It stops once the tests are written and failing. Making them pass is [impl-code](impl-code.md)'s job.

## Example

> Use casso-skills-impl-tests for `docs/plans/discount-codes-L2-tests.md`. Work on branch `discount-codes-l2`. Run tests with `npm test`.

```text
FAIL discount_applies_percent    applyCode is not defined
FAIL discount_refuses_second     applyCode is not defined
2 failed, 0 passed: both fail because the feature does not exist yet.
```

## Related skills

- [impl-code](impl-code.md): the next step, making these tests pass.
- audit-tests [TBD (In Dev)]: check the tests against the plan.
