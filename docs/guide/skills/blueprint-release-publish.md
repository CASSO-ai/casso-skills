# blueprint-release-publish

**Skill folder:** `casso-skills-blueprint-release-publish`

## Purpose

Publish merged documentation as the new official version, the one every later stage plans and builds against. Nothing is deployed or run: publishing means moving the official marker (a tag, branch or version number) to the exact version that passed [blueprint-release-validate](blueprint-release-validate.md), checking the published copy, and telling everyone building on the previous version what changed.

## When to use

- After [blueprint-release-validate](blueprint-release-validate.md) passes and the requirements owner has approved publishing.
- For code releases, use [release-deploy](release-deploy.md) instead.

## What you give it

- The validated version and its blueprint-release-validate report.
- The approval: who approved and when.
- Your publish command, such as creating a version tag.

## What it produces

- **An approval check**: no approval, no publish.
- **An identity match**: the version published equals the validated version.
- **A change summary**: every requirement added, changed or removed since the last official version.
- **A read-back check** on the published copy, not your local files.
- **A downstream notice**: open work built on the previous version that cites a changed requirement.
- **A release record.** Earlier official versions are kept, never rewritten.

## Example

> Use casso-skills-blueprint-release-publish for `7d10e4b`, validated in `docs/releases/docs-2026-11-16-validate.md`, approved by the shop owner. Publish with `git tag spec-v4 7d10e4b && git push origin spec-v4`.

```markdown
Approved: yes      Validated 7d10e4b = publishing 7d10e4b: match
Published spec-v4 -> 7d10e4b (previous: spec-v3 -> 2a0f55c)
Changed since spec-v3: SHOP-3 changed, SHOP-9 added
Read-back of spec-v4: index opens, 0 broken links: passed
Needs re-check: WBS leaf SHOP-3.1 (open)
```

## Related skills

- [blueprint-release-validate](blueprint-release-validate.md): must pass first.
- [blueprint-branch-merge](blueprint-branch-merge.md): the merges this release collects.
