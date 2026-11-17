---
name: casso-skills-wbs
description: Use when breaking an authorized audited spec into a work breakdown structure — each leaf one deliverable small enough for one agent, with bidirectional clause traceability and dependencies
---

# WBS (casso-skills-wbs)

## Overview

Take a slice's authorized spec and produce the requirement → task → test traceability matrix. Each leaf is one deliverable small enough for one agent.

**Core principle:** The WBS is a faithfulness instrument — every authorized requirement gets a leaf; no leaf invents scope.

**Method sources:** bite-sized implementation planning (header, file map, right-sized leaves); Project `wbs-method` (leaves, both-way clause traceability, dependencies, completeness checks).

## Preconditions

- Spec authorized, and its review scored 100. (Once `casso-skills-audit-spec` [TBD (In Dev)] ships, its PASS is required instead.)
- When the slice needs stored data: data model + dictionary present for WBS leaves to cite, and their review scored 100. (Once `casso-skills-audit-data-model` [TBD (In Dev)] ships, its PASS is required instead.)
- Specs carry `C-SPEC-<PROJECT>-<n>` units with one `[CHECK]` each.

## Process

### 1. Scope check before one WBS

If the authorized slice still spans independent subsystems, stop and ask whoever authorized the work to split before building one WBS.

### 2. Enumerate requirements from the source

Enumerate every `[C-SPEC-…]` definition (line-start markers) from the authorized spec files for the slice. Do not sample from memory.

### 3. Create leaves

For each requirement, define one leaf (or a minimal set of leaves when the unit truly needs sequenced deliverables) with:

- Leaf id and title
- Mapped `C-SPEC` id(s)
- Deliverable description
- Empirical check (the unit's `[CHECK]` or a named proof derived from it)
- Dependencies on other leaves (build order)

No TBD leaves, no "write tests later," and no leaf without an empirical check or C-SPEC mapping.

### 4. Bidirectional traceability

Maintain both directions:

- Requirement → leaf (no orphan requirement)
- Leaf → requirement (no invented leaf)

### 5. Dependency graph

Record prerequisites so a leaf with no dependencies can start first. Cycles are defects — break or escalate them.

### 6. Cross-cutting sweep

Re-read cross-cutting classes (errors, logging, auth, migrations, observability, CLI output, security) and confirm each relevant requirement has a leaf.

### 7. Output artefact

Write the WBS matrix at the path named on the brief. Include the build order and the both-way maps.

Header the artefact with: slice goal; cited spec (and data model, if any) paths and SHAs, with their review scores (or, once shipped, `casso-skills-audit-spec` [TBD (In Dev)] and `casso-skills-audit-data-model` [TBD (In Dev)] report paths); global constraints copied verbatim from the spec.

### Vertical feature slices

Prefer **vertical** slices (one path through schema + API + UI, or the project's equivalent layers) over horizontal layers (all schema, then all API, then all UI). Each slice should deliver working, testable functionality.

### Phase template

Organize work into phases: **Setup** → **Foundational** (blocking prerequisites) → **per-user-story / per-leaf** phases in priority order → **Polish** (cross-cutting). Mark tasks that can run in parallel.

### Sizing XS–XL and checkpoints

Size leaves/tasks XS–XL. **Break XL** further before work starts. Place verification checkpoints every 2–3 tasks (or after each phase).

### Never overwrite an incomplete plan

Before writing or replacing a plan/WBS artifact, check for an existing incomplete plan (unchecked tasks / open leaves). If different work is mid-build in another session, **stop and ask** — do not delete, overwrite, or rename on your own.

## Common mistakes

- Orphan requirements that never got a leaf.
- Invented leaves with no `C-SPEC` backing.
- Leaves too large for one agent (hide multiple deliverables).
- Placeholder leaves (TBD, "write tests later") or leaves missing empirical check / C-SPEC mapping.
- Building one WBS across independent subsystems instead of asking whoever authorized the work to split.

## Review checklist

- [ ] Slice does not span independent subsystems (or an authorized split obtained)
- [ ] Every C-SPEC unit in scope maps to ≥1 leaf
- [ ] Every leaf maps to ≥1 C-SPEC unit
- [ ] No TBD / "write tests later" placeholders
- [ ] Dependencies acyclic and explicit
- [ ] Each leaf has an empirical check
- [ ] Header: slice goal, audit SHAs/paths, global constraints verbatim
- [ ] Cross-cutting sweep recorded
- [ ] Work sliced vertically (end-to-end paths), not only horizontal layers
- [ ] Phases follow Setup → Foundational → per-story → Polish; parallel markers set
- [ ] XL items broken down; checkpoints every 2–3 tasks
- [ ] Existing incomplete plan/WBS not overwritten without asking
