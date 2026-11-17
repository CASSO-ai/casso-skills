# L1 review rubric: casso-skills-branch-merge

Use this list against **merge-record fields**, **reported shas and counts**, and evidence the **branch-validate PASS** matches the recorded tree. Pass each line or record fail with evidence (sha, tool output, commit message).

1. **Preconditions** — Work reflects prior `casso-skills-branch-validate` PASS (or hotfix exception as ruled); project owner approval present (SKILL.md Preconditions).
2. **Merge check readout** — Deterministic readout covers rebase state, branch-validate green, scope, current base as project defines (SKILL.md Process §1).
3. **Identity match** — Tree recorded as merged matches the identity branch-validate passed on; if main moved, re-validation evidenced or merge not recorded under old PASS (SKILL.md Process §2).
4. **Three-part bar** — Workspace green with asserted counts, mutation by test name when required, external oracle — re-verified after merge-base check (SKILL.md Process §3).
5. **Merge record** — Timestamp, merging work identity, merge commit sha tied to validated tree (or byte-identical successor) populated atomically via CLI or stated manual procedure (SKILL.md Process §4).
6. **Merger behavior** — Release guidelines for ordering/hold consulted where merge timing applies (SKILL.md Process §5).
7. **Commit message** — Merge commit (or record) carries counts, mutation names, oracle output, validated-tree identity, known gaps (SKILL.md Process §6).
8. **Five-axis review** — Correctness, readability, architecture, security, performance addressed; diff sizing guidance considered (~100 lines focused) (SKILL.md Five-axis review).
9. **Terminology** — **work item** used for pipeline activities (SKILL.md Review checklist).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. Merge record fields or judged-important merge artefacts are not all committed as required.
2. PASS linkage, counts, or mutation names appear without branch-validate report excerpt or tool output for the recorded tree.
3. Mutation-by-test-name or oracle re-check is missing after merge-base drift where Process §3 requires re-verify.
4. Merge records a tree outside branch-validate scope or skips project owner approval Preconditions require.
5. Junk unrelated to merge evidence is committed with the record.
6. Commit message omits counts, mutation names, oracle output, validated identity, or known gaps with no honest limit statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: merge timing ignores the project's release guidelines, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: merge readout stops without recording cause when rebase or scope checks fail.
9. Merge event fields stay incomplete so another run must finish the record.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
