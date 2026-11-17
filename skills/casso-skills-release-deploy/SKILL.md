---
name: casso-skills-release-deploy
description: Use when deploying a release after approval from the person responsible for releases — deploy the exact tree that passed release-validate, then run a quick live check on the published artefact
---

# Release Deploy (casso-skills-release-deploy)

## Overview

Deploy the **exact tree** that passed `casso-skills-release-validate`, with approval from the person responsible for releases, then run a quick live check on the published artefact. Your project's release tooling **records** release events; execution stays with project release scripts and human/agent operations outside product verbs when so configured.

**Core principle:** No deploy without explicit approval from the person responsible for releases. The deployed sha must equal the release-validate PASS sha.

## Preconditions

- `casso-skills-release-validate` PASS for the candidate sha.
- Explicit approval for this deploy.

## Process

### 1. Approval gate

No deploy without explicit approval from the person responsible for releases naming the candidate sha.

### 2. Identity match

Confirm the tree being deployed is the **same sha** release-validate reported PASS on. If anything rebuilt or retagged a different tree, stop and re-validate.

### 3. Release record

Append release semantics: environment, version pointer, approving user, deploying work item, deployed sha. Use the project's release-record CLI when available; otherwise record the same fields by a manual procedure approved by the person responsible for releases and state that limit.

### 4. Execute deploy

Invoke the project release script only when the brief names that scope. Report dry-run or working-environment limits honestly.

### 5. Quick live check

After deploy, verify on the **published artefact** (not a branch tip or scratch build): a short smoke or health check the project defines. Record pass/fail and any stated limits.

### 6. Skills bundle (when in scope)

When the release ships curated skills, confirm the installed skills folder names match the skill table names for this release.

### 7. Post-release artifact table and smoke

After deploy, render a post-release table: each published artifact, its producing job, validation/smoke result, and status (`passed` / `failed` / `blocked`). Handle version-bump PR state explicitly (merged / left-open / failed / n/a). Missing smoke infra is **blocked**, not passed.

### 8. Ship lifecycle entry

Treat ship/deploy as its own lifecycle entry with pre-launch checks, monitoring/rollback ready, and a clear success signal — not only "the pipeline went green."

## Common mistakes

- Deploying a sha that did not pass release-validate.
- Verifying a scratch build and calling it deployed.
- Deploying without approval from the person responsible for releases.
- Hiding a working-environment limit that blocked the real release.

## Review checklist

- [ ] Explicit approval before record
- [ ] Deployed sha equals release-validate PASS sha
- [ ] Release row semantics satisfied
- [ ] Quick live check on the published artefact
- [ ] Stated limits if the working environment cannot push or run release
- [ ] Terminology: work item
- [ ] Post-release artifact table + smoke recorded; blocked ≠ passed
- [ ] Ship lifecycle entry covers pre-launch, monitor/rollback, and success signal
