---
name: casso-skills-branch-merge
description: Use when recording that a branch merge completed after approval from the person responsible for merges — confirm the merged result is exactly the tree that passed branch-validate
---

# Branch Merge (casso-skills-branch-merge)

## Overview

Record the merge after approval from the person responsible for merges. This skill **checks** mergeability and **records** that the merged result is **exactly** the tree that passed `casso-skills-branch-validate`. Your own git tooling performs the merge; this skill gates and records it.

**Core principle:** Merge requires explicit approval from the person responsible for merges. The merge record binds to the validated tree identity — no silent substitution.

**Method sources:** branch integration hygiene before merge

## Preconditions

- `casso-skills-branch-validate` PASS for this branch (hotfix templates may skip when so ruled).
- Explicit approval for the merge.

## Process

### 1. Merge check (readout)

Run the deterministic mergeability readout: rebase state, branch-validate green, scope in bounds, base current. The project defines what "tests pass" means and owns the scripts that check it.

### 2. Identity match

Confirm the tree about to be recorded as merged is the **same identity** (sha or equivalent) that branch-validate reported PASS on. If main moved or the tree drifted, re-run branch-validate — do not record a different tree under the old PASS.

### 3. Three-part merge bar on the merged tree

Before the merge record: workspace green with **asserted counts**, mutation proof by **test name** when the project requires it at merge time, and an external oracle. Re-verify after the merge-base check.

### 4. Record merge event

Populate merge fields atomically: merge timestamp, merging work identity, merge commit sha equal to the validated tree (or the recorded successor that is byte-identical in content to it). Use the project's merge-record CLI verbs when available; if flags are not yet published, record the same fields by a manual procedure approved by the person responsible for merges and state that limit.

### 5. Merger job behavior

The merger agent is interactive and job-assigned; may postpone or hold per the project's release guidelines. Read those guidelines before ordering merges.

### 6. Commit message evidence

The merge commit carries counts, mutation names, oracle output, validated-tree identity, and known gaps.

### Five-axis review

Review the candidate change across five axes: **correctness**, **readability**, **architecture**, **security**, and **performance**. Prefer change sizing near ~100 lines of focused diff when splitting reviewable units; oversized dumps hide defects.

## Common mistakes

- Recording merge without approval from the person responsible for merges.
- Recording a tree that is not the one branch-validate passed.
- Trusting a green branch tip without the merged-tree identity check.

## Review checklist

- [ ] Explicit approval obtained before record
- [ ] Merged tree identity matches branch-validate PASS tree
- [ ] Three-part bar evidenced on the merged tree
- [ ] Merge event fields recorded atomically
- [ ] Release guidelines consulted for ordering
- [ ] Terminology: work item
- [ ] Five-axis review covered (correctness, readability, architecture, security, performance)
