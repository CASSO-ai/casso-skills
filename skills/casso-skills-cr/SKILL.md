---
name: casso-skills-cr
description: Use when authoring a Change Request work item — framing the request, drafting acceptance, and listing open ambiguities before impact analysis
---

# Change Request (casso-skills-cr)

> Portions adapted from anthropics/knowledge-work-plugins (change-request), Apache 2.0; modified by Novospir Ventures Inc.

## Overview

Author the Change Request for a change-request task: restate what is asked, why it matters, draft acceptance, and evidence pointers. This work item precedes impact analysis.

**Core principle:** Faithful scribe — record what was asked; do not invent scope.

Do not propose your own alternative approaches at this stage: record what was asked. Inventing options turns a request into a design decision the requester never made.

Do not unilaterally pick one reading of an ambiguity: list ambiguities for whoever authorized the work and do not fill them in.

**Method sources:** structured design exploration and elicitation after scribe rules; problem–solution intake shape from the project SDLC conventions.

## Preconditions

- Input comes from the task's problem and background and any authorizing directive in the brief.
- Say **work item** for pipeline activities.

## Process

### 1. Frame the request

Restate **WHAT HAPPENS**, **WHY IT MATTERS**, and **THE FIX** in problem–solution form. Lead with why it matters; keep mechanism under evidence.

### 2. Assess scope before detail

If the request spans multiple independent subsystems, flag decomposition for whoever authorized the work before drafting detailed acceptance.

### 3. Draft acceptance

Name observable acceptance checks the downstream pipeline can verify. Do not invent requirements the request did not state.

### 4. Honor the intake boundary

This work item authors the CR artifact bound to the task. Edits to the live spec need separate, explicit approval. Write the CR at the path named in the brief when one is given. Commit the CR artifact at the brief path so downstream agents can see it (project VCS policy).

### 5. Self-review before handoff

Before handoff, scan the CR for TBD/TODO, vague acceptance, and self-contradiction; fix or escalate — do not leave placeholders. Check WHAT/WHY/FIX/acceptance for internal contradiction before handoff.

### 6. Hand off to impact analysis

List open contradictions or ambiguities for whoever authorized the work before impact work proceeds. Do not resolve contradictions yourself. When listing open ambiguities for whoever authorized the work, ask **one** clarifying question per message (or per authorizing-party turn); do not dump an unanswered questionnaire.

### 7. Record requirement deltas against living specs

When the change touches authorized living specs, record the proposal as **deltas**, not a restatement of the whole domain:

- **ADDED** — new requirements (with at least one concrete checkable scenario each)
- **MODIFIED** — changed requirements (copy the full existing unit, then edit; keep prior wording noted)
- **REMOVED** — retired requirements (with reason; archive folds these back into the living set when authorized)

Deltas are planning artifacts for explicit authorization. Do not edit the live specs in this work item.

### 8. Rollback, approvals, and communication tables

Include these tables on the CR artifact when the change needs ops-style change management (deployments, process changes, multi-stakeholder rollouts):

| Table | Purpose |
|-------|---------|
| **Rollback** | Trigger, reverse steps, and verification that the rollback worked |
| **Approvals** | Approver, role, status (pending until whoever authorized the work or a named approver acts) |
| **Communication** | Audience, message, channel, timing |

Keep each row specific (who, when, how) — "everyone" is not an impact or audience.

### 9. Mid-stream course correction

When a significant change arrives **after** planning has started (specs, epics/WBS, architecture, or UX already in flight), produce a **sprint change proposal** that assesses impact across those artifacts and lists concrete edits per artifact. Hand off the proposal for explicit authorization before rewriting downstream work. Describe the technique generically — do not brand product features with third-party trademarks.

## Common mistakes

- Filling gaps with assumed requirements instead of asking whoever authorized the work.
- Leading with mechanism instead of why it matters.
- Skipping acceptance so later audits have nothing empirical to check.
- Dumping multiple unanswered clarifying questions in one message.
- Leaving TBD/TODO or vague acceptance in the handed-off CR.
- Drafting detailed acceptance across independent subsystems without flagging decomposition.

## Review checklist

- [ ] Problem–solution shape present (what happens, why it matters, the fix)
- [ ] Scope checked — multi-subsystem requests flagged for decomposition before detail
- [ ] Observable acceptance drafted
- [ ] No invented scope
- [ ] CR scanned for placeholders, vague acceptance, and internal contradiction
- [ ] Ambiguities listed for whoever authorized the work, not filled in
- [ ] At most one clarifying question per authorizing-party turn
- [ ] CR committed at the brief path (project VCS policy)
- [ ] Ready for the impact-analysis work item
- [ ] Requirement deltas recorded as ADDED/MODIFIED/REMOVED when living specs are touched
- [ ] Rollback / approvals / communication tables present when ops change-management applies
- [ ] Mid-stream changes produce a cross-artifact sprint change proposal before rewrites
