# L1 review rubric: casso-skills-data-model

Use this list against the **dictionary bundle**, **model summary**, **both-way trace maps**, and **commits** at the brief paths. Pass each line or record fail with evidence (path, CSV row, C-SPEC id).

1. **Preconditions** — Authorized spec; spec review score of 100 cited (`casso-skills-audit-spec` [TBD (In Dev)] PASS once shipped); spec units have stable ids with one acceptance check each (SKILL.md Preconditions).
2. **Enumerate clauses** — Data-bearing clauses listed from source files (not from memory); unmodelable clauses stopped with project owner question (SKILL.md Process §1).
3. **Store family** — Primary store kind chosen with rationale; non-obvious choice records 2–3 candidates + recommendation; non-relational has access-pattern matrix before physical keys (SKILL.md Process §2).
4. **Conceptual then logical** — Conceptual diagram before physical; review recorded; physical-first fails sequence check; relationships have cardinality both ends and mandatory/optional marked (SKILL.md Process §3, Clean-room §4 §7).
5. **Domain questions** — In-tenant roles asked; tenant isolation for multi-tenant (SKILL.md Process §4).
6. **Dictionary bundle** — Files under brief path (`entities.csv`, `attributes.csv`, `relationships.csv`, plus companions per format); standard columns + `x_` extension rule; every attribute has `spec_id`; every data-bearing clause maps; no orphan/invented rows (SKILL.md Process §5–6).
7. **Both-way maps** — Spec → model and model → spec maps with no orphans (SKILL.md Process §6).
8. **Output** — Model summary + dictionary committed and versioned per project at brief paths (SKILL.md Process §7).
9. **Clean-room** — Atomic field constraints; noun harvest; technology-neutral definitions; overloaded entities; m-n associative entities; parent-dependent records — as the numbered items require, evidenced in deliverables (SKILL.md Clean-room §1–3 §5–6 §8).
10. **MVP scope** — Blueprint expansion not attempted (SKILL.md Post-MVP note, Review checklist).
11. **Terminology** — **work item** used where pipeline activities appear (SKILL.md Review checklist).
12. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Dictionary files, model summary, maps, or other judged-important artefacts are not all committed at the brief paths.
2. Clause lists, trace rows, or `spec_id` coverage appear without CSV or source excerpts that prove them.
3. Not applicable to this activity.
4. Blueprint expansion beyond MVP is attempted, attributes or entities lack spec backing, or store family is locked without the candidate comparison the skill requires when non-obvious.
5. Build artefacts, scratch exports, or other junk are committed with the dictionary.
6. Enumeration, relationships, tenant isolation, or Clean-room rows are missing with no project owner question or honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: physical-first diagram order is used while the sequence check fails, the live spec is edited here, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: unmodelable clauses are guessed into attributes instead of stopping with an project owner question.
9. Maps, dictionary bundle, or summary remain incomplete so another run must finish the data model work item.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
