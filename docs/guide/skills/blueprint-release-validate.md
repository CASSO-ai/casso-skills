# blueprint-release-validate

**Skill folder:** `casso-skills-blueprint-release-validate`

## Purpose

Check merged documentation before it is published as the new official version. It re-runs the mechanical structure checks on the exact merged version and refuses the release if any check fails, naming each failure. A branch passing earlier is not enough; merged branches can break each other.

## When to use

- After the documentation branches for a release are merged, before [blueprint-release-publish](blueprint-release-publish.md) makes them the official version.

## What you give it

- The exact commit of the merged documents to be published.
- Your structural check commands.
- Where to save the report.

## What it produces

A **PASS** or **FAIL** report with:

- the pinned version under test;
- the result of every mechanical check on that version;
- a scorecard and a list of each document checked.

A check that could not run is reported as **blocked**, never as passed.

## Example

> Use casso-skills-blueprint-release-validate on commit `7d10e4b`. Structure check: `npm run docs:check`. Save to `docs/releases/docs-2026-11-16-validate.md`.

```markdown
Candidate: 7d10e4b
docs:check: 0 broken links, 0 duplicate requirement numbers, 0 format errors
Verdict: PASS for 7d10e4b only.
```

## Related skills

- [blueprint-branch-validate](blueprint-branch-validate.md): the per-branch check that comes earlier.
- [blueprint-release-publish](blueprint-release-publish.md): publish exactly this version.
