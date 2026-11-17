---
name: casso-skills-plan-code
description: Use when authoring the implementation (code) plan against an authorized audited spec — file map, work-item decomposition, and wire-contract obligations when triggered
---

# Plan Code (casso-skills-plan-code)

## Overview

Write the **code implementation plan** traced to authorized C-SPEC units. Save the plan at the path named in the brief (commonly under the project's plans tree).

**Killer question:** If I only read the spec, would I write these implementation work items?

**Method sources:** bite-sized implementation planning (header, file map, right-sized leaves); `casso-skills-audit-plans` [TBD (In Dev)] coverage dimensions for impl work items and wire obligations.

## Preconditions

- Spec work item done, and the authorized spec's review scored 100. (Once `casso-skills-audit-spec` [TBD (In Dev)] ships, its PASS with a fresh audit report is required instead.)
- Read authorized specs from the live spec tree.

## Process

### 1. Extract principles

Copy non-negotiable rules using the spec's **exact words**; tag `foundation-derived` vs `spec-internal`.

### 2. Plan header and constraints

Header with Goal, Architecture, and **Global Constraints** copied verbatim from the spec. Map files to create or modify before decomposing work.

### 3. Decompose into work items

Each plan work item is independently reviewable with explicit file paths. In plan prose say **work item** for each decomposable unit.

Prefer **one problem domain per work item**. When the work item is a fix, paste the failing names or error text. State hard constraints (for example tests-only) so a confined agent cannot broaden scope.

Inside each work item, list ordered actions small enough to verify alone (write failing proof name, run expect RED, implement, run expect GREEN, commit) with exact commands where the project's test runner is known.

For each work item, state **Consumes** / **Produces** interfaces with exact signatures neighboring work items rely on.

When a work item changes code, show the intended code (or equivalent exact patch shape) in the plan — never "implement validation" without the check.

Each work item's prose must be self-contained for a confined agent: specific scope, clear goal, constraints, and expected output/report shape — do not rely on session history.

### 4. Wire contract obligations (when triggered)

**Wire contract** = the exact data format two programs agree to exchange across a network boundary. If the plan touches remote-call / server-response code, include `## Wire contract obligations`: list endpoints, response fields, and cite that `casso-skills-audit-code` [TBD (In Dev)] Phase 6 (wire contract) is required at impl audit.

### 5. Removals

If the spec removes behavior, enumerate every removal location.

### 6. Self-review type consistency

After drafting, check type/method/property names agree across work items; fix inline.

### Vertical feature slices

Prefer **vertical** slices (one path through schema + API + UI, or the project's equivalent layers) over horizontal layers (all schema, then all API, then all UI). Each slice should deliver working, testable functionality.

### Phase template

Organize work into phases: **Setup** → **Foundational** (blocking prerequisites) → **per-user-story / per-leaf** phases in priority order → **Polish** (cross-cutting). Mark tasks that can run in parallel.

### Sizing XS–XL and checkpoints

Size leaves/tasks XS–XL. **Break XL** further before work starts. Place verification checkpoints every 2–3 tasks (or after each phase).

### Never overwrite an incomplete plan

Before writing or replacing a plan/WBS artifact, check for an existing incomplete plan (unchecked tasks / open leaves). If different work is mid-build in another session, **stop and ask** — do not delete, overwrite, or rename on your own.

## Common mistakes

- Invented scope that the spec never required.
- Vague file targets ("update the API").
- Skipping wire obligations when the plan clearly touches remote calls.
- Broad work items that mix unrelated domains or omit failing names/constraints on a fix.
- Work-item prose that assumes session history a confined agent will not have.
- Saying "implement X" without showing the intended check or patch shape.

## Review checklist

- [ ] Every C-SPEC `[CHECK]` maps to plan work items
- [ ] File paths explicit
- [ ] Each work item has ordered, alone-verifiable actions (exact runner commands when known)
- [ ] Consumes/Produces interfaces stated with exact signatures
- [ ] Intended code or patch shape shown where the work item changes code
- [ ] Type/method/property names agree across work items
- [ ] Each work item is self-contained (scope, goal, constraints, report shape)
- [ ] One problem domain per work item; failing names/errors pasted on fixes; hard constraints stated
- [ ] Wire obligations section present when triggered
- [ ] No invented scope
- [ ] Terminology uses work item
- [ ] Work sliced vertically (end-to-end paths), not only horizontal layers
- [ ] Phases follow Setup → Foundational → per-story → Polish; parallel markers set
- [ ] XL items broken down; checkpoints every 2–3 tasks
- [ ] Existing incomplete plan/WBS not overwritten without asking
