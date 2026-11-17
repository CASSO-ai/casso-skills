# data-model

**Skill folder:** `casso-skills-data-model`

## Purpose

Decide how data will be stored before the work is broken down, so storage shape is a deliberate choice and not something improvised inside one piece of code. It produces a data model and a data dictionary, and links every entity and field to the requirement that needs it.

## When to use

- After the spec's review scores 100 (audit-spec [TBD (In Dev)] once it ships), when the change adds or changes stored data.
- Skip it when nothing new is stored.

## What you give it

- The approved, audited requirements.
- What kind of store you use, or ask the skill to recommend one with reasons.
- Where to save the model and the dictionary.

## What it produces

- **Which store**: the kind of storage chosen, with the reasons.
- **The model**: entities, their fields and the relationships between them, worked from a high-level sketch down to concrete fields.
- **The data dictionary**: one entry per field, with type, meaning and allowed values. It is a set of plain-text table files.
- **Trace maps in both directions**: every requirement that needs data points to the model, and every entity and field points back to a requirement.
- **Questions**: domain questions it needs answered, such as "Can a code be reused after it expires?"

## Example

> Use casso-skills-data-model on `docs/specs/discount-codes.md`. We use a relational database. Save to `docs/data/discount-codes/`.

```markdown
Entity: DiscountCode
  code        text, unique        <- C-SPEC-SHOP-1
  percent     integer, 1..100     <- C-SPEC-SHOP-1
  expires_at  timestamp           <- C-SPEC-SHOP-2
Entity: Order
  discount_code  reference to DiscountCode, at most one  <- C-SPEC-SHOP-3
```

## Related skills

- audit-data-model [TBD (In Dev)]: check the model before breaking down the work.
- [wbs](wbs.md): its pieces cite the dictionary.
