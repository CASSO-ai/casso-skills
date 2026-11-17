# blueprint-branch-merge

**Skill folder:** `casso-skills-blueprint-branch-merge`

## Purpose

Merge a documentation branch (requirements, data model, design documents) after it passed [blueprint-branch-validate](blueprint-branch-validate.md). A requirements merge changes what everything later is built from, so its bar differs from a code merge: the person who owns the requirements approves the wording itself, the branch must still agree with every document merged since it was checked, and the merge lists the plans, tests and code that rely on the changed wording so they get re-checked. Your normal tools do the merge; this skill checks and records it.

## When to use

- After [blueprint-branch-validate](blueprint-branch-validate.md) passes and the requirements owner has approved the content.
- For code branches, use [branch-merge](branch-merge.md) instead.

## What you give it

- The branch, and the blueprint-branch-validate report with the version it passed.
- The content approval: who approved and when.

## What it produces

- **A freshness check**: if another documentation branch merged since validation, it stops and asks for a new validation run.
- **An identity match**: the version being merged is the one that passed validation.
- **A changed-requirements list**: every requirement added, changed or removed, by number. A removed number is never reused, and a new requirement never silently replaces an old one.
- **A structure re-check on the merged result**: numbers unique, links resolve. This catches two branches that picked the same new number.
- **A downstream list**: every plan, task, test and piece of code that cites a changed requirement, marked for re-check.
- **A merge record**, and a commit message that cites all of the above.

## Example

> Use casso-skills-blueprint-branch-merge for `spec-discount-stacking`. Validation report: `docs/validation/spec-discount-stacking.md`. The shop owner approved SHOP-3 as written today.

```markdown
Validated tree 51c2e9a = merge candidate 51c2e9a: match
Merged since validation: none
Changed: SHOP-3 (one code per order -> one code per order, plus one free-shipping code)
Approved by: shop owner, 2026-11-16 10:40
Downstream, needs re-check: WBS leaf SHOP-3.1, test plan scenario T-7, src/checkout/discount.ts
```

## Related skills

- [blueprint-branch-validate](blueprint-branch-validate.md): must pass first.
- [blueprint-release-validate](blueprint-release-validate.md): once the release's documentation merges are done.
