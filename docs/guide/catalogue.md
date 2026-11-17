# CASSO Skills catalogue

**The software development methodology for enterprise AI software engineering.**

CASSO Skills gives teams of AI agents a shared method for delivering enterprise software. The methodology spans the development lifecycle, from the first change request to a deployed release, with clear requirements, defined handoffs, independent reviews and evidence at every stage.

This page lists every skill in pipeline order. For how the skills fit together, start with the [README](../../README.md). Where a skill was extended from, or inspired by, skills in another open-source project, its row names that project.

**Audit skills and audit rubrics are in development.** Their links are marked **TBD (In Dev)**. See the [roadmap](../../README.md#11-roadmap) for planned additions.

## The 25 skills

Each row links the skill's method (`SKILL.md`) and its review rubric (`RUBRIC.md`). Rows are in pipeline order; skip any stage your change does not need.

| # | Skill | What it does | Goal, and how it goes beyond existing skills | Extended from or inspired by | Checked by |
|---|---|---|---|---|---|
|**Intake** ||||||
| 1 | **research**<br>[SKILL.md](../../skills/casso-skills-research/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-research/RUBRIC.md) | Investigates a question and returns findings, without touching product code | Covers any open question, not only debugging; the result is a findings report other stages can cite, and any trial code is thrown away | Superpowers, Spec Kit | Feeds the spec, which audit-spec [TBD (In Dev)] checks |
| 2 | **cr**<br>[SKILL.md](../../skills/casso-skills-cr/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-cr/RUBRIC.md) | Writes a change request: the problem, draft acceptance checks, and open questions | The agent records what was asked and lists the open questions for a person to settle, instead of proposing its own options or picking one reading | OpenSpec, Anthropic's knowledge-work-plugins | Feeds the spec, which audit-spec [TBD (In Dev)] checks |
| 3 | **impact**<br>[SKILL.md](../../skills/casso-skills-impact/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-impact/RUBRIC.md) | Rates the blast radius of a change (1-5) and lists every surface it touches | Forces "what breaks if this is wrong" before any spec or plan work, and surfaces contradictions with what already exists | pstack, code-change-impact, Anthropic's knowledge-work-plugins | Feeds the spec, which audit-spec [TBD (In Dev)] checks |
|**Spec** ||||||
| 4 | **spec**<br>[SKILL.md](../../skills/casso-skills-spec/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-spec/RUBRIC.md) | Writes spec units: one requirement, its why and why-not, and exactly one acceptance check | The agent writes down only what was decided and lists gaps instead of filling them, and every rejected alternative becomes a testable "must not" | Spec Kit | audit-spec [TBD (In Dev)] |
| 5 | **audit-spec**<br>TBD (In Dev) | Checks a spec against your foundation documents for staleness, contradictions and gaps | A fresh, committed audit report is required before any plan may cite the spec | Spec Kit | Its rubric |
| 6 | **consistency**<br>TBD (In Dev) | The shared three-stage method every audit uses: a quick pass, a claim-by-claim contradiction check, then a question-driven search for gaps | Brings published fact-checking methods (FActScore, Chain-of-Verification) to SDLC documents | OpenSpec, pstack | Used inside every audit |
|**Blueprint gate** ||||||
| 7 | **blueprint-branch-validate**<br>[SKILL.md](../../skills/casso-skills-blueprint-branch-validate/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-blueprint-branch-validate/RUBRIC.md) | Checks a documentation branch (specs, data model, design docs) merged onto what is already there | Brings merge-time checks from code to documents, catching conflicts between branches before they merge | Superpowers, Spec Kit | Its rubric; gates blueprint-branch-merge |
| 8 | **blueprint-branch-merge**<br>[SKILL.md](../../skills/casso-skills-blueprint-branch-merge/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-blueprint-branch-merge/RUBRIC.md) | Merges a validated documentation branch after the requirements owner approves the wording, and lists the plans, tests and code that rely on what changed | A merge bar for requirements rather than code: content approval, a re-check against documents merged since, and no reused or silently replaced requirement numbers | — | Its rubric; gated by blueprint-branch-validate |
| 9 | **blueprint-release-validate**<br>[SKILL.md](../../skills/casso-skills-blueprint-release-validate/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-blueprint-release-validate/RUBRIC.md) | Re-runs the structure checks on the merged documents before they are published | Treats documentation as a release with its own gate, and a check that could not run is reported as blocked | — | Its rubric; gates blueprint-release-publish |
| 10 | **blueprint-release-publish**<br>[SKILL.md](../../skills/casso-skills-blueprint-release-publish/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-blueprint-release-publish/RUBRIC.md) | Makes the exact validated documents the official version after approval, checks the published copy, and records what changed | Publishing moves the official version marker and records what changed; nothing is deployed. Earlier official versions are kept, and open work built on the old wording is flagged | — | Gated by blueprint-release-validate |
|**Design** ||||||
| 11 | **data-model**<br>[SKILL.md](../../skills/casso-skills-data-model/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-data-model/RUBRIC.md) | Turns an audited spec into a data model and data dictionary | Every entity and attribute traces back to a spec clause, and every clause forward to the model; a clause it cannot model goes back to the owner as a question | — | audit-data-model [TBD (In Dev)] |
| 12 | **audit-data-model**<br>TBD (In Dev) | Checks the model and dictionary against the spec, both ways, plus format rules | Catches invented entities and missing attributes before the work is broken down | — | Its rubric |
| 13 | **wbs**<br>[SKILL.md](../../skills/casso-skills-wbs/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-wbs/RUBRIC.md) | Breaks an approved part of the project into a work breakdown structure: every task needed to build it, in build order, each small enough for one agent | Every task maps to a requirement and carries its own check, with no "write tests later" | Superpowers, Spec Kit | audit-wbs [TBD (In Dev)] |
| 14 | **audit-wbs**<br>TBD (In Dev) | Checks that every requirement has a task and every task has a requirement | Run right after the WBS and again later, to prove nothing was dropped or invented | — | Its rubric |
|**Plan** ||||||
| 15 | **plan-code**<br>[SKILL.md](../../skills/casso-skills-plan-code/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-plan-code/RUBRIC.md) | Writes the implementation plan: file map, work items, and interface obligations | Every acceptance check maps to a work item, and scope the spec never asked for is flagged | Superpowers, Spec Kit | audit-plans [TBD (In Dev)] |
| 16 | **plan-tests**<br>[SKILL.md](../../skills/casso-skills-plan-tests/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-plan-tests/RUBRIC.md) | Writes the test plan: scenarios, negative cases and named proofs | Tests are planned as their own deliverable, and every forbidden behavior gets a scenario | Superpowers, Addy Osmani's agent-skills, Matt Pocock's skills | audit-plans [TBD (In Dev)] |
| 17 | **audit-plans**<br>TBD (In Dev) | Checks both plans against the spec and foundation documents | Checks coverage both ways and flags interface changes that need extra proof | OpenSpec, pstack | Its rubric |
|**Build** ||||||
| 18 | **impl-tests**<br>[SKILL.md](../../skills/casso-skills-impl-tests/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-impl-tests/RUBRIC.md) | Writes failing tests first, and stops before any product code | A separate step, so the tests that define done are written and checked before code exists | Superpowers, Addy Osmani's agent-skills, Matt Pocock's skills | audit-tests [TBD (In Dev)] |
| 19 | **audit-tests**<br>TBD (In Dev) | Checks the test scripts against the test plan, both ways | Proves every planned scenario has a test that can actually fail | — | Its rubric |
| 20 | **impl-code**<br>[SKILL.md](../../skills/casso-skills-impl-code/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-impl-code/RUBRIC.md) | Writes the product code that makes those tests pass, then refactors and self-reviews | The scope is limited to the assigned spec units | Superpowers, Addy Osmani's agent-skills, Matt Pocock's skills | audit-code [TBD (In Dev)] |
| 21 | **audit-code**<br>TBD (In Dev) | Three-way check of spec, plan and code (with tests) | One report ties every requirement to the plan line, the code and the test that prove it | OpenSpec, pstack | Its rubric |
|**Ship** ||||||
| 22 | **branch-validate**<br>[SKILL.md](../../skills/casso-skills-branch-validate/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-branch-validate/RUBRIC.md) | Tests a feature branch merged onto current main: full regression, named new tests, mutation proofs | A test only counts once it has been shown to fail when the code is broken | Superpowers, Addy Osmani's agent-skills | Its rubric; gates branch-merge |
| 23 | **branch-merge**<br>[SKILL.md](../../skills/casso-skills-branch-merge/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-branch-merge/RUBRIC.md) | Records a merge after approval, and confirms the merged result is exactly what was validated | No approval, no merge, and no silently swapping in a different version | Addy Osmani's agent-skills | Gated by branch-validate |
| 24 | **release-validate**<br>[SKILL.md](../../skills/casso-skills-release-validate/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-release-validate/RUBRIC.md) | Runs full regression and every release check on the exact version to be deployed | Covers the whole release; a check that could not run is reported as blocked, never passed | Superpowers, EthicalML's agent-skills-marketplace | Its rubric; gates release-deploy |
| 25 | **release-deploy**<br>[SKILL.md](../../skills/casso-skills-release-deploy/SKILL.md) · [RUBRIC.md](../../skills/casso-skills-release-deploy/RUBRIC.md) | Deploys after approval, exactly the validated version, then checks the live result | The deployed version must equal the validated one, and the live result is checked after deploy | EthicalML's agent-skills-marketplace | Gated by release-validate |

Credits name the projects at family level. Each project's copyright and license text is in [NOTICE.md](../../NOTICE.md).

## Review rubrics

Each skill uses a **review rubric** in its `RUBRIC.md`, or the shared [GENERIC-RUBRIC.md](../../GENERIC-RUBRIC.md) if it has none of its own. On every dispatch, a reviewer reads the finished work, the skill's `SKILL.md` and its `RUBRIC.md`, and marks each line pass or fail with evidence: a file path and line, command output, a test name, a commit, or quoted text. The BA agent's description of the work is not enough on its own. Each review reports a **usable score** using these bands:

- **Usable: 80-100%.** The required steps were followed, the work includes supporting evidence, any limits are stated, and the changes are committed.
- **Partly usable: 40-75%.** Some parts need improvement, with the reasons identified in the checklist.
- **Not usable: 0-35%.** The output does not adequately follow the brief or the skill.

The usable score is a percentage in steps of 5, with one line naming the deductions applied. Declaring a limitation honestly ("I could not complete X because Y") does not itself cost points. The report must still make clear which checks could not be completed. **Work with a usable score under 100% is rewritten, not argued over:** see [Dispatching one step by hand](../../README.md#step-3-usable-score-under-100-write-a-new-brief).

**Audit rubrics** (TBD (In Dev)) will give a spec, plan or code work item a separate **readiness score**: how much of the work item is ready as it is, with no further work or rework. See [Why every output is scored against a rubric](../../README.md#5-why-every-output-is-scored-against-a-rubric).

## What checks each skill

Every dispatch's output is checked against a review rubric and receives a usable score. Independent audits, which check a work item against its requirements and the work from earlier stages, are in development.

| Writes | Checked by |
|---|---|
| spec | audit-spec [TBD (In Dev)] |
| data-model | audit-data-model [TBD (In Dev)] |
| wbs | audit-wbs [TBD (In Dev)] |
| plan-code, plan-tests | audit-plans [TBD (In Dev)] |
| impl-tests | audit-tests [TBD (In Dev)] |
| impl-code | audit-code [TBD (In Dev)] |
| a feature branch | branch-validate, before branch-merge |
| a release candidate | release-validate, before release-deploy |
| a documentation branch | blueprint-branch-validate, before blueprint-branch-merge |
| a documentation release | blueprint-release-validate, before blueprint-release-publish |

The research, cr and impact skills provide the information needed to write the specification.

## The blueprint gate

Once the specification is written and reviewed, the requirements go through their own merge and release, before anyone plans from them:

1. **[blueprint-branch-validate](../../skills/casso-skills-blueprint-branch-validate/SKILL.md)** checks the documentation branch merged onto what is already there.
2. **[blueprint-branch-merge](../../skills/casso-skills-blueprint-branch-merge/SKILL.md)** merges it once the requirements owner approves the wording, and lists the plans, tests and code that rely on what changed.
3. **[blueprint-release-validate](../../skills/casso-skills-blueprint-release-validate/SKILL.md)** re-runs the structure checks on the merged documents.
4. **[blueprint-release-publish](../../skills/casso-skills-blueprint-release-publish/SKILL.md)** makes that exact version the official one and records what changed since the last one.

**Why:** the requirements are what every later stage is built from. A plan built on unmerged or still-changing requirements has to be redone when they change, and on a large team two branches can change the same requirement without either noticing. Merging and publishing them as a numbered official version means every agent plans and builds from the same, current wording, and anything built on a requirement that later changes is flagged for re-check instead of silently drifting.

## The work breakdown structure

The **work breakdown structure (WBS)** turns an approved change into tasks. The [wbs](../../skills/casso-skills-wbs/SKILL.md) skill breaks the approved requirements into tasks small enough for an agent to complete. Each task links back to a requirement, says how it will be checked, and identifies any tasks that must finish first, so a task with no open dependency can start and independent tasks can run at the same time. There are no placeholder tasks and no "write the tests later" task. Planning, building and merging then happen for each task. See [Scaling the workflow](../../README.md#7-scaling-the-workflow) for what that means as the number of tasks grows.

## Building on Superpowers

CASSO Skills builds on [Superpowers](https://github.com/obra/superpowers), which is the base for many of these skills, and extends it for a team of agents working across many tasks at once. What that adds is described in [Building on Superpowers](../../README.md#9-building-on-superpowers).
