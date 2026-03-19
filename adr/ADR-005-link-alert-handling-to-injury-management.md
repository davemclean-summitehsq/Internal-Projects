---
adr: "ADR-005"
title: "Link lone worker alert handling to Injury Management when escalation reveals an incident"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "integration"
  - "injury-management"
  - "traceability"
  - "workflow"
---

# Link lone worker alert handling to Injury Management when escalation reveals an incident

## Context and Problem Statement

A missed check-in may sometimes turn out to be an administrative lapse, but it may also indicate an actual injury or emergency. The lone-worker process should therefore support a path from alert investigation into formal incident or injury handling without breaking traceability.

The design discussion explicitly introduced the ability for supervisors to log actions including creation of an injury-related record.

## Decision Drivers

- Need traceability from lone-worker alerts to actual incidents
- Need to support supervisor action paths beyond simple closure
- Need to avoid disconnected follow-up processes
- Need to preserve business context when a safety event is discovered

## Considered Options

- Keep lone-worker alerts operationally separate from injury management
- Allow alert handling to create or connect to an Injury record
- Require a completely manual handoff into injury management outside the lone-worker solution

## Decision Outcome

Chosen option: **Allow lone-worker alert handling to create or connect to an Injury record**.

Supervisor response to an alert may include logging an injury-related action so that injuries discovered through the lone-worker monitoring process can be traced back to their originating lone-worker session or alert context.

## Consequences

This strengthens traceability across modules and improves the value of the lone-worker process as part of a broader safety workflow. It also supports later reporting on injuries arising from lone-worker situations.

The integration introduces cross-object dependencies and will require careful design of ownership, linkage, and data propagation.

## More Information

The discussion explicitly described a scenario in which a supervisor determines that a real injury occurred and connects that outcome to an injury record so the organization can track injuries originating from lone-worker records.
