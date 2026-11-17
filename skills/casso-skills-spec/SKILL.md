---
name: casso-skills-spec
description: Use when authoring functional spec units — WHYs, WHY-NOTs, and C-SPEC units with exactly one acceptance check each — before plan work
---

# Spec Authoring (casso-skills-spec)

## Overview

Author or propose spec changes as **C-SPEC units**. Propose under the project's proposed-spec area until whoever owns the spec approves promotion to the live spec tree.

**Core principle:** Faithful scribe — transcribe authorized decisions; one spec ↔ one `[CHECK]`.

Do not propose your own alternative approaches at this stage: record what was asked. Inventing options turns a request into a design decision the requester never made.

Do not unilaterally pick one reading of an ambiguity: list ambiguities for whoever authorized the work and do not fill them in.

**Method sources:** structured design exploration and elicitation after scribe rules; Project WBS method §3.5.1 and §3.5.5 (unit format).

## Preconditions

- Impact analysis complete for the slice.
- Read the project's WBS/spec-format method before writing.

## Process

### 1. Mint IDs

> Every spec id must be unique, and never reused or renumbered. If you use CASSO Rex, run `casso rex get spec id --project <project-short-code>`. Otherwise keep a file in your project's git repository that lists the ids already used: take the next number, add it to the file, and push (**push** = save commits to the shared repository remote). If the push is rejected because someone else pushed first, pull and take the next number again.

### 2. Assess scope before hardening

If units span independent subsystems, flag decomposition before hardening prose.

### 3. Write each unit

- `[C-SPEC-<PROJECT>-<n>]` on its own line, then the requirement, then exactly one `[CHECK]`.
- Context lines start with `[WHY]` / `[WHY-NOT]` / `[COUNTEREXAMPLE]` / `[EXAMPLE]` / `[NOTE]` at line start only.
- Build and test obligations attach to requirement + `[CHECK]` only.

### 4. Propose, do not canonize

File drafts under the proposed area; never treat an unauthorized edit of the live spec tree as done work. Commit proposed-spec drafts per project VCS policy so audit-spec [TBD (In Dev)] can see them.

### 5. No inventing

Ambiguity → ask whoever authorized the work. Contradiction → surface, never auto-resolve.

When authorized decisions leave architecture/data-flow/error/testing uncovered for the slice, list those gaps for whoever authorized the work rather than inventing units.

### 6. Self-review before proposing

Before filing, scan for TBD/TODO/incomplete units and vague `[CHECK]` text; fix or escalate. Check new units do not contradict each other or cited authorized rulings before filing. After drafting, run placeholder / consistency / scope / ambiguity checks inline before proposing.

### 7. Consult non-negotiables (constitution)

Before hardening units, consult the project's written non-negotiables / constitution (coding standards, testing bar, UX consistency, performance). Later phases are evaluated against those principles. If none exist, record that gap for whoever authorized the work rather than inventing policy.

### 8. Clarify loop before plan handoff

When the draft still has material ambiguity, run a clarify loop of **at most five** targeted questions total, **one question per authorizing-party turn**, encode each answer back into the proposed units, and stop the turn for the answer. Repeat only after answers land. Do not unilaterally pick a reading.

### 9. Constraints quality bar

When the project maintains a constraints / quality-bar document, ensure proposed requirements do not silently weaken it. Prefer checks with a stated cost and a place they run (edit-time / task-done / CI). Point at the existing bar; do not invent a second conflicting one.

## Common mistakes

- Unlabelled prose that reads like a requirement (format error).
- Two independent checks stuffed into one unit.
- Inventing ids instead of minting them.
- Hardening prose across independent subsystems without flagging decomposition.
- Leaving TBD/TODO or vague `[CHECK]` text in proposed drafts.
- Inventing architecture/data-flow/error/testing units that were never authorized.

## Review checklist

- [ ] Each unit has exactly one `[CHECK]`
- [ ] Markers at line start; unlabelled requirement-shaped prose flagged
- [ ] Spec ids unique; minted via `casso rex get spec id` or the project's id ledger file per Process §1
- [ ] Scope checked — multi-subsystem spans flagged before hardening
- [ ] Draft only under proposed until explicit authorization
- [ ] Proposed drafts committed per project VCS policy
- [ ] Placeholder / consistency / scope / ambiguity self-review done
- [ ] Architecture/data-flow/error/testing gaps listed for whoever authorized the work, not invented
- [ ] Project non-negotiables consulted (or gap recorded)
- [ ] Clarify loop ≤5 targeted questions used when ambiguity remains; answers encoded into units
- [ ] Constraints / quality bar not weakened; cost-placed checks respected
