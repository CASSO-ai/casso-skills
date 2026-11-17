---
name: casso-skills-data-model
description: Use when turning an approved audited spec into a data model and data dictionary before WBS — entities, attributes, relationships, and bidirectional clause traceability
---

# Data Model (casso-skills-data-model)

## Overview

Turn the approved, audited functional spec into a **data model** plus a **data dictionary** the rest of the pipeline can audit and cite. Every entity and attribute traces to a spec clause; every clause that needs data traces to the model.

**Core principle:** Storage shape is decided deliberately before breakdown — not discovered inside one implementation work item.

**Post-MVP note:** this work item widens later into a broader **blueprint** activity. Do **not** build the blueprint expansion now; produce data model + dictionary only.

**Method sources:** Industry data-modeling practice (conceptual → logical → physical; ER; access-pattern-first for non-relational stores); the project's data-dictionary format research recommendation (multi-file CSV bundle — use the project's published data-dictionary format guidance; pending review of that format).

## Preconditions

- Spec authorized, and its review scored 100 for the slice. (Once `casso-skills-audit-spec` [TBD (In Dev)] ships, its PASS is required instead.)
- Spec units carry stable ids with one acceptance check each.

## Process

### 1. Enumerate data-bearing requirements

From the authorized spec, list every clause that implies stored state, identifiers, relationships, tenancy, retention, or query/access needs. Do not sample from memory — enumerate from the source files.

If a clause cannot be modeled without guessing, stop and ask whoever authorized the work — do not invent attributes.

### 2. Choose store family (with rationale)

Select the primary store kind (relational, document, key-value, graph, search, object, cache, or a stated combination) from requirement signals. Record the rationale. When store-family choice is non-obvious, record 2–3 candidate families with trade-offs and a recommendation before locking the primary store_kind. For non-relational primary stores, draft an access-pattern matrix before physical keys.

### 3. Conceptual then logical model

Produce and review a conceptual diagram of entities, attributes, and relationships before introducing physical schema choices; record the review result and fail the sequence check if physical design came first. Then add attributes, keys, and integrity rules in a platform-neutral logical form. For every relationship, record minimum and maximum cardinality at both ends and state whether each end is mandatory or optional; reject any unmarked end. Default to normalized relational shape unless a named reason justifies duplication or another family.

### 4. Ask domain questions the research requires

Always ask whether in-tenant roles (for example admin vs viewer) are needed. Add minimal role/assignment structures only when the spec mentions sharing, admins, or read-only users; otherwise record that a single role is sufficient. For multi-tenant products, plan row-level tenant isolation in the store.

### 5. Emit the data dictionary (recommended format)

Write the dictionary bundle under the path the brief names (default shape: project `data/dictionary/`):

| File | One row per |
|------|-------------|
| `entities.csv` | Entity / collection |
| `attributes.csv` | Attribute / field |
| `relationships.csv` | Relationship with cardinality |
| `constraints.csv` | Named constraint |
| `enumerations.csv` | Allowed code values |
| `access-patterns.csv` | Read/write path (required when store_kind is non-relational) |
| `security.csv` | Tenancy / classification scope |

**Standard columns** (fixed; do not repurpose): entity, attribute, definition, data_type, nullable, **spec_id**, and the relationship cardinality fields (`0..1`, `1..1`, `0..*`, `1..*`). `spec_id` lists the numbered spec requirement id(s) the row satisfies; it is a standard column, not an extension. Other project-specific columns use the `x_` prefix only.

**Traceability (required):** every attribute carries `spec_id` listing the spec unit id(s) it satisfies; every data-bearing clause appears on at least one entity or attribute.

### 6. Both-way trace maps

Produce:

- Spec clause → model element(s)
- Model element → spec clause(s)

No orphan data-bearing clause; no invented entity/attribute without a clause.

### 7. Output artefact

Commit the model summary (short conceptual prose + store rationale) and the dictionary bundle at the brief paths. Version them with the project so later WBS leaves can cite them.

## Additional requirements

1. **Constrain every atomic field.** For each primitive field, record type, applicable format or length, allowed values or range, and default or an explicit statement that no default exists. The field is incomplete if any applicable cell is blank.
2. **Harvest noun candidates.** Scan every requirement and use case, list each noun that denotes stored or exchanged data, and disposition it as an entity, attribute, synonym of an existing item, or out of scope with a reason. Completion requires every candidate to have one disposition.
3. **Keep the dictionary technology-neutral.** Review every dictionary definition for physical terms such as table, index, or storage engine. Replace implementation choices with business meaning and logical shape, or move the choice to the physical rationale; PASS when no unexplained physical term remains.
4. **Mark both ends of every relationship.** Incorporated by strengthening Process 3 with minimum/maximum cardinality and participation at both ends plus an unmarked-end rejection rule.
5. **Split overloaded entities.** For each entity, group attributes by identity and lifecycle. When groups can be created, changed, or retired independently, split them or record a requirement-based reason to keep them together; verify the decision in the model summary.
6. **Resolve attributed many-to-many links.** Inspect every many-to-many relationship. If the relationship has its own attributes, replace it with an associative entity and two marked relationships; verify that each relationship attribute moved to that entity.
7. **Start with a conceptual diagram.** Incorporated by strengthening Process 3 with a recorded conceptual-diagram review and a physical-design sequence failure condition.
8. **Model parent-dependent records explicitly.** Identify records that cannot exist without a parent and mark them as parent-dependent. Define inherited or parent-scoped identity plus deletion and reassignment behavior; the record is incomplete until all three rules are stated.

## Common mistakes

- Inventing tables the spec never required.
- Inventing attributes when a clause cannot be modeled without guessing.
- Omitting `spec_id` on attributes.
- Skipping relationships/cardinality.
- Jumping to physical DDL without a logical model and access patterns.
- Locking a non-obvious store_kind without recording 2–3 candidate families and a recommendation.

## Review checklist

- [ ] Spec review score of 100 cited (audit-spec [TBD (In Dev)] PASS once shipped)
- [ ] Store family chosen with rationale (2–3 candidates + recommendation when non-obvious)
- [ ] Dictionary bundle present with required files
- [ ] Standard columns + `x_` extension rule obeyed
- [ ] Every attribute has `spec_id`, and every id in it exists in the authorized spec
- [ ] Every data-bearing clause maps to the model
- [ ] Unmodelable clauses escalated to whoever authorized the work (no invented attributes)
- [ ] Relationships carry allowed cardinality codes
- [ ] Tenant isolation addressed when multi-tenant
- [ ] Blueprint expansion not attempted (MVP scope)
- [ ] Terminology: work item
