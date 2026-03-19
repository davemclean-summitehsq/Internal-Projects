---
adr: "ADR-008"
title: "Provide separate inventory views for open, completed, and raw check-in data"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "navigation"
  - "reporting"
  - "inventory"
  - "ui"
---

# Provide separate inventory views for open, completed, and raw check-in data

## Context and Problem Statement

Users need operational visibility into current lone-worker sessions, completed sessions, and detailed raw check-in data. A single undifferentiated list would make day-to-day monitoring cumbersome, while fully separating everything into unrelated pages would weaken the relationship between sessions and their check-ins.

The design direction favored parent-record-centered inventories with filtered variants, plus a separate raw check-in inventory when detailed data review is needed.

## Decision Drivers

- Need quick access to active lone-worker sessions
- Need separate visibility into completed sessions
- Need access to raw check-in records without making them the primary navigation model
- Need inventories that support operational use and reporting

## Considered Options

- Present all lone-worker data in one inventory only
- Use parent-record inventories with filtered open and completed views, plus a separate check-in inventory
- Make raw check-ins the main operational inventory

## Decision Outcome

Chosen option: **Use filtered inventory views on the parent Lone Worker record and provide a separate raw Check-In inventory**.

The default inventory is intended to show the parent lone-worker records, with cloned and filtered views for open and completed records. A separate inventory on the check-in object provides access to the underlying raw check-in data when needed.

## Consequences

This gives users a practical operational view while preserving access to detailed records for analysis or troubleshooting. It also reinforces the parent-child architecture by making the parent record the primary operational unit.

The design will require thoughtful default columns, filters, and permissions to keep the experience clear for different user groups.

## More Information

The discussion explicitly described open and completed parent-record listings, a separate raw check-in list, and a parent inventory that could display summary columns such as employee, first check-in, final check-in, duration, alert count, and supervisor.
