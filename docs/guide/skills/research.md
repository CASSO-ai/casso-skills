# research

**Skill folder:** `casso-skills-research`

## Purpose

Investigate a question and write down what you found, with evidence. A research run reads and measures; it does not change your product code. It is allowed to disagree with what you hoped to hear.

## When to use

- You need facts before deciding: "Why is checkout slow?", "Which payment library fits?", "Is this idea worth building?"
- Earlier reports disagree and you want a fresh, independent look.
- Use it before [cr](cr.md) when you are not yet sure what to ask for.

## What you give it

- The questions to answer, as specific as you can.
- Where to look: code folders, logs, documents, links.
- Where to save the findings.
- Optionally, permission to write a small throwaway test harness. Without it, the run stays read-only.

## What it produces

A findings report with:

- the questions;
- the method used;
- the evidence, with citations (file and line, command output, links);
- what is known versus what is still open, and the limits of the study.

The report keeps three things apart: what was **observed**, what was **inferred** from it, and what is **recommended**. When it says something is absent, it also shows that the same search finds something that is present, so a wrong search is not mistaken for "not there". It tests one hypothesis at a time. When the question is an idea to assess, it says whether the idea is worth pursuing and why.

## Example

> Use casso-skills-research. Question: do customers abandon checkout more often when they have no discount code? Look at `analytics/exports/checkout-2026-10.csv`. Save findings to `docs/research/checkout-abandonment.md`.

Typical finding:

```markdown
Observation: 31% of checkouts that reached the payment step were abandoned
(analytics/exports/checkout-2026-10.csv, rows 2-4410).
Inference: the export has no discount field, so it cannot show whether the
missing code caused any of this.
Open question: add a "had code" field to the export before deciding.
```

## Related skills

- [cr](cr.md): turn what you learned into a change request.
- [impact](impact.md): research what a proposed change would touch.
