---
name: casso-skills-blueprint-release-publish
description: Use when publishing a validated blueprint release as the new official version after blueprint-release-validate PASS — approval gate, identity match, move the official pointer to that exact tree, read back the published copy, record the release and list the work built on the previous version
---

# Blueprint Release Publish (casso-skills-blueprint-release-publish)

## Overview

Publish the merged blueprint as the new **official version** — the version every later stage plans and builds against. Publishing documents is not a deploy: nothing is started or run. It means moving the official pointer (a tag, branch or version number, as your project defines it) to the exact tree that passed `casso-skills-blueprint-release-validate`, then telling the people and agents building on the previous version what changed.

This is the last step of the blueprint gate: `casso-skills-blueprint-branch-validate` → `casso-skills-blueprint-branch-merge` → `casso-skills-blueprint-release-validate` → **this skill**. For code releases use `casso-skills-release-deploy`.

**Core principle:** The official blueprint points only at a tree whose release validation passed on that same identity, and every change from the previous official version is named.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); modeled on `casso-skills-release-deploy`, with the deploy and live smoke test replaced by a pointer move and a read-back of the published copy.

## Preconditions

- `casso-skills-blueprint-release-validate` PASS for the candidate, with its report and the pinned identity (sha or equivalent).
- Explicit approval to publish from the person who owns the requirements, naming the candidate.
- Say **work item** for pipeline activities.

## Process

### 1. Approval gate

No publish without explicit approval naming the candidate identity.

### 2. Identity match

Confirm the tree to publish is the **same identity** blueprint-release-validate reported PASS on. If anything merged or changed since, stop and re-validate.

### 3. Change summary

List every spec unit added, changed or removed since the previous official version, by id, with the blueprint-branch-merge record that brought each one in. This is the release's changelog.

### 4. Publish

Move the official pointer to the candidate identity using the project's publish command. Do not rewrite or delete earlier official versions; they stay retrievable so work built on them can be compared.

### 5. Read-back check

Read the **published** copy, not your local tree: the official pointer resolves to the candidate identity, the document index opens, and the references checked in validation still resolve there. Record pass or fail. A check that could not run is **blocked**, never passed.

### 6. Downstream notice

Collect the downstream impact lists from the blueprint-branch-merge records in this release. List every open work item, plan or brief built against the previous official version that cites a changed unit, marked needs re-check against the new version.

### 7. Release record

Record atomically: published identity, previous official identity, who approved and when, publishing work identity, timestamp, the change summary, the read-back result and the downstream notice. Use the project's release-record command when available; otherwise record the same fields by a manual procedure approved by the person who owns the requirements, and state that limit.

## Common mistakes

- Publishing a tree other than the validated one, or one that moved after validation.
- Checking the local tree instead of the published copy.
- Rewriting an earlier official version instead of adding a new one.
- Publishing without a change summary, so nobody can tell what changed.
- Treating "could not read back" as passed.

| Excuse | Required action |
|--------|-----------------|
| Validate passed / it's just docs / the pointer obviously moved | Get the approval, match the identity, read back the published copy and record the result |

## Review checklist

- [ ] blueprint-release-validate PASS cited with pinned identity
- [ ] Explicit approval to publish, naming the candidate
- [ ] Published identity equals the validated identity
- [ ] Change summary lists every unit added / changed / removed since the previous official version
- [ ] Earlier official versions left intact
- [ ] Read-back done on the published copy; blocked recorded as blocked
- [ ] Downstream notice lists work built on the previous version that cites changed units
- [ ] Release record fields recorded atomically
- [ ] Terminology: work item
