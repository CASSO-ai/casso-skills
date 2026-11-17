# release-deploy

**Skill folder:** `casso-skills-release-deploy`

## Purpose

Deploy a release, and only after approval. The version deployed must be exactly the one that passed [release-validate](release-validate.md). After deploying, it checks the live result quickly. Your own release scripts do the deploy; this skill gates and records it.

## When to use

- After [release-validate](release-validate.md) passes and the person responsible for releases has approved this deploy.

## What you give it

- The validated version and its release-validate report.
- The approval: who approved and when.
- Your deploy command and a quick live check, such as a health page or a smoke test.

## What it produces

- **An approval check**: no approval, no deploy.
- **An identity match**: the version to deploy equals the validated version.
- **A release record**: what was deployed, when and by whom.
- **A quick live check** against what was actually published, not the local build.
- **A table of published artefacts** with the smoke-test results.

## Example

> Use casso-skills-release-deploy for `3c88a20`, validated in `docs/releases/2026-11-16-validate.md`, approved by the shop owner. Deploy with `npm run deploy`. Live check: open `/checkout` and apply a test code.

```markdown
Approved: yes      Validated 3c88a20 = deploying 3c88a20: match
Deployed 3c88a20 at 15:20
Live check: test code SAVE10 on a 50.00 order shows 45.00: passed
```

## Related skills

- [release-validate](release-validate.md): must pass first.
