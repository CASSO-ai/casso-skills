# impl-code

**Skill folder:** `casso-skills-impl-code`

## Purpose

Write the smallest product code that makes the already-written tests pass, then tidy it up while keeping them passing. It never claims success without fresh test output that shows the named tests passing.

## When to use

- After [impl-tests](impl-tests.md), when the planned tests exist and fail for the right reason.
- For a bug fix: write a test that shows the bug first, then use this skill.

## What you give it

- The code plan and the requirements it covers.
- The branch with the failing tests.
- How to run the tests.

## What it produces

- Product code that makes the named tests pass, limited to the requirements you assigned.
- A refactoring pass that keeps every test passing.
- A self-review that traces each change back to a plan step and a requirement.
- A local commit, with the commit id read from git, and a report with the test output.

When a test will not pass, it finds the root cause before making more edits, rather than guessing. When review feedback arrives, it checks the feedback against the code before acting on it.

## Example

> Use casso-skills-impl-code for `docs/plans/discount-codes-L2-code.md` on branch `discount-codes-l2`. Run tests with `npm test`.

```text
PASS discount_applies_percent
PASS discount_refuses_second
2 passed, 0 failed
Commit: 4f2a9c1 "Apply one discount code per order (SHOP-1, SHOP-3)"
```

## Related skills

- [impl-tests](impl-tests.md): must come first.
- audit-code [TBD (In Dev)]: check the result against the plan and requirements.
