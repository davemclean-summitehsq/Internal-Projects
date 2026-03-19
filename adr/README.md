# Lone Worker ADRs

This directory contains Architectural Decision Records (ADRs) for the Lone Worker solution using the MADR structure.

## File Naming Convention

Use the following pattern for ADR files:

`ADR-XXX-short-kebab-case-title.md`

Examples:

- `ADR-001-parent-child-lone-worker-records.md`
- `ADR-002-single-end-user-check-in-form.md`
- `ADR-003-store-operational-rules-in-preferences-object.md`

## Ordering Convention

- ADR numbers should be zero-padded to three digits.
- Numbers should reflect the sequence in which decisions are documented, not necessarily implementation order.
- Preserve ADR numbers once assigned. If an ADR is superseded later, update its status rather than renumbering the set.

## Suggested Directory Structure

```text
/docs/adr/
  README.md
  adr-index.md
  ADR-001-parent-child-lone-worker-records.md
  ADR-002-single-end-user-check-in-form.md
  ADR-003-store-operational-rules-in-preferences-object.md
  ADR-004-supervisor-alert-workflow-tasks.md
  ADR-005-link-alert-handling-to-injury-management.md
  ADR-006-auto-populate-employee-and-supervisor-context.md
  ADR-007-helper-and-calculated-fields-for-operational-logic.md
  ADR-008-filtered-inventory-views-for-open-completed-and-raw-data.md
  ADR-009-structure-first-then-business-logic.md
```

## Status Values

Use concise lifecycle states such as:

- `proposed`
- `accepted`
- `deprecated`
- `superseded`

## Authoring Notes

- Keep ADRs focused on real architectural or design-significant decisions.
- Prefer one ADR per materially distinct decision.
- Avoid naming individuals in the ADR body text.
- Named individuals may appear in YAML front matter such as `deciders`, `consulted`, and `informed`.
- Use restrained inference only where needed to clarify context, outcome, or consequences.
