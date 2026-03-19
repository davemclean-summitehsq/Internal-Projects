---
id: 0003
title: Use Configurable Time-Driven Check-In Monitoring
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: business-rules
depends-on:
  - 0006
tags:
  - intelex
  - lone-worker
  - timing
  - alerting
---

# Use Configurable Time-Driven Check-In Monitoring

## Context and Problem Statement

The application must determine when a worker is expected to check in again and when a missed check-in should become actionable. Different clients may require different intervals and escalation timings.

Related ADRs: [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md), [0006](./0006-store-operational-rules-in-a-preferences-object.md).

## Decision Drivers

- Check-in frequency must be configurable
- The application may be reused across clients with different requirements
- The system must support objective, time-based compliance logic
- Admins need control without code changes
- Alert timing should be derived consistently from configured rules

## Considered Options

- Use configurable time-driven monitoring based on settings
- Hard-code one check-in interval and one grace period
- Allow each worker or supervisor to set ad hoc intervals manually
- Use location movement alone without scheduled timing

## Decision Outcome

Chosen option: **Use configurable time-driven monitoring based on settings**.

This provides predictable and reusable compliance logic while allowing each implementation to tune timing behavior without redesign.

## Consequences

- Good, because the solution is reusable across clients
- Good, because alert timing becomes explainable and auditable
- Good, because settings can support hours, minutes, or days
- Bad, because preference data and helper calculations are required
- Bad, because time-driven logic must be carefully tested for edge cases

## Confirmation

The implementation is compliant if:

- administrators can configure check-in frequency
- administrators can configure an alert grace period
- the system calculates next expected check-in and escalation timing from those values

## Pros and Cons of the Options

### Use configurable time-driven monitoring based on settings

- Good, because it is flexible
- Good, because it supports productization
- Good, because it avoids code changes for common policy changes
- Bad, because implementation is more complex than hard-coding

### Hard-code one check-in interval and one grace period

- Good, because it is simple to build
- Bad, because it is not reusable
- Bad, because admin control is poor
- Bad, because future client variation becomes expensive

### Allow each worker or supervisor to set ad hoc intervals manually

- Good, because it is flexible at the individual level
- Bad, because governance becomes inconsistent
- Bad, because auditability and reporting become weaker
- Bad, because errors and missed expectations become more likely

### Use location movement alone without scheduled timing

- Good, because it reduces reliance on explicit time settings
- Bad, because it does not solve the core requirement of scheduled check-ins
- Bad, because stationary lone workers could still be at risk without movement

## More Information

A preferences object should define check-in frequency and grace period. Helper fields on the parent record may calculate the next expected deadline and alert timing.
