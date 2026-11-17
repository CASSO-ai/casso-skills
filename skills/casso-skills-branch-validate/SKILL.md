---
name: casso-skills-branch-validate
description: Use when validating an individual feature branch against current main before merge — full regression on the merged tree, named new tests, mutation proofs, and a PASS/FAIL report with counts
---

# Branch Validate (casso-skills-branch-validate)

## Overview

Validate one branch **before** merge: merge the branch onto current main in a throwaway tree, run full regression through the project's test runner, prove each of the branch's new tests by name (including a mutation that shows each can fail), and confirm nothing the branch touches regressed. Report **PASS** or **FAIL** with asserted suite and pass counts.

**Core principle:** Evidence before claims. The validated tree is the only tree eligible for `casso-skills-branch-merge`.

**Method sources:** evidence-before-claim discipline (fresh proof, no rationalization); structured code-review handoff (findings with locus, severity, strengths after proofs)

Re-run implementer tests yourself on the candidate tree with fresh runner evidence; do not skip re-running because a reviewer or subagent already ran them.

Apply temporary mutations as part of the gate, then revert them clean; validation is not limited to a forever read-only reviewer checkout.

**Post-MVP note:** none — this work item stays branch-scoped. Release-wide gates belong to `casso-skills-release-validate`.

## Preconditions

- Implementation and test audits for the branch's scope are complete when the pipeline includes them.
- Independent verifier: no product edits that ship (temporary mutations only, reverted clean).

## Process

### 1. Build the candidate merged tree

Integrate the branch onto **current main** in a disposable workspace. Record the resulting tree identity (sha or equivalent). All proofs below run on **this** tree.

### 2. Identify proof commands

Name the project's test-runner entry point and the **exact test names** that are new on this branch. Also name the regression suite the project requires for a branch of this blast radius.

### 3. Full regression on the merged tree

Run the project's full regression (or the brief's named regression scope) through the project's test runner. One log file per run; report each run's integer id when the runner assigns one. Poll on a capped loop; treat a poll error as finished and report it.

### 4. New tests by name

Execute each new test by name. Assert pass counts for the named set.

### 5. Mutation per new test

For each new test: introduce a temporary mutation that should make that test go RED; confirm it fails; revert clean; report compiler error count if a mutation does not compile. Mutations must break agreement between two independent places (not a shared constant both sides read).

### 6. Touched-surface regression

Confirm surfaces the branch touches did not regress relative to main (named proofs or scoped suites as the project defines).

### 7. External oracle

Include at least one check that can disagree with the code — lint, diff-vs-spec read — beyond self-assertion.

### 8. Verdict

Report **PASS** / **FAIL** with: candidate-tree identity, suite count, pass count, named mutations, and known gaps. Do not rubber-stamp PASS without the named proofs; categorize gaps as blocking vs known-accepted; note what the branch did well only after proofs. On FAIL, each blocking finding cites file:line (or test name), why it blocks merge, and the remedy. A FAIL stops merge until fixed or whoever owns merge/release accepts a stated false alarm.

### Five-axis review

Review the candidate change across five axes: **correctness**, **readability**, **architecture**, **security**, and **performance**. Prefer change sizing near ~100 lines of focused diff when splitting reviewable units; oversized dumps hide defects.

## Common mistakes

- Claiming pass from a prior run or from confidence.
- Validating the branch tip alone without integrating onto current main.
- Mutation that only changes a shared constant both sides read (self-assertion).
- Skipping full regression when the brief requires it on this host.
- Rubber-stamping PASS without named proofs and asserted counts.

| Excuse | Required action |
|--------|-----------------|
| Should pass / I'm confident / just this once / agent said success | Still run full regression on the candidate tree and assert counts |

## Review checklist

- [ ] Candidate tree = branch integrated onto current main; identity recorded
- [ ] Full regression evidenced through the project's test runner
- [ ] New tests executed by name with asserted counts
- [ ] Mutation per new test, matched by name, reverted clean
- [ ] Touched surfaces checked for regression
- [ ] Suite and pass counts both named in the PASS/FAIL report
- [ ] On FAIL, each blocking finding cites file:line (or test name), why, and remedy
- [ ] Gaps categorized blocking vs known-accepted; strengths only after proofs
- [ ] Terminology: work item
- [ ] Five-axis review covered (correctness, readability, architecture, security, performance)
