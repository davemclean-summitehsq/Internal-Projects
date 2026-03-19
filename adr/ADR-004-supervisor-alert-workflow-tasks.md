---
adr: "ADR-004"
title: "Drive missed check-in response through supervisor-owned alert workflow tasks"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "workflow"
  - "alerts"
  - "escalation"
  - "roles"
---

# Drive missed check-in response through supervisor-owned alert workflow tasks

## Context and Problem Statement

The solution must respond when a required check-in is missed. An email notification alone may not provide enough structure, accountability, or action support. The process needs a clear owner and a manageable operational response model for supervisors.

The discussion established that missed check-ins should result in a supervisor-facing alert task after a configurable grace period.

## Decision Drivers

- Need clear ownership of missed check-in response
- Need a structured escalation path after a missed check-in
- Need to show the supervisor the day’s check-in history
- Need to support actionable supervisor responses, not just notification
- Need to allow configurable grace period before escalation

## Considered Options

- Send only a passive email notification to the supervisor
- Create a workflow task for the supervisor after the grace period
- Escalate directly to a broader incident workflow without an intermediate supervisor task

## Decision Outcome

Chosen option: **Create supervisor-owned alert workflow tasks after a configurable grace period**.

When a required check-in is not completed in time, the system waits for the configured grace period and then generates a lone-worker alert task for the supervisor. That task is intended to show the relevant history for the day and provide the supervisor with available response actions.

## Consequences

This supports accountability and creates a formal response path that is easier to track and audit than email alone. It also gives the supervisor a focused work item rather than expecting manual interpretation of notifications.

The approach requires workflow configuration and clear task design. It also means alert timing and ownership logic become central architectural elements of the solution.

## More Information

The conversation distinguished between the timing rule for expected check-ins, the grace period before escalation, and the need for a supervisor task that shows the day’s history and allows response actions.
