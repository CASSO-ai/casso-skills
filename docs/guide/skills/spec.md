# spec

**Skill folder:** `casso-skills-spec`

## Purpose

Write numbered requirements. Each one states a single requirement with exactly one acceptance check, and records why it was decided and why the alternatives were rejected. The skill writes down decisions that have been made. It does not make new ones.

## When to use

- After [cr](cr.md), and after [impact](impact.md) for anything non-trivial.
- When a requirements document needs updating because a decision changed.

## What you give it

- The change request, and the impact analysis if you have one.
- The answers to any open questions.
- A short project code for numbering units, such as `SHOP`.
- Where to save the draft. Use a "proposed" folder.

## What it produces

Requirement units, each in this form:

```markdown
[C-SPEC-<PROJECT>-<n>]
<one requirement>
[CHECK] <one observable acceptance check>
```

Optional context lines follow a unit:

- `[WHY]`: the reason for the decision.
- `[WHY-NOT]`: why an alternative was rejected, written as a concrete thing that would go wrong.
- `[COUNTEREXAMPLE]`, `[EXAMPLE]`, `[NOTE]`: supporting detail.

The draft goes under your proposed folder. Only the person who owns your requirements moves it into the approved set. If something is unclear or contradicts an earlier requirement, the skill asks; it never fills the gap itself.

## Example

> Use casso-skills-spec. Write units for `docs/changes/discount-codes-cr.md`. Answers: percentage only, one code per order. Project code SHOP. Save to `docs/specs/proposed/discount-codes.md`.

```markdown
[C-SPEC-SHOP-3]
An order accepts at most one code.
[CHECK] Entering a second valid code on an order that already has one is refused.
[WHY] Requester answer: one code per order.
[WHY-NOT] Stacking codes was not asked for and would change the pricing rules.
```

See [Dispatching one step by hand](../../../README.md#8-dispatching-one-step-by-hand) for the full set.

## Related skills

- audit-spec [TBD (In Dev)]: always check the draft before planning from it.
- [data-model](data-model.md), [wbs](wbs.md), [plan-code](plan-code.md), [plan-tests](plan-tests.md): the stages that build on approved units.
