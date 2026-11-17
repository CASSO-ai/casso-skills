---
name: casso-skills-impact
description: Use when assessing blast radius and touched surfaces for a Change Request before spec or plan work — classifies the change and surfaces contradictions for whoever authorized the work
---

# Impact Analysis (casso-skills-impact)

> Portions adapted from anthropics/knowledge-work-plugins (change-request), Apache 2.0; modified by Novospir Ventures Inc.

## Overview

Analyze the authorized Change Request: classify the change, enumerate touched surfaces, estimate blast radius, and surface contradictions for whoever authorized the work to adjudicate before spec or plan work.

**Core principle:** Compare against the whole relevant artifact set — authorized functional specs, decision rulings, and cited code — not only the CR text.

## Preconditions

- CR work item complete.
- When the analysis names hosts, filesystems, or toolchains, read the project's measured host-facts reference before asserting them.

## Process

### 1. Classify and enumerate

List every spec domain, module, migration, CLI surface, and cross-cutting class the change touches (error handling, logging, auth, migrations, observability, CLI output, security).

If enumeration shows multiple independent subsystems, recommend separate impact/spec slices to whoever authorized the work before deep detail.

### 2. Blast radius

Record a judged **blast_radius_level** (1–5) on the task. State what breaks if the change is wrong.

### 3. Contradictions and clarifications

Raise load-bearing conflicts to whoever authorized the work; do not auto-resolve. Record any routing choice for minor clarifications explicitly.

If tempted to auto-resolve a conflict to keep moving, STOP and re-enumerate surfaces from sources.

When contradictions involve code, note recent commits/diffs on cited paths as evidence pointers.

### 4. Output artifact

Produce an impact-analysis document outside the live spec tree. Use the path named in the brief.

### 5. Prove the one safety fact by running code

A writeup alone is worthless for the load-bearing safety claim. Find the one or two facts the change's safety depends on and prove them by running code (small script or test that imports the real library / calls the real path). Mark unproven when you cannot run it.

**Certainty ladder** (state where each fact stopped):

1. Self-said — worthless alone
2. `file:line` citation
3. Walked the failure path and showed it cannot reach
4. Ran it (script/test against real code)
5. Reproduced in the running app

Prefer step 4 when cheap.

### 6. Coupling-class taxonomy and verdict

Classify each changed surface by coupling class; that sets blast reach:

| Coupling class | Typical reach |
|----------------|---------------|
| Shared util / core helper | Wide — every importer |
| Public API / exported symbol | Callers in and out of the module |
| Schema / type / interface | Wide; silent in dynamic languages |
| Wire contract (REST/DTO/proto/event) | Cross-service |
| Config / registry / feature flags | Fan-out to derived behavior |
| Leaf-internal change | Local |

Emit a verdict: **SAFE** / **SAFE WITH CAVEATS** / **IMPACT FOUND**. Caveats name residual unrun checks; IMPACT FOUND names the broken consumer or twin.

### 7. Users / Systems / Processes / Cost grid

For non-code or ops-facing surfaces, fill an impact grid:

| Area | Impact (High/Med/Low/None) | Details |
|------|----------------------------|---------|
| Users | | Who is affected and how |
| Systems | | What systems change |
| Processes | | What workflows change |
| Cost | | Budget / capacity impact |

### 8. Cross-artifact impact (mid-sprint)

When the change lands mid-sprint, also map impact onto PRD/CR acceptance, epics/WBS leaves, architecture notes, and UX artifacts. Feed that map into the sprint change proposal on the CR path when one is required.

## Common mistakes

- Treating the CR alone as the whole picture.
- Auto-resolving contradictions to keep moving.
- Naming host or toolchain facts without checking measured host facts.
- Pushing deep detail before recommending separate slices for independent subsystems.

## Review checklist

- [ ] Surfaces enumerated across domains and cross-cutting classes
- [ ] Multi-subsystem independence flagged with separate-slice recommendation when present
- [ ] Blast radius recorded with consequence stated
- [ ] Authorizing-party contradictions surfaced, not resolved
- [ ] Recent commits/diffs noted when code contradictions are cited
- [ ] No live-spec edits without explicit authorization
- [ ] Artifact path matches the brief (or stated limit if none was named)
- [ ] Load-bearing safety fact proven by running code, or marked unproven
- [ ] Certainty ladder stated for each safety-critical fact
- [ ] Coupling classes assigned; verdict SAFE / SAFE WITH CAVEATS / IMPACT FOUND
- [ ] Users/Systems/Processes/Cost grid filled when non-code surfaces apply
- [ ] Mid-sprint changes map impact across PRD/epics/architecture/UX
