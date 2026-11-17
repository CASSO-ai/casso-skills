# wbs (work breakdown structure)

**Skill folder:** `casso-skills-wbs`

## Purpose

Break approved requirements into pieces of work, called leaves. Each leaf is one deliverable, small enough for one agent to do in one go. The breakdown is a faithfulness check as much as a plan: every requirement gets a leaf, and no leaf adds work nobody asked for.

## When to use

- After the spec's review scores 100, and the data model's if there is stored data (audit-spec [TBD (In Dev)] and audit-data-model [TBD (In Dev)] once they ship).
- When a change is too big for one agent session.

## What you give it

- The approved requirements, and the data dictionary if there is one.
- Where to save the breakdown.

## What it produces

- **Leaves**: each with a name, the requirements it covers, a size from XS to XL and the check that proves it is done.
- **Trace maps in both directions**: requirement to leaf, and leaf to requirement.
- **A dependency graph**: which leaves must be finished before others start, giving a build order.
- **A cross-cutting sweep**: work every leaf shares, such as logging or migrations, made explicit.

If the requirements are really several separate projects, it says so before writing one breakdown. Leaves are cut as thin end-to-end slices of a feature where possible.

## Example

> Use casso-skills-wbs on `docs/specs/discount-codes.md` with the dictionary in `docs/data/discount-codes/`. Save to `docs/plans/discount-codes-wbs.md`.

```markdown
L1 (S) Store discount codes        covers SHOP-1, SHOP-2   check: migration test
L2 (M) Apply a code at checkout    covers SHOP-1, SHOP-3   depends on L1
L3 (S) Refuse expired codes        covers SHOP-2           depends on L2
```

## Related skills

- audit-wbs [TBD (In Dev)]: check the breakdown.
- [plan-code](plan-code.md), [plan-tests](plan-tests.md): plan each leaf.
