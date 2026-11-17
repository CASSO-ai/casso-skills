---
name: casso-skills-blueprint-branch-merge
description: Use when merging a blueprint branch (specs, data model, design docs) after blueprint-branch-validate PASS — requires the requirements owner's approval of the content, re-checks against blueprints merged since validation, lists the downstream work that cites changed units, and records the merge
---

# Blueprint Branch Merge (casso-skills-blueprint-branch-merge)

## Overview

Merge one validated **blueprint** branch into the blueprint main. A blueprint merge changes the source of truth that every later stage (data model, WBS, plans, tests, code) is built from, so its bar is different from a code merge: the **content** must be approved by the person who owns the requirements, the branch must still agree with every blueprint merged since it was validated, and the merge must name the downstream work that now rests on changed wording.

This is the second step of the blueprint gate: `casso-skills-blueprint-branch-validate` → **this skill** → `casso-skills-blueprint-release-validate` → `casso-skills-blueprint-release-publish`. Your own git tooling performs the merge; this skill gates and records it. For code branches use `casso-skills-branch-merge`.

**Core principle:** An agent never makes its own wording official. Only the requirements owner's approval of the exact text, on the exact validated tree, makes a blueprint change part of the source of truth.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); requirements change control (owner approval of content, traceability of each changed unit to the work that cites it).

## Preconditions

- `casso-skills-blueprint-branch-validate` PASS for this branch, with its report and the validated tree identity (sha or equivalent).
- Approval **of the content** from the person who owns the requirements, naming the changed units or the validated tree. Approval to merge alone is not enough.
- Say **work item** for pipeline activities.

## Process

### 1. Merge check (readout)

Confirm the branch still integrates cleanly onto the current blueprint main. List every blueprint merge that landed on main since the validation run. If any landed, the PASS is stale: re-run `casso-skills-blueprint-branch-validate` on the new candidate tree. Do not merge under the old PASS.

### 2. Identity match

Confirm the tree about to be merged is the **same identity** blueprint-branch-validate reported PASS on. Any edit after validation, even a typo fix, needs a new validation run.

### 3. Content approval

List every spec unit the branch **adds**, **changes** or **removes**, by id. Confirm the requirements owner approved that content. Rules:

- An agent may draft and propose blueprint text; it never approves it, and never merges its own text as official without that approval.
- A later unit does **not** replace an earlier one unless the change says so explicitly, naming the unit it replaces. An unstated conflict stops the merge.
- A removed id is retired, never reused for a different requirement.

### 4. Structure re-check on the merged tree

Re-run the mechanical structure checks on the merged result: every spec unit has its id, no duplicate ids, every reference resolves. These are cheap and catch two branches that took the same new id in parallel. Record each check, command, exit status and failure list.

### 5. Downstream impact list

For each added, changed or removed unit, list every artefact that cites it: data model entries, WBS leaves, code and test plans, tests, code, open work items. Mark each as **needs re-check**. This list is part of the merge record, so work built on the old wording is re-checked rather than silently left stale.

### 6. Record merge event

Populate merge fields atomically: merge timestamp, merging work identity, approver of the content and when, merge commit sha equal to the validated tree (or a successor byte-identical in content), the changed-unit list, and the downstream impact list. Use the project's merge-record command when available; otherwise record the same fields by a manual procedure approved by the person who owns the requirements, and state that limit.

### 7. Commit message evidence

The merge commit carries: the blueprint-branch-validate report path, the validated tree identity, the changed unit ids (added / changed / removed), who approved the content, the downstream impact list (or its path), and known gaps.

## Common mistakes

- Merging on merge approval when nobody approved the content.
- Merging under a PASS that predates another blueprint merge.
- Reusing a removed spec id, or letting a new unit silently override an old one.
- Leaving out the downstream impact list, so plans and code built on the old wording look current.
- Applying code merge criteria (test counts, mutation proofs) and calling the blueprint checked.

| Excuse | Required action |
|--------|-----------------|
| It's only wording / the owner will agree / validate passed yesterday | Get the content approval, list blueprint merges since validation and re-validate if any, re-run the structure checks on the merged tree |

## Review checklist

- [ ] blueprint-branch-validate PASS cited, with validated tree identity
- [ ] Blueprint merges since validation listed; re-validated if any
- [ ] Merged tree identity matches the validated tree
- [ ] Changed units listed by id (added / changed / removed)
- [ ] Requirements owner approved the content; no agent self-approval
- [ ] No silent supersession; no reused ids
- [ ] Structure checks re-run on the merged tree with results recorded
- [ ] Downstream impact list produced and marked needs re-check
- [ ] Merge event fields recorded atomically
- [ ] Commit message carries the evidence
- [ ] Terminology: work item
