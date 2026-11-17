---
name: casso-skills-blueprint-release-validate
description: Use when validating the merged blueprint before casso-skills-blueprint-release-publish makes it the official version — rerun mechanical structural checks on the exact merged tree and refuse release on any failure with a named report
---

# Blueprint Release Validate (casso-skills-blueprint-release-validate)

## Overview

Validate the **merged blueprint** before `casso-skills-blueprint-release-publish` makes it the official version. Rerun the **mechanical** structural checks on the **exact merged tree**. Report **PASS** or **FAIL**. Refuse the release on any failure with a report naming each failing item.

This is the third step of the blueprint gate: `casso-skills-blueprint-branch-validate` → `casso-skills-blueprint-branch-merge` → **this skill** → `casso-skills-blueprint-release-publish`. This skill is the mechanical check that must PASS before publishing.

**Core principle:** Point the blueprint head only at a merged tree whose mechanical structural checks all passed on that same sha. Branch-level PASS is not enough.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); modeled on `casso-skills-release-validate`.

## Preconditions

- Merged blueprint tree chosen (the intended blueprint head after merges intended for this release).
- Release owner named the candidate sha.

## Process

### 1. Pin the candidate sha

Record the exact merged-blueprint tree identity (sha) under validation. Every check below must cite this sha. If the tree moves, restart validation.

### 2. Mechanical structural checks (rerun)

Rerun every mechanical check the project scripts for blueprint structure on that tree. Required checks:

- Every spec unit has its spec ID
- No duplicate spec IDs across the loaded set
- Every in-set reference resolves to a real target

Name each check, its command or script, exit status, and the list of failing items (path + id + reason). Tie each result to the candidate sha.

IDENTIFY → RUN fresh → READ → VERIFY → only then claim. Do not reuse blueprint-branch-validate evidence for a different sha.

### 3. Verdict

Report **PASS** / **FAIL** with: candidate sha, mechanical check table (name → result → failing items), and known gaps. On any failure, **refuse** the release and name each failing item in the report. FAIL blocks `casso-skills-blueprint-release-publish` until fixed or a stated false alarm is accepted by whoever authorized the work.

### Conformance scorecard

Produce a release conformance scorecard with **required** rows that gate release. A project profile or local waiver **cannot** mark a required gate as optional. Every required row needs file-path or command evidence; leave unknowns as unknown rather than guessing.

### Per-artifact validation inventory

Maintain an inventory of every published artifact. Each row has its own validation command. A producing job succeeding is **not** the same as the artifact passing its validation command — run each validation independently and record status per artifact.

### blocked ≠ passed

Missing checks, credentials, infra, or smoke-test capability are **blocked**, never **passed**. Do not collapse "could not run" into green.

## Common mistakes

- Reusing blueprint-branch-validate evidence for a different sha.
- Skipping a mechanical check because branch-validate was green or it "usually passes."
- Running checks on a scratch copy instead of the candidate merged tree.
- Claiming PASS while any named structural failure remains unlisted.

| Excuse | Required action |
|--------|-----------------|
| Usually passes / blueprint-branch-validate was green / confident | Still run every mechanical check on this sha and name each failure |

## Review checklist

- [ ] Candidate sha pinned and cited on every mechanical result
- [ ] Every spec unit has its spec ID (fresh run on this sha)
- [ ] No duplicate spec IDs (fresh run on this sha)
- [ ] Every in-set reference resolves (fresh run on this sha)
- [ ] On FAIL, report names each failing item and refuses release
- [ ] PASS/FAIL report ready for blueprint-release-publish handoff
- [ ] Terminology: work item
- [ ] Conformance scorecard present; required rows gate release
- [ ] Per-artifact validation inventory run; job success ≠ artifact pass
- [ ] Missing checks/credentials/infra recorded as blocked, not passed
