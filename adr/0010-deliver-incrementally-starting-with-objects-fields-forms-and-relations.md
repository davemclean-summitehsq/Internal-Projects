---
id: 0010
title: Deliver Incrementally Starting with Objects, Fields, Forms, and Relations
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: delivery
depends-on:
  - 0001
  - 0002
  - 0006
tags:
  - intelex
  - lone-worker
  - delivery
  - implementation
---

# Deliver Incrementally Starting with Objects, Fields, Forms, and Relations

## Context and Problem Statement

The application includes non-trivial business logic around parent record creation, timing, alerts, geolocation, and supervisor actions. A junior developer is building the solution and should avoid getting blocked for long periods on advanced logic before the core structure exists.

Related ADRs: [0001](./0001-use-parent-child-record-model.md), [0002](./0002-use-single-check-in-form-for-end-users.md), [0006](./0006-store-operational-rules-in-a-preferences-object.md).

## Decision Drivers

- The solution includes several moving parts
- Some logic is exploratory and may change during build
- The developer is still learning platform patterns
- Early progress should produce visible structure and reduce uncertainty
- The team wants a practical and coachable delivery approach

## Considered Options

- Build incrementally: objects, fields, forms, and relations first; advanced logic after
- Try to implement full end-to-end business logic from the start
- Build the alert workflow first and backfill the rest later
- Produce only documentation and postpone implementation decisions

## Decision Outcome

Chosen option: **Build incrementally: objects, fields, forms, and relations first; advanced logic after**.

This creates stable scaffolding, reduces risk of developer blockage, and allows review checkpoints before deeper automation is added.

## Consequences

- Good, because the developer can make progress even when blocked on one advanced concept
- Good, because early review can catch structural issues before business logic hardens
- Good, because the application can be validated in layers
- Bad, because some early builds will not be fully testable end to end
- Bad, because temporary gaps in behavior must be documented clearly

## Confirmation

The implementation is compliant if:

- the application structure is created first
- unresolved business logic items are tracked explicitly
- advanced automation is added after the data model and forms are in place
- review checkpoints occur between structural build and logic completion

## Pros and Cons of the Options

### Build incrementally: objects, fields, forms, and relations first; advanced logic after

- Good, because it is practical for a junior developer
- Good, because it exposes platform unknowns early
- Good, because it supports coaching and iterative review
- Bad, because the first pass will be incomplete by design

### Try to implement full end-to-end business logic from the start

- Good, because it aims for immediate completeness
- Bad, because it increases risk of blockage and rework
- Bad, because structural issues may be harder to untangle later

### Build the alert workflow first and backfill the rest later

- Good, because the exception path gets early attention
- Bad, because it depends on data model decisions not yet proven
- Bad, because normal operational flow would remain unclear

### Produce only documentation and postpone implementation decisions

- Good, because it gives more time to think
- Bad, because platform-specific lessons are delayed
- Bad, because uncertainty remains theoretical

## More Information

A practical execution rule is to move past any one blocker after a short investigation period, log the issue, and continue building the next structural component.
