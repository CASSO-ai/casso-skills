# L1 review rubric: casso-skills-research

Use this list against the **research write-up** under the project/brief path and cited **primary evidence**. Pass each line or record fail with evidence (path, command output, quoted log).

1. **Questions** — Investigation questions stated up front; falsifiable where possible (SKILL.md Process §1).
2. **Primary evidence** — Named sources read; commands/outputs/paths recorded for relied-on facts (SKILL.md Process §2).
3. **Defect trace** — Differences vs working reference listed; bad values traced to origin — not stopping at first symptom (SKILL.md Process §2).
4. **Hypotheses** — One hypothesis at a time; Recommendations free of stacked untested theories (SKILL.md Process §3).
5. **Layers** — Observation / Inference / Recommendation labeled distinctly (SKILL.md Process §4).
6. **Positive control** — Absence claims use matcher that finds a known-present control first (SKILL.md Process §5).
7. **Findings file** — Research tree (or brief path): questions, method, evidence, limits, open project owner questions (SKILL.md Process §6).
8. **Scope stop** — No product code unless brief authorizes throwaway harness under the spike area (SKILL.md Process §7).
9. **Idea pipeline** — When ask is an idea: intake→research→define→shape→decide with verdict go / needs-clarification / kill (SKILL.md Process §8).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Findings file or other judged-important research artefacts are not all committed.
2. Commands, outputs, paths, or source reads are claimed without showing them in the deliverables.
3. "Not found" or absence is claimed without the positive-control match the skill requires first.
4. Product code ships here, the idea pipeline is bypassed for an idea ask, or Recommendations stack untested theories.
5. Build artefacts, scratch captures, or other junk are committed as research.
6. Questions, method, evidence, limits, or project owner open items are missing from the findings file with no honest gap statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: observation, inference, and recommendation are mixed so inferences read as measurements, or unauthorized product edits appear.
8. It stopped early or looped without reporting why; or, in this activity: tracing stops at the first symptom while differences vs a working reference and root tracing are unfinished, or hypotheses are stacked without the one-at-a-time rule.
9. Verdict, handoff, or findings remain incomplete so another run must finish the research work item.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
