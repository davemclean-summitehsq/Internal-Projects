---
id: 0004
title: Escalate Missed Check-Ins via Supervisor Alert Workflow
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: workflow
depends-on:
  - 0001
  - 0003
  - 0007
tags:
  - intelex
  - lone-worker
  - workflow
  - supervisor
---

# Escalate Missed Check-Ins via Supervisor Alert Workflow

## Context and Problem Statement

When a worker misses a required check-in and the grace period expires, the application must trigger an operational response. Supervisors need a structured way to review the context and decide what action to take.

Related ADRs: [0001](./0001-use-parent-child-record-model.md), [0003](./0003-use-configurable-time-driven-check-in-monitoring.md), [0007](./0007-auto-populate-employee-and-supervisor-context.md), [0009](./0009-link-lone-worker-events-to-injury-records.md).

## Decision Drivers

- Missed check-ins must trigger escalation
- Supervisors need visibility into the worker’s recent check-in history
- The response process must support both minor and serious outcomes
- The system must assign responsibility clearly
- The design should preserve an audit trail of follow-up actions

## Considered Options

- Create a supervisor alert task or workflow after missed check-ins
- Send only an email notification without a tracked task
- Notify a shared mailbox or distribution list only
- Auto-close missed check-ins without supervisor intervention

## Decision Outcome

Chosen option: **Create a supervisor alert task or workflow after missed check-ins**.

This gives a clear owner, preserves accountability, and supports a range of supervisor responses.

## Consequences

- Good, because responsibility for response is explicit
- Good, because the alert can show the day’s check-in history
- Good, because supervisors can log actions taken
- Good, because the workflow can support escalation to injury handling when needed
- Bad, because workflow design and task states add complexity
- Bad, because supervisor assignment must be reliable

## Confirmation

The implementation is compliant if:

- a missed check-in plus grace period generates an alert record or task
- the alert is assigned to the correct supervisor
- the supervisor can record the action taken and resolve the alert

## Pros and Cons of the Options

### Create a supervisor alert task or workflow after missed check-ins

- Good, because it supports accountability and auditability
- Good, because it enables structured operational response
- Good, because it supports future reporting on alerts and outcomes
- Bad, because it requires workflow design and administration

### Send only an email notification without a tracked task

- Good, because it is quick to implement
- Good, because it may be sufficient for low-maturity use cases
- Bad, because response tracking is weak
- Bad, because ownership and resolution history are unclear

### Notify a shared mailbox or distribution list only

- Good, because multiple people can see the issue
- Bad, because explicit ownership is poor
- Bad, because follow-up may be inconsistent
- Bad, because audit history is limited

### Auto-close missed check-ins without supervisor intervention

- Good, because it reduces operational workload
- Bad, because it defeats the safety purpose of the application
- Bad, because serious events could be missed

## More Information

Supervisor actions should include logging a check-in on behalf of the worker, recording actions taken, closing the lone worker period where appropriate, and linking an injury record when an incident has occurred.
