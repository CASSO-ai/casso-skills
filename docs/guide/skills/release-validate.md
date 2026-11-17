# release-validate

**Skill folder:** `casso-skills-release-validate`

## Purpose

Check a whole release before it is deployed. It runs the full test suite and every release check your project has on the exact version that will be deployed, and ties each result to that version. A branch passing on its own is not enough; branches can interact once merged together.

## When to use

- After all the branches for a release are merged, before [release-deploy](release-deploy.md).

## What you give it

- The release candidate: the exact commit you intend to deploy.
- Your project's release checks and how to run them.
- Where to save the report.

## What it produces

A **PASS** or **FAIL** report with:

- the pinned version under test;
- full regression results with counts;
- a result for each release check, tied to that version;
- a scorecard and a list of every artefact checked.

A check that could not run is reported as **blocked**, never as passed.

## Example

> Use casso-skills-release-validate on commit `3c88a20`. Release checks: `npm test`, `npm run lint`, `npm run build`. Save to `docs/releases/2026-11-16-validate.md`.

```markdown
Candidate: 3c88a20
Full suite: 212/212 passed        lint: passed        build: passed
Verdict: PASS for 3c88a20 only. Any later commit needs a new run.
```

## Related skills

- [release-deploy](release-deploy.md): deploy exactly this version.
- [branch-validate](branch-validate.md): the per-branch check that comes earlier.
