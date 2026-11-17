---
name: casso-skills-research
description: Use when running a research work item — investigation that produces findings as an external oracle; read-only toward product code unless the brief explicitly allows a harness
---

# Research (casso-skills-research)

## Overview

Investigation that produces findings. Research is an **external oracle**: it can disagree with assumptions, prior reports, and even the brief's hoped-for answer.

**Core principle:** Measure, cite, and separate observation from inference. A research work item does not silently become implementation.

**Method sources:** systematic root-cause investigation before proposing fixes; Project research-folder conventions; project research brief conventions.

## Preconditions

- The work item is categorized as research (read-only investigation).
- Scope and questions are named on the brief or task.

## Process

### 1. Frame the questions

Write the questions the investigation must answer. Prefer falsifiable questions over open narrative.

### 2. Gather primary evidence

Read the named sources. Prefer primary artefacts (logs, commands you run, file contents, measured host facts) over summaries. Record exact commands and outputs you rely on.

When tracing a defect or behavior: list every difference vs a working reference; trace bad values to origin; do not stop at the first symptom site.

### 3. Hypotheses one at a time

State one hypothesis at a time; change one variable; if disproved, form a new hypothesis — do not stack untested theories in Recommendations.

### 4. Separate layers

In the write-up, label **Observation**, **Inference**, and **Recommendation** distinctly. Never present an inference as a measurement.

### 5. Positive-control absences

Before claiming something is absent, show the same matcher finding a known-present control. Wrong patterns print nothing and look like a clean result.

### 6. File the findings

Write findings under the project's research tree (or the path the brief names). Include: questions, method, evidence, limits, and open questions for whoever authorized the work.

### 7. Stop at research

Do not expand into product code changes unless the brief explicitly authorizes a throwaway harness under the spike area. Harnesses stay throwaway until a separate pipeline promotes them.

### 8. Idea assessment pipeline (when the ask is an idea)

When researching whether to pursue an idea, walk **intake → research → define → shape → decide** and end with an explicit verdict: `go` / `needs-clarification` / `kill`. Keep assessment artifacts separate from delivery specs; a go verdict still requires explicit authorization before spec work.

## Common mistakes

- Treating a peer's report as independent corroboration without checking identity.
- Skipping the positive control on an absence claim.
- Quietly implementing a fix inside a research work item.
- Stopping at the first symptom site without listing differences vs a working reference.
- Stacking multiple untested theories in Recommendations.

## Review checklist

- [ ] Questions stated up front
- [ ] Primary evidence cited (commands/outputs/paths)
- [ ] Defect/behavior traces list differences vs a working reference and follow values to origin
- [ ] One hypothesis at a time; Recommendations free of stacked untested theories
- [ ] Observation / inference / recommendation separated
- [ ] Absence claims have a positive control
- [ ] Limits and open questions for whoever authorized the work listed
- [ ] No unauthorized product code changes
- [ ] Idea assessments follow intake→research→define→shape→decide with an explicit verdict
