---
id: 0001
title: Use Parent-Child Record Model for Lone Worker Tracking
status: accepted
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: data-model
depends-on: []
tags:
  - intelex
  - lone-worker
  - parent-child
  - data-model
---

# Use Parent-Child Record Model for Lone Worker Tracking

## Context and Problem Statement

The application must support repeated check-ins for a worker during a single lone worker period, while also allowing supervisors and administrators to review the overall state of that period as one coherent unit. We need a data model that supports both individual check-in events and an aggregated day- or period-level record.

Related ADRs: [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md), [0008](./0008-separate-user-supervisor-and-admin-experiences-within-one-app.md), [0011](./0011-record-lone-worker-completion-intent-at-the-first-check-in.md).

## Decision Drivers

- A worker may check in multiple times during one lone worker period
- Supervisors need a consolidated view of the worker’s current and historical status
- Alerts and downstream actions need to be associated with the broader lone worker period, not only one check-in
- The design should support open and completed lone worker periods
- The model should be extensible for future reporting and productization

## Considered Options

- Store every check-in as an independent standalone record only
- Use a parent Lone Worker record with child Check-In records
- Use one record with repeated fields for multiple check-ins
- Use only an alert-centric model and infer the rest from alerts

## Decision Outcome

Chosen option: **Use a parent Lone Worker record with child Check-In records**.

This best represents the real-world concept of one lone worker period containing many check-ins and allows alerts, reporting, and supervisor actions to roll up to a single operational record.

## Consequences

- Good, because supervisors can review a full lone worker period in one place
- Good, because the design supports inventory views for open and completed lone worker periods
- Good, because check-ins remain atomic events for auditability
- Good, because related alerts and future incident links can be attached to the parent record
- Bad, because the application requires business logic to auto-create and auto-associate the correct parent record
- Bad, because parent-child relationships increase implementation complexity

## Confirmation

The implementation is compliant if:

- each submitted check-in is linked to exactly one open parent Lone Worker record for that worker, or triggers creation of one if none exists
- each Lone Worker record can display a related grid of its check-ins
- open and completed inventory views operate from the parent object

## Pros and Cons of the Options

### Store every check-in as an independent standalone record only

- Good, because the model is simple
- Good, because it minimizes initial relationship configuration
- Bad, because supervisors do not get a natural container for a worker’s day or period
- Bad, because reporting on lone worker periods becomes harder
- Bad, because alert handling becomes fragmented

### Use a parent Lone Worker record with child Check-In records

- Good, because it maps cleanly to the business process
- Good, because it supports auditability and operational review
- Good, because it creates a clear anchor for alerts and related incidents
- Bad, because it requires relationship and automation logic

### Use one record with repeated fields for multiple check-ins

- Good, because it keeps all data on one object
- Bad, because it does not scale to unpredictable numbers of check-ins
- Bad, because it is awkward for audit history and reporting
- Bad, because it complicates UI behavior significantly

### Use only an alert-centric model and infer the rest from alerts

- Good, because it focuses on the exception workflow
- Bad, because normal compliant activity becomes a second-class concept
- Bad, because the absence of alerts does not fully describe the lone worker period
- Bad, because it produces weak operational history

## More Information

The parent object should represent the active or completed lone worker period, while the child object should represent individual check-in events. The parent object should also be the primary reporting and inventory surface for supervisors and admins.
