# L1 review rubric: casso-skills-impact

Use this list against the **impact-analysis document** outside the live spec tree and supporting **evidence** (commits, host-facts citations, run outputs). Pass each line or record fail with evidence (path, command output).

1. **Classify & enumerate** — Domains, modules, migrations, CLI, cross-cutting classes listed; multi-subsystem call for separate slices when shown (SKILL.md Process §1).
2. **Blast radius** — `blast_radius_level` 1–5 on the task; states what breaks if wrong (SKILL.md Process §2).
3. **Contradictions** — Load-bearing conflicts raised to project owner, not auto-resolved; minor routing explicit; code conflicts cite recent commits/diffs (SKILL.md Process §3).
4. **Output path** — Document at brief path (SKILL.md Process §4).
5. **Safety proof** — One or two load-bearing safety facts proven by running code or marked unproven; certainty ladder stated per fact (SKILL.md Process §5).
6. **Coupling & verdict** — Surfaces classified; verdict SAFE / SAFE WITH CAVEATS / IMPACT FOUND with caveats or named consumer (SKILL.md Process §6).
7. **Impact grid** — Users/Systems/Processes/Cost filled when non-code surfaces apply (SKILL.md Process §7).
8. **Mid-sprint mapping** — PRD/WBS/architecture/UX impact mapped when change lands mid-sprint; feeds sprint change proposal when required (SKILL.md Process §8).
9. **Host facts** — When naming hosts/filesystems/toolchains, measured host-facts reference consulted (SKILL.md Preconditions).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Impact-analysis file or other judged-important artefacts are not all committed.
2. Surface list, safety fact, or blast claim appears without file paths, command output, commits, or host-facts citations the deliverable must show.
3. Not applicable to this activity.
4. Deep analysis ships before a multi-subsystem split is recommended when enumeration requires it, or impact is narrowed to the CR text alone.
5. Scratch captures or junk are committed with the analysis.
6. Impact grid, verdict, certainty ladder, or brief path element is missing with no honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: host or toolchain facts are asserted without consulting measured host facts where Preconditions require it.
8. It stopped early or looped without reporting why; or, in this activity: contradictions are cleared inside the analysis while Process §3 expects project owner handoff, or enumeration is skipped while momentum continues.
9. Cross-artifact mapping, safety proof, or task fields remain incomplete so another run must finish impact work.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
