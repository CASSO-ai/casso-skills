---
name: casso-skills-blueprint-branch-validate
description: Use when validating a whole blueprint branch (specs, data model, design docs) before casso-skills-blueprint-branch-merge — four judgment document checks across the branch and against what is already merged, with mechanical structural checks and a PASS/FAIL report
---

# Blueprint Branch Validate (casso-skills-blueprint-branch-validate)

## Overview

Validate one **blueprint** branch **before** merge: integrate the branch onto the current blueprint main in a throwaway tree, then review the whole document set (functional specs, data model, design docs) against what is already merged. Report **PASS** or **FAIL**.

This is the first step of the blueprint gate, which runs right after `casso-skills-audit-spec` [TBD (In Dev)]: **this skill** → `casso-skills-blueprint-branch-merge` → `casso-skills-blueprint-release-validate` → `casso-skills-blueprint-release-publish`. This skill is the document check that must PASS before the merge.

**Core principle:** Evidence before claims. The validated blueprint tree is the only tree eligible for `casso-skills-blueprint-branch-merge`.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); structured code-review handoff (findings with locus, severity, strengths after proofs); the four judgment checks in Process §4.

## Preconditions

- Blueprint branch named; independent verifier (no shipping edits to the live blueprint — disposable integrate tree only).
- Earlier authoring and audit work items for the slice are complete when the pipeline includes them.
- Say **work item** for pipeline activities.

## Process

### 1. Build the candidate merged blueprint tree

Integrate the blueprint branch onto **current blueprint main** in a disposable workspace. Record the resulting tree identity (sha or equivalent). All checks below run on **this** tree, compared against what is already merged on main.

### 2. Identify proof commands and document set

Name every mechanical checker the project scripts for blueprint structure (spec-ID presence, duplicate-ID scan, reference resolution). Name the document roots in scope: functional specs, data model, design docs cited by the branch.

### 3. Mechanical structural checks (scripted where possible)

Run every available scripted check on the candidate tree. At minimum assert:

- Every spec unit has its spec ID
- No duplicate spec IDs across the loaded set
- Every in-set reference resolves to a real target

Record each check name, command, exit status, and failure list. A mechanical failure is a blocking FAIL item.

### 4. Judgment review — four document checks

Apply the **four judgment checks** below **across the branch and against what is already merged**:

1. **Contradictions** — statements that conflict with each other or with already-merged blueprint text
2. **Omissions** — required coverage the slice claims but leaves out
3. **Extras not clearly defined** — added material that lacks a clear definition or acceptance shape
4. **Structural gaps** — missing spec IDs, duplicate IDs, unresolved references, or other structural holes the mechanical pass did not already name

Judgment findings cite artifact path (and unit/id when applicable), why they block merge, and the remedy shape.

### 5. Fresh evidence gate

IDENTIFY the proving commands → RUN them fresh on this candidate tree → READ the output → VERIFY → only then claim. Do not claim PASS from a prior run, from confidence, or from an author's report.

### 6. Verdict

Report **PASS** / **FAIL** with: candidate-tree identity, mechanical check table, judgment findings (blocking vs known-accepted), strengths noted **after** proofs, and known gaps. On FAIL, each blocking finding cites file:line or exact unit/id, why it blocks merge, and the remedy. A FAIL stops `casso-skills-blueprint-branch-merge` until fixed or whoever owns merge/release accepts a stated false alarm.

Immediately before the verdict, rebuild both the spec-to-evidence and evidence-to-spec gap lists from the candidate tree. PASS only when both are empty or each remaining gap is recorded as known-accepted.

### Reviewer-owned requirements checklist

Treat requirements-quality checklists as **reviewer-owned**. An agent may help evaluate when asked, but must **not** silently self-approve checklist boxes. A checked item means a reviewer determined the requirements-quality criterion is satisfied — it does not mean implementation is complete.

### Read-only cross-artifact analyze

Before treating the branch as ready to implement or merge, run a **read-only** cross-artifact consistency pass (spec ↔ plan ↔ tasks / WBS ↔ related blueprint docs). Report conflicts, gaps, and ambiguities. Fix problems at the owning source artifact, then re-analyze until clean. Do not edit artifacts inside the analyze pass itself.

### External mechanical validator

Prefer a mechanical validator as an external oracle on requirement shape: every unit uses enforceable language (SHALL/MUST where the project format requires), each requirement carries at least one scenario/check, and delta integrity holds (ADDED/MODIFIED/REMOVED sections consistent with living specs). Record the command and its exit status. A green self-assertion without an external check is insufficient.

## Additional requirements

1. **Check invariants, not impressions.** Rewrite each validation claim as a condition with a boolean pass/fail result and named evidence. Reject narrative-only claims for which two reviewers could reach different results from the same artifacts.
2. **Refresh both gap directions before completion.** Incorporated by strengthening Process 6 with freshly rebuilt two-way gap lists and explicit closure criteria.
3. **Test blueprint reconstructability.** Give an independent agent only the frozen blueprint and evaluator-owned checks, then compare its observable results with the required behavior. PASS when all checks agree; do not require the agent's internal layout to match an existing construction.
4. **Change specification first.** For every branch behavior change, verify that the authoritative specification changed before its construction artifact and that the implementation traces to the revised clause. A code-first or stale-spec sequence is a blocking finding.
5. **Keep domain truth above construction aids.** Verify that domain rules, invariants, and acceptance conditions live in the blueprint and that templates or generators only consume them. PASS the branch on satisfaction of those domain conditions, not on whether a construction template was completed.

## Common mistakes

- Claiming pass from a prior run or from confidence.
- Validating the branch tip alone without integrating onto current blueprint main.
- Skipping a scripted structural check because it "usually passes."
- Rubber-stamping PASS without named mechanical results and the four judgment checks.
- Treating advisory notes as equal to blocking contradictions or unresolved references.

| Excuse | Required action |
|--------|-----------------|
| Should pass / I'm confident / just this once / agent said success | Still run every mechanical check on this candidate tree and complete the four judgment checks; assert results in the report |

## Review checklist

- [ ] Candidate tree = blueprint branch integrated onto current blueprint main; identity recorded
- [ ] Mechanical checks run fresh: every spec unit has its spec ID
- [ ] Mechanical checks: no duplicate spec IDs
- [ ] Mechanical checks: every in-set reference resolves
- [ ] Judgment: contradictions reviewed across branch and against merged main
- [ ] Judgment: omissions reviewed
- [ ] Judgment: extras not clearly defined reviewed
- [ ] Judgment: structural gaps reviewed (including any the scripts missed)
- [ ] On FAIL, each blocking finding cites path/id, why, and remedy
- [ ] Gaps categorized blocking vs known-accepted; strengths only after proofs
- [ ] PASS/FAIL report ready for blueprint-branch-merge handoff
- [ ] Terminology: work item
- [ ] Requirements checklist not silently self-approved by the agent
- [ ] Read-only cross-artifact analyze run; issues fixed at source then re-analyzed
- [ ] Your project's strict mechanical validation command (or equivalent) recorded as external oracle
