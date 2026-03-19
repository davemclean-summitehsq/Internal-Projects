---
adr: "ADR-007"
title: "Use helper and calculated fields to support timing, alerting, and reporting behavior"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "business-logic"
  - "helper-fields"
  - "calculated-fields"
  - "reporting"
---

# Use helper and calculated fields to support timing, alerting, and reporting behavior

## Context and Problem Statement

The solution requires derived values that are central to behavior and reporting, including expected next deadline, whether alert conditions are met, relationships to alert objects, and summary-level display fields. Computing all of this only inside workflows or only at runtime would make the design harder to inspect and report on.

The discussion explicitly called for helper and calculated fields on the parent object.

## Decision Drivers

- Need to support time-driven behavior
- Need to simplify alert logic and reporting
- Need to expose summary-level values on parent records
- Need to support relationships and derived inventories

## Considered Options

- Keep all derived logic only inside workflows or scripts
- Use helper and calculated fields to materialize core derived values
- Minimize stored derived values and calculate almost everything on demand

## Decision Outcome

Chosen option: **Use helper and calculated fields for core operational behavior and reporting**.

The design includes helper or calculated fields for next expected check-in deadline, alert eligibility or alert timing, and relationships needed to expose related alert objects and reporting-friendly summaries.

## Consequences

This makes core behavior more visible in the data model and supports cleaner inventory views and reporting. It also reduces some complexity in downstream workflow steps by materializing important derived values.

The tradeoff is a more complex schema with fields whose purpose is primarily operational or technical rather than directly user-entered.

## More Information

The discussion called out helper fields for expected deadlines, alert-related calculations, and relationships needed to expose lone-worker alerts from the parent record context. The design also relied on summary-style fields such as first and most recent check-in details.
