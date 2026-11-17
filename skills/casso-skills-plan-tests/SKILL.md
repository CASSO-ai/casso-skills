---
name: casso-skills-plan-tests
description: Use when authoring the test plan — scenarios, negative cases, and named proofs against the authorized spec — before implementing tests
---

# Plan Tests (casso-skills-plan-tests)

## Overview

Author the **test plan** (scenarios, negative cases, named suite/test proofs) against the authorized spec **before** implementing tests.

**Killer question:** If I only read the spec, would I write these test scenarios?

**Method sources:** bite-sized implementation planning (header, file map, right-sized leaves); `casso-skills-audit-plans` [TBD (In Dev)] test-scenario coverage dimensions; ATDD split (tests define done).

## Preconditions

- Code plan complete for the slice, and its review scored 100. (Once `casso-skills-audit-plans` [TBD (In Dev)] ships, its PASS is required instead.)
- Spec units provide the single `[CHECK]` per test obligation.

## Process

### 1. Map test files before scenarios

List test files to create or modify before scenario decomposition.

### 2. Map checks to scenarios

For each C-SPEC `[CHECK]`, declare at least one scenario with **When** / **Expected** columns.

Prefer one behavior per scenario; if the name needs "and", split into two When/Expected rows.

Scenarios must assert observable product behavior, not mock existence; if isolation needs a double, the Expected column still names real outcomes.

Where helpful, embed the intended test skeleton (name + assertion) in the scenario row or appendix so `casso-skills-impl-tests` cannot invent a different proof.

Each scenario states the exact runner invocation and pass/fail signal an agent must return.

For scenarios that expect failure, the Expected column names the **structured** outcome to assert (error type, status/code, or named constraint field) — never a substring of a human-readable error message.

Each scenario's skeleton must tie every setup query or helper call to an assertion; decorative lookups with no Expected linkage are forbidden.

### 3. Negative and anti-requirement cases

Where the spec says "must NOT", plan scenarios that would fail if the forbidden behavior appears.

### 4. Name runnable proofs

Name **exact test names** or project test-runner script invocations. Downstream QA and audits verify by name.

### 4b. Required tests must run, not skip

Separate **required** tests (mandated by brief or spec) from optional or integration-only groups. Integration tests that need outside services get their own named group in the plan.

A required test whose environment is missing must **fail the run** (or report the required group as not run, which counts as failure). It must not rely on the runner's skip mechanism while the overall report still shows success.

Every required group's pass/fail signal states **how many tests ran** and **how many were skipped** so an all-skipped suite cannot masquerade as green.

### 5. Testing tables are authoritative

The test plan's Testing tables are what `casso-skills-impl-tests` implements and `casso-skills-audit-tests` [TBD (In Dev)] validates. Keep scenario wording stable so audits can copy it verbatim.

### 6. Artifact placement

Write the test plan at the path named on the brief. When the brief gives no separate name, place a clearly titled test-plan section or sibling file next to the code plan and state that location in the handoff.

### Doubt-driven in-flight review (high-stakes)

For high-stakes decisions in this work item, run **CLAIM → EXTRACT → DOUBT → RECONCILE**:

1. **CLAIM** — state the claim and why it matters
2. **EXTRACT** — isolate the smallest reviewable artifact/contract, stripped of surrounding reasoning
3. **DOUBT** — adversarial review (fresh context when available)
4. **RECONCILE** — classify every finding against the artifact text; fix or escalate

### Converge append-only (after implement)

When a later converge pass finds gaps against this test plan, append gap scenarios/tasks only — do not silently rewrite the locked plan mid-flight without asking. Clearing gaps happens in the owning implement work items.

### Review on two axes

When reviewing plans or code under this skill, evaluate in parallel:

- **Standards** — repo rules, naming, engineering conventions
- **Spec** — originating CR/spec/PRD acceptance

A change can pass one axis and fail the other; report both.

### Adversarial plan stress-test

Before locking a plan (or a high-stakes test/code approach), run a short adversarial interview that attacks assumptions, failure modes, and missing acceptance. Stop when remaining questions are cosmetic. Do not treat polite agreement as confirmation.

## Common mistakes

- Scenarios that restate the check without a When/Expected pair.
- Counting "suite green" instead of naming the proving tests.
- Drifting scenario text between plan and later audit reports.
- Scenarios whose names need "and" (two behaviors jammed into one row).
- Expected columns that assert a mock exists instead of a real product outcome.
- Omitting the exact runner invocation and pass/fail signal the agent must return.
- Planning required database or integration tests without a skip/run signal, so all-skipped runs still read as pass.
- Expected columns that match error message text instead of structured error fields.
- Skeleton rows with helper calls or queries that never connect to an assertion.

## Review checklist

- [ ] Test files to create/modify listed before scenario decomposition
- [ ] Every `[CHECK]` has ≥1 When/Expected scenario
- [ ] One behavior per scenario (split when the name needs "and")
- [ ] Expected asserts observable product behavior (not mock existence)
- [ ] Intended test skeleton (name + assertion) embedded where helpful
- [ ] Each scenario names exact runner invocation and pass/fail signal
- [ ] Error scenarios assert structured fields (type, code, constraint), not message text
- [ ] Every skeleton call or query ties to an Expected assertion (no decorative lookups)
- [ ] Required vs integration groups named; required groups declare run and skip counts in pass/fail signal
- [ ] Required tests cannot pass via skip when prerequisites are missing
- [ ] Negative cases where the spec forbids behavior
- [ ] Named tests/suites for the project's test runner
- [ ] Scenario wording stable for downstream audit copy
- [ ] Artifact path stated for the next work item
- [ ] High-stakes decisions ran CLAIM→EXTRACT→DOUBT→RECONCILE when applicable
- [ ] Converge/gap handling is append-only (no silent delete/edit to clear gaps)
- [ ] Review considered Standards and Spec axes
- [ ] Adversarial stress-test run before locking high-stakes plan/approach
