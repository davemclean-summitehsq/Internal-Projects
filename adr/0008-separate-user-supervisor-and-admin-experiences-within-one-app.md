---
id: 0008
title: Separate User, Supervisor, and Admin Experiences Within One Application
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: application-structure
depends-on:
  - 0001
  - 0002
  - 0007
tags:
  - intelex
  - lone-worker
  - roles
  - navigation
---

# Separate User, Supervisor, and Admin Experiences Within One Application

## Context and Problem Statement

The application serves multiple roles with different needs: workers performing check-ins, supervisors responding to alerts and reviewing periods, and admins configuring the system. These experiences should feel purpose-built while still operating within one coherent application.

Related ADRs: [0001](./0001-use-parent-child-record-model.md), [0002](./0002-use-single-check-in-form-for-end-users.md), [0006](./0006-store-operational-rules-in-a-preferences-object.md).

## Decision Drivers

- Different personas have different tasks
- Workers need simplicity
- Supervisors need operational oversight
- Admins need configuration control
- The product should remain unified for maintenance and reporting

## Considered Options

- Build one application with role-specific forms, inventories, and navigation
- Build separate applications for workers, supervisors, and admins
- Build one generic UI for everyone
- Build only the worker experience and defer the rest

## Decision Outcome

Chosen option: **Build one application with role-specific forms, inventories, and navigation**.

This balances usability, maintainability, and coherent reporting.

## Consequences

- Good, because each persona gets an experience tailored to their job
- Good, because all records remain in one application boundary
- Good, because security and reporting can still operate on a shared data model
- Bad, because role-based UI design and permissions require more planning
- Bad, because navigation and inventory design become more complex

## Confirmation

The implementation is compliant if:

- workers access a simple check-in flow
- supervisors can access open and completed lone worker records and alerts
- admins can access preferences and setup
- the experiences are differentiated without duplicating the core data model

## Pros and Cons of the Options

### Build one application with role-specific forms, inventories, and navigation

- Good, because it keeps one coherent solution
- Good, because it supports shared reporting and governance
- Good, because it avoids fragmentation
- Bad, because permissions and UI branching are more complex

### Build separate applications for workers, supervisors, and admins

- Good, because each application could be highly specialized
- Bad, because data and maintenance become fragmented
- Bad, because cross-role reporting and traceability become harder

### Build one generic UI for everyone

- Good, because implementation may be simpler initially
- Bad, because usability suffers for all roles
- Bad, because the worker flow becomes cluttered

### Build only the worker experience and defer the rest

- Good, because it accelerates initial delivery
- Bad, because the application would not solve the operational response problem end to end
- Bad, because key safety controls would remain incomplete

## More Information

The initial views should likely include a worker check-in form, supervisor inventory for all/open/completed lone worker periods, separate inventory for raw check-ins, and a preferences or setup area for administrators.
