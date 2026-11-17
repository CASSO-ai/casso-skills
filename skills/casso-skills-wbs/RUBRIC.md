# L1 review rubric: casso-skills-wbs

Use this list against the **WBS matrix** at the brief path, **build order**, and **both-way maps**. Pass each line or record fail with evidence (leaf id, C-SPEC id, dependency edge).

1. **Preconditions** — Spec review scored 100; when data needed, data model review scored 100. Once `casso-skills-audit-spec` [TBD (In Dev)] and `casso-skills-audit-data-model` [TBD (In Dev)] ship, their PASS is required instead (SKILL.md Preconditions).
2. **Scope** — Independent subsystems split via project owner before one WBS (SKILL.md Process §1).
3. **Enumerate** — Every line-start `[C-SPEC-…]` from authorized spec files listed — not sampled from memory (SKILL.md Process §2).
4. **Leaves** — Each requirement → leaf (or minimal sequenced set) with id, title, mapped C-SPEC ids, deliverable, empirical check (`[CHECK]` or derived proof), dependencies; no TBD / no "write tests later" (SKILL.md Process §3).
5. **Bidirectional trace** — Requirement→leaf and leaf→requirement with no orphans/invented scope (SKILL.md Process §4).
6. **Dependencies** — Explicit graph; acyclic; cycles broken or escalated (SKILL.md Process §5).
7. **Cross-cutting** — Errors, logging, auth, migrations, observability, CLI, security swept; gaps closed or evidenced (SKILL.md Process §6).
8. **Header** — Artefact header: slice goal; cited spec (and data model, if any) paths, SHAs and review scores (audit-spec [TBD (In Dev)] / audit-data-model [TBD (In Dev)] reports once shipped); global constraints verbatim from spec (SKILL.md Process §7).
9. **Vertical / phases / sizing** — Vertical slices preferred; phases Setup→Foundational→stories→Polish with parallel markers; XS–XL sizing, XL broken down; checkpoints every 2–3 tasks (SKILL.md Vertical feature slices, Phase template, Sizing).
10. **Overwrite guard** — No delete/overwrite/rename of incomplete existing plan without stopping and asking (SKILL.md Never overwrite an incomplete plan).
11. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. WBS matrix or judged-important artefacts are not all committed on the task branch.
2. Enumeration, maps, dependency claims, or cited SHAs appear without the matrix, spec excerpts, or audit pointers that show them.
3. Not applicable to this activity.
4. Invented leaves, orphan requirements, or scope beyond the authorized spec and project owner split appear in the trace.
5. Non-matrix junk is committed alongside the WBS.
6. Header, cross-cutting sweep, dependency detail, or brief slice element is missing with no honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: an existing incomplete plan is overwritten without stopping and asking, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: dependency cycles or ordering defects remain while the worker proceeds without escalate and honest reporting.
9. Leaves, traces, or sizing checkpoints remain incomplete so another run must finish the WBS.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
