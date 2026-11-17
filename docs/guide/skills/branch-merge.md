# branch-merge

**Skill folder:** `casso-skills-branch-merge`

## Purpose

Record a merge, and only after it was approved. It confirms that what gets merged is exactly the version that passed [branch-validate](branch-validate.md), with nothing swapped in or added afterwards. Your normal tools do the merge itself; this skill checks and records it.

## When to use

- After [branch-validate](branch-validate.md) passes and the person responsible for the main branch has approved the merge.

## What you give it

- The branch, and the branch-validate report with the version it passed.
- The approval: who approved and when.

## What it produces

- **A merge check**: can the branch still merge cleanly?
- **An identity match**: the version being merged is the one that passed validation. If anything changed, the merge stops and the branch is validated again.
- **A merge bar on the merged result**: it builds, the tests pass, and nothing unexpected changed.
- **A merge record**, and a commit message that cites the validation evidence.
- A short review covering correctness, readability, design, risk and tests.

## Example

> Use casso-skills-branch-merge for `discount-codes-l2`. Validation report: `docs/validation/discount-codes-l2.md`. Approved by the shop owner today.

```markdown
Validated tree 9b1e07d = merge candidate 9b1e07d: match
Merged as 3c88a20 "Apply one discount code per order (SHOP-1, SHOP-3)
Validated: docs/validation/discount-codes-l2.md (212/212 passed)"
```

## Related skills

- [branch-validate](branch-validate.md): must pass first.
- [release-validate](release-validate.md): once the release's merges are done.
