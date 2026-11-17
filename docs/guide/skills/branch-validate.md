# branch-validate

**Skill folder:** `casso-skills-branch-validate`

## Purpose

Prove a feature branch is safe to merge. It merges the branch onto your current main branch in a throwaway copy, runs your full test suite there, and proves each new test can actually fail. Only the exact version that passes here is eligible for [branch-merge](branch-merge.md).

## When to use

- After audit-code [TBD (In Dev)], before merging.
- Again if the main branch moves on before you merge.

## What you give it

- The branch to validate and your main branch's name.
- How to run the full test suite.
- The names of the branch's new tests.
- Where to save the report.

## What it produces

A **PASS** or **FAIL** report with counts:

- **Full regression** on the merged copy, with how many suites and tests ran and passed. "0 passed" is never read as "all passed".
- **Each new test by name**, run fresh even if someone already ran it.
- **A deliberate break per new test**: a temporary change to the product code that should make the test fail, showing it really guards something. Every such change is then undone cleanly.
- **Touched areas**: confirmation that nothing the branch touches got worse.
- **Findings**: each with its location and severity, followed by the strengths of the change.

The validator does not ship any edits of its own.

## Example

> Use casso-skills-branch-validate on `discount-codes-l2` against `main`. Full suite: `npm test`. New tests: discount_applies_percent, discount_refuses_second. Save to `docs/validation/discount-codes-l2.md`.

```markdown
Verdict: PASS on merged tree 9b1e07d
Full suite: 14 suites, 212 tests, 212 passed
discount_applies_percent: passes; removing the percentage step makes it fail
discount_refuses_second:  passes; allowing a second code makes it fail
```

## Related skills

- [branch-merge](branch-merge.md): merge exactly this validated version.
- [release-validate](release-validate.md): the check for a whole release.
