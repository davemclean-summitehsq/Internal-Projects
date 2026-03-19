# ADR Index

This index lists the Architectural Decision Records for the Lone Worker solution.

## ADR List

1. [ADR-001: Use a parent Lone Worker record with child Check-In records](./ADR-001-parent-child-lone-worker-records.md)
2. [ADR-002: Use a single end-user check-in form for start, progress, and end-of-day activity](./ADR-002-single-end-user-check-in-form.md)
3. [ADR-003: Store operational rules in a Preferences object](./ADR-003-store-operational-rules-in-preferences-object.md)
4. [ADR-004: Drive missed check-in response through supervisor-owned alert workflow tasks](./ADR-004-supervisor-alert-workflow-tasks.md)
5. [ADR-005: Link lone worker alert handling to Injury Management when escalation reveals an incident](./ADR-005-link-alert-handling-to-injury-management.md)
6. [ADR-006: Auto-populate employee and supervisor context on lone worker records](./ADR-006-auto-populate-employee-and-supervisor-context.md)
7. [ADR-007: Use helper and calculated fields to support timing, alerting, and reporting behavior](./ADR-007-helper-and-calculated-fields-for-operational-logic.md)
8. [ADR-008: Provide separate inventory views for open, completed, and raw check-in data](./ADR-008-filtered-inventory-views-for-open-completed-and-raw-data.md)
9. [ADR-009: Sequence implementation by building structural objects and forms before advanced business logic](./ADR-009-structure-first-then-business-logic.md)

## Summary Table

| ADR No. | Title | Summary |
|---|---|---|
| ADR-001 | Use a parent Lone Worker record with child Check-In records | Organize each lone-worker period as a parent record containing multiple check-ins. |
| ADR-002 | Use a single end-user check-in form for start, progress, and end-of-day activity | Simplify the worker experience by using one form pattern across the lone-worker period. |
| ADR-003 | Store operational rules in a Preferences object | Centralize configurable timing, alerting, and threshold settings in an admin-managed object. |
| ADR-004 | Drive missed check-in response through supervisor-owned alert workflow tasks | Escalate missed check-ins through structured supervisor workflow tasks after a grace period. |
| ADR-005 | Link lone worker alert handling to Injury Management when escalation reveals an incident | Allow alert handling to create or connect an injury record for cross-process traceability. |
| ADR-006 | Auto-populate employee and supervisor context on lone worker records | Default or derive core employee and supervisor context rather than relying on manual entry. |
| ADR-007 | Use helper and calculated fields to support timing, alerting, and reporting behavior | Materialize key derived values needed for alert timing, relationships, and reporting. |
| ADR-008 | Provide separate inventory views for open, completed, and raw check-in data | Use parent-record-centered filtered inventories, with raw check-in data exposed separately. |
| ADR-009 | Sequence implementation by building structural objects and forms before advanced business logic | Build the core schema and forms first, then add automation and more complex business logic. |

## Notes

These ADRs are intentionally focused on architecture and design-significant decisions that were explicit or strongly implied by the transcript. They are suitable for direct storage in a repository and later refinement as the solution moves from proposed to accepted implementation decisions.
