---
name: casso-skills-release-validate
description: Use when validating a whole release candidate before deploy — full regression and every project release gate on the exact tree to be deployed, each result tied to that tree's sha
---

# Release Validate (casso-skills-release-validate)

## Overview

Validate the **entire release candidate** before deploy. Run full regression and every project release gate on the **exact tree** that will be deployed. Tie each result to that tree's sha. Report **PASS** or **FAIL**.

**Core principle:** Deploy only a tree whose release gates all passed on that same sha. Branch-level PASS is not enough.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); project release-gate documentation (generic — use whatever the project defines).

## Preconditions

- Candidate tree chosen (usually the intended release tip after merges intended for this release).
- Release owner named the candidate sha.

## Process

### 1. Pin the candidate sha

Record the exact tree identity (sha) under validation. Every gate below must cite this sha. If the tree moves, restart validation.

### 2. Full regression

Run the project's full regression suite through the project's test runner on that tree. Assert suite and pass counts. One log file per run; report run ids when assigned. Poll on a capped loop; treat poll errors as finished.

### 3. Release gates (project-defined)

Execute **every** release gate the project requires for a deploy. Keep gates generic in this skill — invoke the project's named checks. Typical classes (examples, not product-internal mandates):

- Cross-platform / target builds the project ships
- Data dictionary parity with the schema the release includes
- Migrations immutable (no rewrite of already-shipped migration history)

Name each gate, its command or script, and its PASS/FAIL tied to the candidate sha.

When a release gate is a regression test for a known defect, prove it with red-green (revert or mutate → must fail → restore) on the candidate sha, not a single green run.

### 4. External oracle

At least one check that can disagree with the release packaging (checksum, published-artefact dry-run, lint) beyond self-assertion.

### 5. Verdict

Report **PASS** / **FAIL** with: candidate sha, gate table (name → result → evidence pointer), suite/pass counts, and known gaps. FAIL blocks `casso-skills-release-deploy` until fixed or a stated false alarm is accepted.

### Conformance scorecard

Produce a release conformance scorecard with **required** rows that gate release. A project profile or local waiver **cannot** mark a required gate as optional. Every required row needs file-path or command evidence; leave unknowns as unknown rather than guessing.

### Per-artifact validation inventory

Maintain an inventory of every published artifact. Each row has its own validation command. A producing job succeeding is **not** the same as the artifact passing its validation command — run each validation independently and record status per artifact.

### blocked ≠ passed

Missing checks, credentials, infra, or smoke-test capability are **blocked**, never **passed**. Do not collapse "could not run" into green.

## Common mistakes

- Reusing branch-validate evidence for a different sha.
- Skipping a project release gate because it "usually passes."
- Running gates on a scratch build instead of the candidate tree.

| Excuse | Required action |
|--------|-----------------|
| Usually passes / branch-validate was green / confident | Still run every gate on this sha |

## Review checklist

- [ ] Candidate sha pinned and cited on every gate result
- [ ] Full regression through the project's test runner with asserted counts
- [ ] Every project release gate named and evidenced
- [ ] Known-defect regression gates proven red-green on this sha
- [ ] External oracle present
- [ ] PASS/FAIL report ready for release-deploy handoff
- [ ] Terminology: work item
- [ ] Conformance scorecard present; required rows gate release
- [ ] Per-artifact validation inventory run; job success ≠ artifact pass
- [ ] Missing checks/credentials/infra recorded as blocked, not passed
