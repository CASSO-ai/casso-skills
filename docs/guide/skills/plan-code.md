# plan-code

**Skill folder:** `casso-skills-plan-code`

## Purpose

Write the implementation plan for approved requirements: which files change, in what steps, and what each step takes in and hands on. The test it applies: would someone reading only the requirements write these steps?

## When to use

- After the spec's review scores 100 (audit-spec [TBD (In Dev)] once it ships), and after [wbs](wbs.md) if the work was broken down.
- Before [plan-tests](plan-tests.md) and any code.

## What you give it

- The approved requirements, or one leaf of the breakdown.
- Where the code lives.
- Where to save the plan.

## What it produces

A plan with:

- **A header**: the goal, the overall approach and any constraints that apply throughout.
- **A file map**: every file to create, change or delete.
- **Work items**: small steps, each naming the requirement it serves, what it uses (*Consumes*), what it provides (*Produces*) and the exact shape of the code, such as function signatures.
- **Removals**: old code the change makes obsolete.
- **Network format duties**: when two programs exchange data across a network, the exact format they must agree on and how it will be proved.

It checks that names and types are used the same way throughout, and it never overwrites a plan that is still in progress.

## Example

> Use casso-skills-plan-code for leaf L2 in `docs/plans/discount-codes-wbs.md`. Code is in `src/`. Save to `docs/plans/discount-codes-L2-code.md`.

```markdown
W1 Apply a code to an order                         serves SHOP-1, SHOP-3
  Consumes: Order, DiscountCode lookup (from L1)
  Produces: applyCode(order: Order, code: string): ApplyResult
  File: src/checkout/discount.ts (new)
```

## Related skills

- [plan-tests](plan-tests.md): the matching test plan.
- audit-plans [TBD (In Dev)]: check both plans together.
