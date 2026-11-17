# CASSO Skills

**The software development methodology for enterprise AI software engineering.**

CASSO Skills gives teams of AI agents a shared method for delivering enterprise software. The methodology spans the development lifecycle, from the first change request to a deployed release, with clear requirements, defined handoffs, independent reviews and evidence at every stage.

As AI takes on more of the work, coordinating and checking that work matters more. CASSO Skills defines what each stage should produce, how it will be checked, and when it is ready to move forward.

The methodology is open source and independent of any coordinator. Use individual skills in your existing workflow, coordinate the available skills with an orchestrator of your choice, or use [CASSO Rex](#10-casso-rex-the-sdlc-coordinator), the SDLC coordinator we are building to manage the work at scale.

**Audit skills and audit rubrics are in development.** Their links are marked **TBD (In Dev)**. See the [roadmap](#11-roadmap) for planned additions.

- [**Install**](INSTALL.md): how to add the skills to Claude Code, Codex, Cursor, Grok, GitHub Copilot, Antigravity or OpenCode.
- [**Skills catalogue**](docs/guide/catalogue.md): skills in pipeline order, with their rubrics, checks and credits.

## Table of contents

1) [Mission](#1-mission)
2) [How we got here](#2-how-we-got-here)
3) [Great Software Takes More Than a Great AI](#3-great-software-takes-more-than-a-great-ai)
4) [How the pieces fit together](#4-how-the-pieces-fit-together)
5) [Why every output is scored against a rubric](#5-why-every-output-is-scored-against-a-rubric)
6) [The basic workflow](#6-the-basic-workflow)
7) [Scaling the workflow](#7-scaling-the-workflow)
8) [Dispatching one step by hand](#8-dispatching-one-step-by-hand)
9) [Building on Superpowers](#9-building-on-superpowers)
10) [CASSO Rex: the SDLC coordinator](#10-casso-rex-the-sdlc-coordinator)
11) [Roadmap](#11-roadmap)
12) [Install](#12-install)
13) [Skills catalogue](#13-skills-catalogue)
14) [Open source and community](#14-open-source-and-community)
15) [Credits and license](#15-credits-and-license)

## 1. Mission

Our mission is to help teams turn growing AI capability into software they can confidently release.

That takes a shared engineering method across the entire lifecycle. Requirements need clear ownership. Tasks need a clear order. Work needs independent review. Each stage needs clear rules for when the work is ready to move forward.

CASSO Skills is that method, published openly so teams can inspect it, use it, adapt it and help improve it.

[CASSO Rex](#10-casso-rex-the-sdlc-coordinator) is the SDLC coordinator we are building around it. For example, a lead agent coordinates a team whose members take on planning, implementation and review. Responsibility rests with the team, with distinct roles and checks throughout the work. CASSO Rex is an extension to Claude Code that gives Claude Code the ability to implement enterprise-class software engineering projects. CASSO Rex also lets Claude Code coordinate agents across Codex, Cursor, GitHub Copilot, Grok, Antigravity and OpenCode.

The goal is to let enterprise engineers focus on the business and technical requirements while AI does everything else that's needed to implement it properly.

## 2. How we got here

When we first started to use AI to write code, it felt extraordinary how much more we could accomplish in a day.

[Superpowers](https://github.com/obra/superpowers), created by Jesse Vincent, was an important part of that journey. We used it, learned from it and benefited from the discipline it brought to AI development. Much of CASSO Skills builds on that foundation, and we are grateful for it.

As we expanded, the coordination work grew with us. More agents meant more tasks underway, more dependencies to track, more reviews to arrange and more issues to follow through until they were resolved. Driving the process manually, step by step, was becoming a job of its own.

The bottleneck had moved. AI could take on more work than we could sustainably coordinate by hand.

That experience shaped CASSO Skills. We wanted to carry the discipline we had learned into a workflow that a coordinator could manage across many agents and many tasks. As agents become more capable, the surrounding system needs to give them clear responsibilities, reliable handoffs and rigorous checks.

For enterprise software engineering, that means:

- **Requirements with clear ownership.** Agents record decisions and surface unanswered questions. A gap stays a question until the requirements owner resolves it.
- **Independent checks backed by evidence.** A separate agent checks the work against published criteria and provides evidence for its findings.
- **One connected lifecycle.** Change requests, specifications, plans, tests, implementation and releases use the same terms, with clear links between the stages.
- **Coordination that can scale with the work.** Task status, dependencies, instructions, reviews and revisions are recorded so an orchestrator can manage the work.
- **An open foundation.** Teams can use the methodology with their own coordinator, adapt another orchestrator or use [CASSO Rex](#10-casso-rex-the-sdlc-coordinator).

We are publishing CASSO Skills because open source helped us get here, and we want to contribute to what comes next.

## 3. Great Software Takes More Than a Great AI

AI gives us something remarkable: development, architecture, debugging and review expertise within the same team of agents. The challenge is making sure each kind of expertise gets its turn. An agent that can explain an architectural principle may still overlook it while implementing a feature.

Think about writing an important email. You choose your words carefully, finish the message, and then read it back. Suddenly, you notice mistakes, missing details or a sentence that does not say what you intended. You already had the knowledge to spot those problems. Looking at the work as an editor brought them into focus.

CASSO Skills applies that separation deliberately. We give agents distinct responsibilities for doing the work, reviewing it for completeness and auditing it for correctness. Each role has a clear purpose and a checklist. Asking an agent to "do the work and check it" becomes a structured process in which the checks are assignments of their own.

Before spending time checking whether the work is right, we first check that all the required work is there. Think of a student handing in a test. Before grading it, the teacher scans it to make sure every question has been answered, every section is complete, and the student has shown their working where required. If something was accidentally skipped, the teacher can hand it back. Grading the answers comes next.

The completeness review serves the same purpose. Using the review rubric, the reviewer checks that the agent addressed every part of the assignment, produced the required outputs and included the requested evidence. If the assignment asks for three things and only two were delivered, the work goes back with clear instructions about what is missing.

The audit is the deeper examination. It checks whether the work satisfies the requirements, whether the decisions and implementation are correct, and whether the evidence supports the conclusions. A plan can include every requested feature but describe behavior that does not match what was agreed.

An audit is a full dispatch that examines the work independently and in detail. Catching missing pieces during the quicker review lets us spend that effort on work that is ready for examination, instead of repeating an intensive audit after basic omissions are fixed.

The audit itself goes through a completeness review too. The reviewer checks that the auditor covered every required part of the work, performed the required checks and provided evidence for its findings. If anything was skipped, the audit goes back for completion. A clean audit result only counts once the audit itself passes its review.

These checks form a loop: do the work, review its completeness, audit its correctness, and review the audit. Findings become clear instructions for the next dispatch. Revised work goes through the relevant checks again, and the cycle continues until the required checks pass and the recorded findings are resolved. This is how we turn AI's ability to spot mistakes into a systematic process for finding and fixing them.

Questions are part of that process. If an agent finds a contradiction, a missing requirement or an uncertainty that affects what it should build, it stops and asks the person responsible for the decision. Work that depends on the answer waits. The agent is explicitly told not to invent an answer: its role is to implement the agreed requirements, and the requirements owner decides what they mean. A guess can become the foundation for plans, code and later decisions, making it much harder to undo than to clarify at the start.

The goal is to give each capability room to do its job: focused implementation, a quick completeness review, a thorough audit and clear answers when something is uncertain. Together, they make careful engineering a repeatable team process for AI.

## 4. How the pieces fit together

The workflow uses the building blocks below.

| **Piece**       | **What it is**                                                                                                    | **Where it lives**                          |
| --------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| **Skill**       | A written method an agent follows for one stage, for example "write the requirements" or "write the tests first". | `skills/casso-skills-<name>/SKILL.md`       |
| **Audit skill** | An independent check of a work item against its requirements and the work from earlier stages. | TBD (In Dev) |
| **Review rubric** | A numbered checklist used by the reviewer on every dispatch to assign a usable score to its output, with evidence. | `RUBRIC.md` in the skill folder, or the shared review rubric |
| **Audit rubric** | A checklist the auditor uses to assign a readiness score to a spec, plan or code work item. | TBD (In Dev) |
| **Brief**       | The instructions given to an agent: the goal, source material, where to save the work and any limits.               | Written by your AI Agent             |

A **dispatch** is one assignment to an agent to carry out a skill. Each dispatch follows the same pattern:

1.) A **brief** sends the work to a BA (business analysis) agent, which follows the stage's **skill**.
2.) The BA agent saves the work in files and commits it to Git. The result must be available for another agent to check.
3.) A second agent evaluates the output against the **review rubric** and assigns a **usable score**.
4.) A usable score under 100% leads to a new brief, revision and another review.
5.) At 100%, the dispatch's output passes its review. The work moves forward once all checks and approvals for that stage are satisfied.

## 5. Why every output is scored against a rubric

A rubric is a checklist that gives reviewers a shared standard. It says what to check and what evidence to provide. This makes reviews more consistent and helps resolve disagreements by looking at the work.

The two checklists answer different questions:

| Checklist | Who uses it | Its percentage is called | What the percentage means |
| --- | --- | --- | --- |
| Review rubric | The reviewer, on every dispatch | Usable score | "How much of this dispatch's output is usable?" |
| Audit rubric | The auditor, on a spec, plan or code work item | Readiness score | "How much of this work item is ready as it is, with no further work or rework?" |

An audit is also a dispatch, and its report gets reviewed too. The reviewer checks whether the auditor completed the required checks and supported the findings with evidence. The report's usable score is separate from the work item's readiness score. A fully usable audit report can correctly conclude that the work is not ready.

The score ranges and revision rule below apply to the **usable score**.

Each skill uses a **review rubric** in `RUBRIC.md`, or the shared rubric linked below. The reviewer reads the finished work, the skill's `SKILL.md` and its `RUBRIC.md`, and marks each line pass or fail with evidence: a file path and line, command output, a test name, a commit, or quoted text. The BA agent's description of the work is not enough on its own. Each review reports a usable score using these bands:

- **Usable: 80-100%.** The required steps were followed, the work includes supporting evidence, any limits are stated, and the changes are committed.
- **Partly usable: 40-75%.** Some parts need improvement, with the reasons identified in the checklist.
- **Not usable: 0-35%.** The output does not adequately follow the brief or the skill.

The usable score is a percentage in steps of 5, with one line naming the deductions applied. Declaring a limitation honestly ("I could not complete X because Y") does not itself cost points. The report must still make clear which checks could not be completed. **Work with a usable score under 100% is rewritten, not argued over.** A skill with no review rubric of its own uses [GENERIC-RUBRIC.md](GENERIC-RUBRIC.md).

The usable score tells you how much of a dispatch's output can be used. The readiness score tells you how much of the work item is ready as it stands.

## 6. The basic workflow

The research, cr and impact skills provide the information needed to write the specification. Every dispatch is checked against a review rubric and receives a usable score. Research is optional, and the data-model stages apply only when stored data changes. The table shows how the stages fit together.

| **Stage**                 | **Writes**                                                                                                                                                                                                                                                                                                                            | **Checked by**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | **Dispatches**                                                      |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| 1. Learn first (optional) | [research](skills/casso-skills-research/SKILL.md)                                                                                                                                                                          | feeds the spec                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | once per question                                             |
| 2. Frame the change       | [cr](skills/casso-skills-cr/SKILL.md), then [impact](skills/casso-skills-impact/SKILL.md)                       | feeds the spec                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | once per change                                               |
| 3. Describe what to build | [spec](skills/casso-skills-spec/SKILL.md)                                                                                                                                                                                  | TBD (In Dev)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | once per change                                               |
| 4. Blueprint gate         | the merged, published requirements                                                                                                                                                                                                                                                                                                    | [blueprint-branch-validate](skills/casso-skills-blueprint-branch-validate/SKILL.md) → [blueprint-branch-merge](skills/casso-skills-blueprint-branch-merge/SKILL.md) → [blueprint-release-validate](skills/casso-skills-blueprint-release-validate/SKILL.md) → [blueprint-release-publish](skills/casso-skills-blueprint-release-publish/SKILL.md) | once per documentation release                                |
| 5. Design                 | [data-model](skills/casso-skills-data-model/SKILL.md)                                                                                                                                                                      | TBD (In Dev)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | once per approved part                                        |
| 6. Break down             | [wbs](skills/casso-skills-wbs/SKILL.md)                                                                                                                                                                                    | TBD (In Dev)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | once per approved part; again when tasks change |
| 7. Plan                   | [plan-code](skills/casso-skills-plan-code/SKILL.md), [plan-tests](skills/casso-skills-plan-tests/SKILL.md)      | TBD (In Dev)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | **for every task**                                            |
| 8. Build                  | [impl-tests](skills/casso-skills-impl-tests/SKILL.md), then [impl-code](skills/casso-skills-impl-code/SKILL.md) | TBD (In Dev)                                                                                                                                                                                                                                                                                                                                                                                                                                                          | **for every task**                                            |
| 9. Merge                  | the feature branch                                                                                                                                                                                                                                                                                                                    | [branch-validate](skills/casso-skills-branch-validate/SKILL.md) → [branch-merge](skills/casso-skills-branch-merge/SKILL.md)                                                                                                                                                                                                                                                                                                                                                                                                                                             | **for every task**                                            |
| 10. Release               | the release candidate                                                                                                                                                                                                                                                                                                                 | [release-validate](skills/casso-skills-release-validate/SKILL.md) → [release-deploy](skills/casso-skills-release-deploy/SKILL.md)                                                                                                                                                                                                                                                                                                                                                                                                                                       | once per release                                              |

The **blueprint gate** is the checkpoint where requirements are approved and published for the team to use. Every later stage builds on them. Publishing a numbered version keeps agents working from the same requirements. If a requirement changes, the work based on it needs to be checked again.

The **work breakdown structure (WBS)** turns an approved change into tasks. The [wbs](skills/casso-skills-wbs/SKILL.md) skill breaks the approved requirements into tasks small enough for an agent to complete. Each task links back to a requirement, says how it will be checked, and identifies any tasks that must finish first. Planning, building and merging then happen for each task. Release checks cover the combined work.

## 7. Scaling the workflow

Today, one developer coordinates this workflow within their own development environment. Connecting that work to a shared CI/CD process is part of the [roadmap](#11-roadmap).

You can dispatch each CASSO Skills skill yourself. That is a useful way to learn the method, deliver a small change or bring selected skills into an existing process.

As the number of tasks and agents grows, coordinating every step manually becomes difficult to sustain. The work breakdown structure is where that becomes visible: one approved change can become dozens of tasks, each with its own dependencies, plans, tests, implementation, reviews and merge checks.

A coordinator needs to manage:

- **Task records.** Keep each task's ID, status, related requirement, checks and dependencies available across agent sessions.
- **Work in the right order.** A task can start when the tasks it depends on have been merged. Independent tasks can proceed at the same time.
- **Follow each task through.** Each task needs planning, tests, code, checks and a merge. Every dispatch gets a separate review, with another dispatch when revisions are needed. The coordination work grows with every task.
- **Review and rework.** Turn findings into clear instructions, send the work back to the BA agent, and have the updated work reviewed again.
- **Changes to requirements.** When an approved requirement changes, work based on the earlier version needs to be identified and rechecked.
- **Clear instructions.** Give each agent the goal, source material, where to save the result, any limits and the decisions already made.

These responsibilities are part of the engineering process. A missed dependency, a lost finding or a skipped review can undermine the checks the methodology puts in place.

This is the role of an **SDLC coordinator**: track progress, coordinate the agents and guide each task through the required stages and checks.

CASSO Skills defines the method. Your coordinator manages the work. Any orchestrator that can give agents the right instructions, track task status and manage the steps can take that role. You can build one yourself, adapt an existing system or use [CASSO Rex](#10-casso-rex-the-sdlc-coordinator).

The skills are open so that this choice remains yours.

## 8. Dispatching one step by hand

This example follows one dispatch on a small change: a BA agent writes the requirements, a reviewer checks them against the review rubric, and a usable score under 100% leads to another dispatch with instructions for what to fix.

**The example.** You manage a small online shop. A support lead writes: *"Customers keep asking for discount codes. Let them type a code at checkout and get the discount. Codes should expire."* You have already used [cr](skills/casso-skills-cr/SKILL.md), which wrote `docs/changes/discount-codes-cr.md` and asked you its open questions. You answered: "percentage only, one code per order".

You need two agent sessions: a **BA agent** and a **reviewer**. They can use the same tool, but the reviewer must not be the session that wrote the work.

### Step 1: The BA agent writes the work

Paste into the BA agent session:

```
Use casso-skills-spec.

Goal: write requirements for the discount-code change.
Input: docs/changes/discount-codes-cr.md
Requester's answers: percentage only; one code per order.
Output: docs/specs/proposed/discount-codes.md, committed on branch spec-discount-codes.
Limits: write only what the change request and the answers say. If anything is
unclear, ask me; do not fill the gap yourself.
When done, report the file, the commit, and any open questions.

```

Suppose the draft contains these four requirements:

```
[C-SPEC-SHOP-1]
At checkout, a valid code reduces the order total by the code's percentage.
[CHECK] An order of 50.00 with a valid 10% code totals 45.00.

[C-SPEC-SHOP-2]
An expired code is refused and the order total is unchanged.
[CHECK] An order of 50.00 with a code that expired yesterday totals 50.00 and shows "code expired".

[C-SPEC-SHOP-3]
An order accepts at most one code.
[CHECK] Entering a second valid code on an order that already has one is refused.

[C-SPEC-SHOP-4]
Codes are not case-sensitive.
[CHECK] "SAVE10" and "save10" apply the same discount.
```

### Step 2: The reviewer assigns a usable score against the review rubric

Paste into the reviewer session:

```
Review this dispatch's output against a CASSO Skills review rubric.

Skill: skills/casso-skills-spec/SKILL.md
Review rubric: skills/casso-skills-spec/RUBRIC.md
Work: docs/specs/proposed/discount-codes.md on branch spec-discount-codes
Brief the BA agent was given: <paste the Step 1 brief>
Source the work must stay within: docs/changes/discount-codes-cr.md

For each numbered rubric line, give PASS or FAIL with evidence: a file path and
line, a commit, command output or quoted text. Do not accept the BA agent's summary
as evidence. Then give the usable score as a percentage in steps of 5, and one line naming the
numbered deductions you applied. Do not edit the work.

```

The report ends like this:

```
5.) No invented scope: FAIL. discount-codes.md:13-15, C-SPEC-SHOP-4 "Codes are not
   case-sensitive." Neither the change request nor the requester's answers mention
   letter case. This is a requirement the requester never asked for.
   (Lines 1-4 and 6-11: PASS, evidence above.)

Usable score: 85%. Item 4: C-SPEC-SHOP-4 adds a requirement the requester did not approve; it
should have been raised as a question.
```

Notice what kind of failure this is. The draft is **complete**: every point in the change request has a requirement. It is not **correct**: one requirement was never agreed.

### Step 3: Usable score under 100%, write a new brief

Do not edit the draft yourself, and do not ask the BA agent to "fix the review comments". Write a new brief that quotes the finding and states exactly what must change, and use it for a new dispatch to the BA agent:

```
Use casso-skills-spec. This is a redo.

Work to change: docs/specs/proposed/discount-codes.md on branch spec-discount-codes.
Why: the review rubric assessment gave a usable score of 85%. Finding, quoted:
  "C-SPEC-SHOP-4 'Codes are not case-sensitive.' Neither the change request nor
   the requester's answers mention letter case."

Do exactly this:
1.) Remove C-SPEC-SHOP-4. Do not reuse the number SHOP-4 for anything else.
2.) Add to the report, as an open question for the requester: "Should codes be
   case-sensitive?"
3.) Change nothing else. Requirements SHOP-1 to SHOP-3 passed review.

Commit on the same branch and report the new commit and the open question.

```

Then repeat Step 2 on the new commit. At a usable score of 100%, the dispatch's output passes its review. The next checkpoint is the specification audit: TBD (In Dev). A new brief keeps the finding on record and focuses the revision on what needs to change. The same review rubric is used again.

That was one step of one change. [Section 7](#7-scaling-the-workflow) is what it looks like across every task the WBS produces.

**Tips:** always name an output path and a branch, so the reviewer reads committed work rather than a chat message. Answer the open questions; the skills stop and ask instead of guessing, on purpose. Commit as you go so the reviewer can check the latest version.

## 9. Building on Superpowers

Superpowers helped us develop a more disciplined way of working with AI. CASSO Skills builds on that contribution and extends it for the scale and coordination needs described above.

Our experience with a developer guiding the workflow shaped the next question: how do we preserve that discipline when a team of agents is working across many tasks at once?

CASSO Skills makes several parts of that workflow explicit:

- **Clear requirement ownership.** Change requests and specifications record the requirements owner's decisions. Open questions go back to that owner, and later work is checked for requirements that were never agreed.
- **Published review criteria.** Every dispatch's output is evaluated against a review rubric and receives a usable score, with evidence for the findings. Output below the required usable score returns for revision and review.
- **Approved versions of requirements.** Requirements are checked against the existing specification and published as an official version, so everyone works from the same reference.
- **A connected enterprise lifecycle.** Intake, impact analysis, specifications, data models, work breakdowns, test and code plans, implementation, branch validation and release checks form one process.
- **Clear coordination responsibilities.** Task records, dependencies, instructions, reviews and revisions are recorded so an orchestrator can manage them across agents and sessions.

These are the choices behind CASSO Skills. They reflect what we needed as our own AI development expanded, and they build on the work that helped make that expansion possible.

## 10. CASSO Rex: the SDLC coordinator

**CASSO Rex** stands for **R**igorous **EX**ecution.

CASSO Rex is the SDLC coordinator we are building to put CASSO Skills into practice at scale. It coordinates a team of agents through the development lifecycle, keeping tasks, dependencies, reviews and rework connected as the work progresses.

Its role is to keep the workflow moving through its required checks:

- **Assign ready work.** Send tasks that are ready to start to agents with the information and instructions they need.
- **Coordinate the team.** Keep planning, implementation and review connected across tasks and dependencies.
- **Route outputs for independent review.** Have a separate agent evaluate each dispatch's committed output against the relevant review rubric and assign a usable score.
- **Follow up on findings.** Turn review findings into clear instructions and have the revised work checked again.
- **Track progress through release.** Keep progress visible as tasks move through checks, merges and releases.

CASSO Skills does not require CASSO Rex. The methodology, skill instructions and rubrics are open for other coordinators to use. Rex is the coordinator we are building, and we welcome others building on the same foundation.

CASSO Rex is in private preview, with early access available to selected teams.

To apply, email [**support@casso.ai**](mailto:support@casso.ai) with:

- Company name and website
- Number of employees
- Size of the team that would use CASSO Rex
- A detailed description of the project you would use it for
- Your name, role and LinkedIn URL

Please include all of these details so we can evaluate the fit for the preview.

## 11. Roadmap

These are the next areas we want to improve. The details and order may change as we develop and test them.

### Independent audits

Define a consistent way to score how ready a work item is. Auditors will record what they checked, what they found and what still needs attention. Reviewers will separately check whether the audit itself was complete and usable.

### System architecture

Expand the current data-model phase into a system architecture phase, with the data model as one part of the design. The architecture will describe the main parts of the system, how they connect, the technologies being used and the constraints they introduce. It will be part of the project blueprint and updated as the system evolves.

### Solution design documents

Add a solution design document (SDD) for each change. It will explain how the proposed solution meets the specifications and fits into the system architecture, including any architectural changes needed. As part of the blueprint phase, the SDD gives the team a chance to review and adjust the approach before writing detailed implementation plans or code.

### AI-native sprint coordination

Organize work into configurable cycles, such as four, six or eight hours, based on priorities, dependencies and available agent capacity. Regular planning and review checkpoints will help the team assess progress and decide what comes next. Tasks may span cycles, and the required checks and approvals still apply.

The sprint method is planned for CASSO Skills. [CASSO Rex](#10-casso-rex-the-sdlc-coordinator) will automate its coordination, while the open methodology remains available to other orchestrators.

### CI/CD integration

Connect the work coordinated in one developer's environment to the team's continuous integration and delivery (CI/CD) process. We are considering two approaches:

1.) Submit each task merge as a separate pull request (PR), with each PR going through CI/CD.
2.) Combine the changes from the task PRs into one combined PR and put that through CI/CD together.

We still need to work out the best balance between frequent feedback, review effort and the amount of work included in each PR.

The checkpoint skills and CI/CD code review will share the same review logic and criteria. The goal is to catch issues in the developer's environment using the same checks that will apply during CI/CD, so integration brings no surprises from a different set of review rules.

## 12. Install

[**Install**](INSTALL.md): how to add the skills to Claude Code, Codex, Cursor, Grok, GitHub Copilot, Antigravity or OpenCode.

## 13. Skills catalogue

[**Skills catalogue**](docs/guide/catalogue.md): skills in pipeline order, with their rubrics, checks and credits.

## 14. Open source and community

CASSO Skills exists because others shared their work. Superpowers and the other open-source projects credited below gave us ideas, methods and tools we could learn from and build on. Publishing our own work is how we give back.

We also believe the methodology can become stronger through use beyond our own team. Different projects reveal different gaps. A confusing handoff, an audit that misses a real defect or a rubric that rewards the wrong thing is an opportunity to improve the method for everyone.

We welcome questions, issues and suggestions, including experience reports from teams using their own orchestrators. Tell us what worked, where a skill fell short and what would make the workflow more useful.

Open a [GitHub Issue](../../issues) to share feedback. We are not accepting external pull requests yet; when that opens, this section will explain how to contribute changes.

New versions are announced in this repository's [Releases](../../releases). To update, copy the latest skill folders over the installed versions using the steps in [Install](INSTALL.md). Each release records what changed.

Our goal is an open engineering methodology that the community can use, challenge and improve together.

## 15. Credits and license

[**Superpowers**](https://github.com/obra/superpowers) methodology. Copyright (c) 2025 Jesse Vincent, **MIT License** (full text in `NOTICE.md`).

**CASSO Skills:** built on and extending the open-source Superpowers methodology by Jesse Vincent.

**Additional third-party sources** adapted into CASSO Skills (each block in `NOTICE.md` includes the published copyright line and license text). Which skill was extended from or inspired by which source is in the [Skills catalogue](docs/guide/catalogue.md).

| **Source**                         | **URL**                                                                                                        | **License**                                                                                                                    |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| GitHub Spec Kit                    | [https://github.com/github/spec-kit](https://github.com/github/spec-kit)                                       | MIT (GitHub, Inc.)                                                                                                             |
| OpenSpec                           | [https://github.com/Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec)                               | MIT (FISSION AI INC)                                                                                                    |
| Addy Osmani agent-skills           | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)                       | MIT (Addy Osmani)                                                                                                              |
| pstack                             | [https://github.com/backnotprop/pstack](https://github.com/backnotprop/pstack)                                 | MIT (Lauren Tan)                                                                                                               |
| code-change-impact                 | [https://github.com/mghareeb/code-change-impact](https://github.com/mghareeb/code-change-impact)               | MIT (Appenza Studio)                                                                                                           |
| mattpocock/skills                  | [https://github.com/mattpocock/skills](https://github.com/mattpocock/skills)                                   | MIT (Matt Pocock)                                                                                                              |
| BMAD-METHOD                        | [https://github.com/bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)                   | MIT (BMad Code, LLC) plus **trademark notice**, BMad™ marks remain with BMad Code, LLC; do not use as CASSO product names |
| Anthropic knowledge-work-plugins   | [https://github.com/anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins)   | Apache 2.0                                                                                                                     |
| EthicalML agent-skills-marketplace | [https://github.com/EthicalML/agent-skills-marketplace](https://github.com/EthicalML/agent-skills-marketplace) | Apache 2.0 (The Institute for Ethical AI & Machine Learning)                                                                   |

Ship `NOTICE.md` (or equivalent) with any public distribution so all MIT and Apache notices and the BMAD trademark notice remain intact.

**License:** CASSO Skills is released under the [Apache License 2.0](LICENSE). Third-party material keeps its own license, listed above and in `NOTICE.md`.
