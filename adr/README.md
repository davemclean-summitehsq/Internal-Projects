# Lone Worker Application ADR Index

This folder contains Architectural Decision Records (ADRs) for the Intelex Lone Worker application.

The ADRs use the MADR-style structure with lightweight YAML front matter for metadata.

## Status legend

- `proposed` — drafted and awaiting review/decision
- `accepted` — reviewed and approved for implementation
- `superseded` — replaced by a newer ADR
- `deprecated` — no longer recommended, but not formally superseded

## Metadata convention

See [ADR-METADATA-CONVENTION.md](./ADR-METADATA-CONVENTION.md).

## ADR index

| ID | Title | Status | Category |
|---|---|---|---|
| [0001](./0001-use-parent-child-record-model.md) | Use Parent-Child Record Model for Lone Worker Tracking | proposed | data-model |
| [0002](./0002-use-single-check-in-form-for-end-users.md) | Use a Single Check-In Form for End Users | proposed | user-experience |
| [0003](./0003-use-configurable-time-driven-check-in-monitoring.md) | Use Configurable Time-Driven Check-In Monitoring | proposed | business-rules |
| [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md) | Escalate Missed Check-Ins via Supervisor Alert Workflow | proposed | workflow |
| [0005](./0005-close-lone-worker-period-by-proximity-to-expected-end-location.md) | Close Lone Worker Period by Proximity to Expected End Location | proposed | business-rules |
| [0006](./0006-store-operational-rules-in-a-preferences-object.md) | Store Operational Rules in a Preferences Object | proposed | configuration |
| [0007](./0007-auto-populate-employee-and-supervisor-context.md) | Auto-Populate Employee and Supervisor Context | proposed | data-flow |
| [0008](./0008-separate-user-supervisor-and-admin-experiences-within-one-app.md) | Separate User, Supervisor, and Admin Experiences Within One Application | proposed | application-structure |
| [0009](./0009-link-lone-worker-events-to-injury-records.md) | Link Lone Worker Events to Injury Records | proposed | integration |
| [0010](./0010-deliver-incrementally-starting-with-objects-fields-forms-and-relations.md) | Deliver Incrementally Starting with Objects, Fields, Forms, and Relations | proposed | delivery |
| [0011](./0011-record-lone-worker-completion-intent-at-the-first-check-in.md) | Record Lone Worker Completion Intent at the First Check-In | proposed | business-rules |

## Recommended adoption sequence

1. 0001 — parent/child data model
2. 0006 — preferences/configuration approach
3. 0011 — capture end-of-period intent at first check-in
4. 0002 — worker-facing form strategy
5. 0007 — employee/supervisor auto-population
6. 0003 — time-driven monitoring
7. 0005 — closeout by proximity
8. 0004 — supervisor alert workflow
9. 0008 — role-based app experience
10. 0009 — injury linkage
11. 0010 — implementation sequencing

## Suggested future ADRs

- Security and permissions model by role
- Handling overnight or multi-day lone worker periods
- Final alert state model and escalation chain
- Mobile/offline behavior assumptions
- Exact Intelex automation pattern for parent record creation and task timing
