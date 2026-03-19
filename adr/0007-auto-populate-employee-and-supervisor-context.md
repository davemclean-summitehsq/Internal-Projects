---
id: 0007
title: Auto-Populate Employee and Supervisor Context
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: data-flow
depends-on:
  - 0001
tags:
  - intelex
  - lone-worker
  - supervisor
  - employee
---

# Auto-Populate Employee and Supervisor Context

## Context and Problem Statement

The application should minimize manual data entry and reduce the chance of check-ins being submitted against the wrong person or without a responsible supervisor context.

Related ADRs: [0002](./0002-use-single-check-in-form-for-end-users.md), [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md), [0008](./0008-separate-user-supervisor-and-admin-experiences-within-one-app.md).

## Decision Drivers

- Worker-facing data entry should be as simple as possible
- Accountability for alerts depends on supervisor assignment
- The employee submitting the check-in is typically the current user
- Derived context should be consistent across records and views
- The design should reduce avoidable user error

## Considered Options

- Default employee to the current user and auto-populate supervisor from related employee or group data
- Require users to select both employee and supervisor manually
- Default employee only, but require supervisor to be entered later
- Derive neither and rely on downstream correction

## Decision Outcome

Chosen option: **Default employee to the current user and auto-populate supervisor from related employee or group data**.

This reduces friction for users and supports reliable alert routing.

## Consequences

- Good, because worker check-ins become faster
- Good, because supervisor routing becomes consistent
- Good, because inventory views can display supervisor without duplicate data entry
- Bad, because employee-master and supervisory relationship data must be trustworthy
- Bad, because action handlers or related-record logic are required

## Confirmation

The implementation is compliant if:

- the employee field defaults to the current user and is read-only for the worker flow
- the supervisor is populated automatically from the selected or inferred employee context
- alerts are assigned to that derived supervisor

## Pros and Cons of the Options

### Default employee to the current user and auto-populate supervisor from related employee or group data

- Good, because it reduces friction
- Good, because it supports correct routing
- Good, because it reduces manual errors
- Bad, because it depends on clean reference data

### Require users to select both employee and supervisor manually

- Good, because it is explicit
- Bad, because it creates unnecessary effort
- Bad, because it increases the risk of misassignment

### Default employee only, but require supervisor to be entered later

- Good, because the worker flow is simplified
- Bad, because alert routing can fail or be delayed
- Bad, because data completeness becomes inconsistent

### Derive neither and rely on downstream correction

- Good, because implementation is simple
- Bad, because operational reliability is poor
- Bad, because it shifts work to supervisors and admins

## More Information

This decision assumes the employee record or related location or group record can identify the appropriate supervisor for monitoring purposes.
