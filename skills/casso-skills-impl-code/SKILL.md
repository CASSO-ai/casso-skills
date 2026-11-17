---
name: casso-skills-impl-code
description: Use when implementing production code to make the already-written tests pass — minimal GREEN, stay-green refactor, then traceability self-review
---

# Implement Code (casso-skills-impl-code)

## Overview

Implement production code until plan-scoped tests pass. Follow ATDD order: tests already exist from `casso-skills-impl-tests`.

**Iron law:** Minimal code to green; watched tests pass in the project's test runner. Do not claim GREEN or completion unless this message includes fresh test-runner output (or a cited runner/run artefact) showing the named tests pass.

**Method sources:** test-driven development (RED before GREEN, verify failure modes, refactor stay-green); plan execution depth when the brief embeds or points at a full plan; receiving and verifying code-review feedback against the codebase; systematic root-cause investigation before proposing fixes; `executing-plans` depth when the brief embeds or points at a full plan; `receiving-code-review` / `systematic-debugging` patterns adapted below.

RED and GREEN are separate work items: complete failing tests in casso-skills-impl-tests before production implementation in casso-skills-impl-code; do not collapse both into one continuous session.

## Preconditions

- `casso-skills-impl-tests` complete; tests failing for the right reasons.
- Read the code plan and authorized spec; implement only assigned C-SPEC units.

## Process

### 1. GREEN — minimal implementation

Implement the smallest change that makes the named tests pass; run through the project's test runner.

**Verification gate before any GREEN/completion claim:** IDENTIFY the proving command → RUN it fresh → READ the output → VERIFY the named tests pass → only then claim.

### 2. Bugfixes under this skill

When fixing a defect here: reproduce with a failing test first (or point at the `casso-skills-impl-tests` proof) before changing production code. Prove RED (revert or pre-fix) then GREEN on the same named test before claiming fixed. One change at a time; no drive-by refactors.

### 3. When greening fails — debug before more edits

When greening fails or a bug appears: investigate root cause before further production edits; no symptom-only patches. Read full errors; reproduce reliably; only then hypothesize. One hypothesis, smallest change, verify; do not stack fixes. After three failed fix attempts, stop and escalate architecture — do not attempt a fourth blind fix. Fix at source; when the defect is invalid data, add validation at each layer the data crosses.

### 4. Refactor stay-green

Refactor only while test-runner runs stay green. Improve only code you touch; do not restructure outside the assigned work item or split files the plan did not call for — report concerns instead. In tests you touch, wait on the condition under test — not arbitrary sleeps; document WHY if a timeout is required.

### 5. Product engineering rules

- No silent error swallows — log or surface every failure path.
- User-facing messages go through the project's user-output helpers; diagnostics through the project's tracing/logging.
- Error messages include the remedy.
- When adding a domain error variant, update every exhaustive API/error mapping that must name it.
- Product identity naming: use the project's full product name as the project defines it, never an undocumented shortened form.

### 6. Self-review and review response

Requirement-traceability self-review against plan + spec before submit.

Before acting on review or self-review notes, verify each item against the codebase; do not implement from tone or agreement. Response pattern for each item: READ → UNDERSTAND → VERIFY → EVALUATE → RESPOND/ACT → IMPLEMENT one item at a time. No performative agreement or thanks in reports; state the technical fix or reasoned pushback. If any review item is unclear, stop implementing the batch; clarify all items first. Treat external review as suggestions: check fitness for this codebase, regressions, rationale for current code, platforms, and reviewer context; push back with evidence when wrong. If feedback adds unused surface area, grep for callers; propose omit (YAGNI) rather than building unused features "properly." Order: clarify first; then blocking → simple → complex; test each fix; verify no regressions.

### 7. Commit and report

Commit only your paths; never stage the whole tree blindly. Report the **local** commit sha from `git rev-parse`; claiming a push that did not happen is a defect.

### Doubt-driven in-flight review (high-stakes)

For high-stakes decisions in this work item, run **CLAIM → EXTRACT → DOUBT → RECONCILE**:

1. **CLAIM** — state the claim and why it matters
2. **EXTRACT** — isolate the smallest reviewable artifact/contract, stripped of surrounding reasoning
3. **DOUBT** — adversarial review (fresh context when available)
4. **RECONCILE** — classify every finding against the artifact text; fix or escalate

### Converge append-only

After implementation evidence exists, gap-finding is **append-only**: add gap tasks / scenarios; do not edit or delete existing implementation to "make the report look clean" inside a converge pass. Re-run implement/tests work items to clear appended gaps.

### Review on two axes

When reviewing plans or code under this skill, evaluate in parallel:

- **Standards** — repo rules, naming, engineering conventions
- **Spec** — originating CR/spec/PRD acceptance

A change can pass one axis and fail the other; report both.

### Adversarial plan stress-test

Before locking a plan (or a high-stakes test/code approach), run a short adversarial interview that attacks assumptions, failure modes, and missing acceptance. Stop when remaining questions are cosmetic. Do not treat polite agreement as confirmation.

## Common mistakes

- Extra scope beyond the assigned units.
- Silent `Ok`/`Err` swallows.
- Reporting a push or sha that was not verified.
- Claiming GREEN without fresh runner output in the same message.
- Patching symptoms without a failing proof or root-cause investigation.
- Stacking multiple untested hypotheses or a fourth blind fix after three failures.
- Implementing review notes from agreement tone without verifying against the code.
- Building unused "proper" features the plan did not call for; restructuring files outside the work item.

## Review checklist

- [ ] Named tests GREEN in the project's test runner with fresh output cited
- [ ] Verification gate followed before the GREEN/completion claim
- [ ] Bugfixes: failing proof (or impl-tests citation) then RED→GREEN on the named test
- [ ] Root-cause path used when greening failed; no stacked blind fixes
- [ ] Logging, error, and naming rules followed
- [ ] Touched-code-only; condition-based waits in tests touched
- [ ] Review items verified against the codebase; unclear items clarified first
- [ ] Traceability self-review done
- [ ] Local commit + real sha reported
- [ ] High-stakes decisions ran CLAIM→EXTRACT→DOUBT→RECONCILE when applicable
- [ ] Converge/gap handling is append-only (no silent delete/edit to clear gaps)
- [ ] Review considered Standards and Spec axes
- [ ] Adversarial stress-test run before locking high-stakes plan/approach
