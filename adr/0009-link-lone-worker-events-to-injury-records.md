---
id: 0009
title: Link Lone Worker Events to Injury Records
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: integration
depends-on:
  - 0004
tags:
  - intelex
  - lone-worker
  - injury
  - traceability
---

# Link Lone Worker Events to Injury Records

## Context and Problem Statement

Some missed check-ins or supervisor interventions may correspond to actual incidents or injuries. The application should support traceability from lone worker activity into incident management where appropriate.

Related ADRs: [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md).

## Decision Drivers

- Lone worker exceptions may result from real injuries or emergencies
- Safety programs benefit from traceability across related processes
- Supervisors need a structured way to document escalation outcomes
- Reporting should support analysis of incidents arising from lone worker contexts

## Considered Options

- Allow supervisors to create or link an injury record from lone worker alert handling
- Keep lone worker and injury processes completely separate
- Send only an external notification to start injury reporting elsewhere
- Automatically create injury records for every alert

## Decision Outcome

Chosen option: **Allow supervisors to create or link an injury record from lone worker alert handling**.

This supports traceability without assuming that every alert is an injury.

## Consequences

- Good, because real incidents can be connected to the originating lone worker context
- Good, because reporting on injuries related to lone work becomes possible
- Good, because supervisors retain judgment
- Bad, because cross-object integration logic is required
- Bad, because governance is needed to define when to link versus create

## Confirmation

The implementation is compliant if:

- supervisors can record that an injury or incident occurred during alert handling
- the lone worker alert or parent record can link to the corresponding injury record
- the relationship is reportable

## Pros and Cons of the Options

### Allow supervisors to create or link an injury record from lone worker alert handling

- Good, because it balances structure with human judgment
- Good, because it supports traceability
- Good, because it avoids over-creating incidents
- Bad, because integration and permissions must be designed carefully

### Keep lone worker and injury processes completely separate

- Good, because boundaries remain simple
- Bad, because related-event traceability is lost
- Bad, because reporting across processes becomes manual

### Send only an external notification to start injury reporting elsewhere

- Good, because the lone worker app stays simpler
- Bad, because traceability depends on manual follow-through
- Bad, because the audit trail is weaker

### Automatically create injury records for every alert

- Good, because no possible event is missed structurally
- Bad, because most alerts are not injuries
- Bad, because false positives would overwhelm users

## More Information

This decision should align with the client’s existing injury-management process and permissions model.
