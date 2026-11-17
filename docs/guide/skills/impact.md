# impact

**Skill folder:** `casso-skills-impact`

## Purpose

Find out what a change request touches and what could break, before anyone writes requirements. It compares the request against your existing requirements, past decisions and the code itself, not only the request text, and it raises any contradictions for the person who asked for the change to settle.

## When to use

- After [cr](cr.md), before [spec](spec.md).
- When a change looks small but sits near something important, such as payments, sign-in or stored data.
- In the middle of a larger piece of work, when a new change might affect work already under way.

## What you give it

- The change request.
- Where your requirements, decision records and code live.
- Where to save the impact analysis.

## What it produces

An impact analysis with:

- **Classification**: what kind of change this is.
- **Touched surfaces**: the files, screens, services and data the change reaches.
- **Blast radius**: a level from 1 (very contained) to 5 (very wide), with the reasoning.
- **Contradictions**: places where the request conflicts with an existing requirement or decision, as questions for the requester.
- **Certainty**: for each claim, how well it is backed, from "someone said so" up to "reproduced in the running app".
- **Users / Systems / Processes / Cost**: a short grid of who and what is affected.

When one fact decides whether the change is safe, the skill proves it by running code, not by reading.

## Example

> Use casso-skills-impact on `docs/changes/discount-codes-cr.md`. Requirements are in `docs/specs/`, code in `src/`. Save to `docs/changes/discount-codes-impact.md`.

Typical output:

```markdown
Blast radius: 3. Touches order totals (src/checkout/total.ts), the order
record, and the receipt email.
Contradiction: docs/specs/pricing.md says "the order total is final once
shown". A code entered after the total is shown changes it. Which rule wins?
```

## Related skills

- [cr](cr.md): the input to this skill.
- [spec](spec.md): the next step, once the contradictions are answered.
