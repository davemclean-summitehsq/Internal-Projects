---
adr: "ADR-006"
title: "Auto-populate employee and supervisor context on lone worker records"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "defaults"
  - "context"
  - "permissions"
  - "data-quality"
---

# Auto-populate employee and supervisor context on lone worker records

## Context and Problem Statement

The solution depends on reliable employee and supervisor context for ownership, alert routing, and reporting. Manual entry of this information during repeated field check-ins would increase friction and create data-quality risk.

The discussion established that employee and supervisor values should be defaulted or set automatically where possible.

## Decision Drivers

- Need accurate routing of alerts to the correct supervisor
- Need to reduce repeated manual data entry
- Need to improve consistency and reporting quality
- Need to preserve a streamlined field-user experience

## Considered Options

- Require users to manually select employee and supervisor values
- Default employee and derive supervisor automatically through related context
- Omit supervisor storage and resolve it dynamically only at alert time

## Decision Outcome

Chosen option: **Default employee and auto-populate supervisor context on lone worker records**.

The employee should default to the current user and be displayed in a controlled or read-only manner after creation. Supervisor context should be set automatically through related selection or action-handler logic and stored for use in inventory views, workflow routing, and reporting.

## Consequences

This reduces user effort and helps ensure alerts and summaries are routed and displayed correctly. It also supports cleaner parent-record summaries and inventory designs.

The tradeoff is that the solution becomes more dependent on accurate upstream employee-to-supervisor relationships and action logic.

## More Information

The discussion included defaulting the employee to the current user, making it read-only or display-only in parts of the experience, and auto-setting supervisor information for use in the parent record and inventory views.
