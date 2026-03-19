---
adr: "ADR-001"
title: "Use a parent Lone Worker record with child Check-In records"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "data-model"
  - "parent-child"
  - "traceability"
---

# Use a parent Lone Worker record with child Check-In records

## Context and Problem Statement

The solution needs to support multiple check-ins during a single lone-worker period while preserving a coherent record of that work period for monitoring, alerting, and reporting. A flat structure of independent check-ins would make it harder to understand the overall session, determine whether the work period is still open, and review the sequence of events associated with a day’s activity.

The discussion established a structure in which a lone-worker period is represented by a parent record, and individual check-ins are stored as related child records under that parent until the period is closed.

## Decision Drivers

- Need to group multiple check-ins into a single operational context
- Need to distinguish an active lone-worker period from completed ones
- Need to support supervisor review of a day’s history of check-ins
- Need to enable summary reporting at the session level
- Need to support later linkage to alerts and escalations

## Considered Options

- Store each check-in as an independent record with no parent session
- Use a parent Lone Worker record with related child Check-In records
- Use a single record that is repeatedly updated rather than storing separate check-ins

## Decision Outcome

Chosen option: **Use a parent Lone Worker record with related child Check-In records**.

Each check-in is created as its own record, and the system joins it to the currently open Lone Worker parent record for that employee. If no open parent record exists, the system creates one automatically and associates subsequent check-ins to it until the lone-worker period is ended.

## Consequences

This structure improves traceability by preserving both the detailed event stream and the higher-level session context. It also supports filtered inventories, summary fields, and workflow logic that operate at the session level while still retaining child-level detail.

The model introduces relationship and auto-association logic that must be configured carefully, especially around creation of the first check-in of a period and closing of the parent record.

## More Information

The parent record was discussed as the container for all check-ins for the day or lone-worker period, with check-ins automatically joining the open parent record for the person. The parent record was also treated as the main object for inventory views and summary reporting.
