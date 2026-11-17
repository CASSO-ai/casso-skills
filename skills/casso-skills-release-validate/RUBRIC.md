# L1 review rubric: casso-skills-release-validate

Use this list against the **PASS/FAIL report**, **gate table tied to candidate sha**, **runner logs** (counts, run ids), and **red-green evidence** for defect gates. Pass each line or record fail with evidence (command, sha, excerpt).

1. **Pin sha** — Candidate tree identity recorded; every gate cites that sha; restart if tree moves (SKILL.md Process §1).
2. **Full regression** — Project full regression on that tree through test runner; suite and pass counts asserted; logs + run ids; poll errors treated as finished (SKILL.md Process §2).
3. **Release gates** — Every project release gate named with command/script and PASS/FAIL on that sha; known-defect gates proven red-green on candidate sha (SKILL.md Process §3).
4. **External oracle** — At least one check disagreeing with packaging (checksum, dry-run, lint, etc.) (SKILL.md Process §4).
5. **Verdict** — PASS/FAIL with sha, gate table, suite/pass counts, known gaps; FAIL blocks release-deploy until fixed or false alarm accepted (SKILL.md Process §5).
6. **Conformance scorecard** — Required rows gate release; no waiver marking required optional; evidence per row or unknown (SKILL.md Conformance scorecard).
7. **Per-artifact inventory** — Each published artifact validated independently; job success ≠ artifact pass (SKILL.md Per-artifact validation inventory).
8. **blocked ≠ passed** — Missing checks/credentials/infra = blocked, not passed (SKILL.md blocked ≠ passed).
9. **Terminology** — **work item** for pipeline activities (SKILL.md Review checklist).
10. **Worker commit** — The worker’s judged-important changes are committed on the task branch; uncommitted work counts as incomplete and lowers usable rating.

## Rating

Give one number, the usable percent, in steps of 5, inside the band the work earns:
- **Usable: 80-100.** The brief and the skill's obligations are met, the proof is in the delivered work, limits are stated, the work is committed.
- **Partly usable: 40-75.** Mostly meets the bar, but some items below apply.
- **Not usable: 0-35.** The brief or the skill was missed, or the items below apply heavily.

**Take points off for** (you judge how many; no fixed deductions):
1. PASS/FAIL report, gate table, or other judged-important validation artefacts are not all committed.
2. Candidate sha, suite count, pass count, or gate PASS appears without runner logs or command output tied to that sha.
3. A known-defect gate or external-oracle check is claimed without red-green or disagreeing-check proof on that sha.
4. Validation scope or gates go beyond this release candidate and project's required set.
5. Junk unrelated to the validation report is committed with it.
6. A required gate, conformance row, per-artifact row, or brief element is omitted with no honest blocked or unknown statement.
7. It broke a standing rule: environment variables, tests run where they aren't allowed, skipping the test runner, hand-rolled git; or, in this activity: full regression, every release gate, or the external oracle is skipped where the skill requires them, or another standing project rule is broken.
8. It stopped early or looped without reporting why; or, in this activity: polling stops or errors are dropped without the finished-run reporting the skill expects.
9. Verdict and evidence set are incomplete so another run must finish before release-deploy.

**Never take points off for a limit stated honestly** ("I could not run X because Y").

**Write one line saying why**, naming the numbered items you applied (for example: "70: items 1 and 6, two files left uncommitted and the CLI part of the brief skipped without a note").
