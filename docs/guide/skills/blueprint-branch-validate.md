# blueprint-branch-validate

**Skill folder:** `casso-skills-blueprint-branch-validate`

## Purpose

Check a large documentation-only branch before it merges. Here "blueprint" means the documents that describe a product: requirements, data model and design documents. The skill merges the branch onto your current main documents in a throwaway copy and reviews the whole set against what is already there.

## When to use

- When a branch changes many requirements or design documents at once and holds no code.
- Right after audit-spec [TBD (In Dev)], before [blueprint-branch-merge](blueprint-branch-merge.md) for that branch.
- For code branches, use [branch-validate](branch-validate.md) instead.

## What you give it

- The documentation branch and your main branch.
- Any structural check commands your project has, such as a link checker or a format checker.
- Where to save the report.

## What it produces

A **PASS** or **FAIL** report with:

- **Mechanical checks**, scripted where possible: structure, numbering, links and format.
- **Four judgment checks** on the merged documents, looking for conflicts and gaps within the branch and against what is already merged.
- Findings with location and severity, followed by the strengths of the change.
- A reviewer checklist that ties each verdict to fresh evidence.

The validator makes no edits to your live documents; it works only in the throwaway copy.

## Example

> Use casso-skills-blueprint-branch-validate on `docs-checkout-rewrite` against `main`. Structure check: `npm run docs:check`. Save to `docs/validation/docs-checkout-rewrite.md`.

```markdown
Verdict: FAIL
- docs/specs/pricing.md now says totals are final once shown;
  docs/specs/discount-codes.md (already merged) changes the total after it
  is shown. Settle which rule wins before merge.
```

## Related skills

- [blueprint-release-validate](blueprint-release-validate.md): the release-time check for documents.
- [blueprint-branch-merge](blueprint-branch-merge.md): merge once this passes.
