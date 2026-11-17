# Generic L1 review rubric (all skills without a dedicated rubric)

Use for any activity skill without a dedicated `RUBRIC.md`. A few sentences the project owner asked for: the reviewer should not face a blank bar.

**Judge the delivered work against the brief and the skill it named.** Check that the evidence lives in the **delivered artefacts** (files, commits, test names, shas, counts) — not only in a narrative summary. Confirm **limits and honest gaps** are stated where the worker could not complete something. Verify the worker **committed** their judged-important changes on the task branch: uncommitted work counts as incomplete and lowers the usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Not all of the worker's judged-important changes were committed.
2. A statement in the worker's report is not backed by evidence in the delivered artefacts.
3. A check or verification is described in a way that cannot be shown to fail when the underlying result is wrong.
4. Delivered work goes beyond the brief or the skill's assigned scope.
5. Committed material includes build artefacts, scratch files, or other noise not part of the task.
6. Part of the brief is missing from the delivered work with no honest statement of the gap or limit.
7. A standing project rule is broken, such as introducing environment variables, running tests where forbidden, skipping the approved test runner, or using hand-rolled git outside project policy.
8. The work stops or repeats without an honest statement of limit or cause.
9. The brief's assigned work item is incomplete and would need another run to finish.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
