---
adr: "ADR-009"
title: "Sequence implementation by building structural objects and forms before advanced business logic"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "implementation"
  - "sequencing"
  - "delivery"
  - "maintainability"
---

# Sequence implementation by building structural objects and forms before advanced business logic

## Context and Problem Statement

The design includes several advanced behaviors, including automatic parent creation and joining, time-driven alerting, reverse relationships, and location-based closure logic. Attempting to complete all of these at once would create unnecessary delivery risk and make troubleshooting harder.

The agreed approach was to build the structural parts of the solution first and defer unresolved logic until the foundational pieces are in place.

## Decision Drivers

- Need a practical and teachable implementation path
- Need to reduce delivery risk while learning unfamiliar configuration areas
- Need to establish the data model and forms before testing advanced logic
- Need to avoid blocking progress on one difficult configuration point

## Considered Options

- Build the full solution including business logic in one pass
- Build objects, fields, relations, and forms first, then layer on advanced logic
- Prototype only the alert workflow first before defining the full structure

## Decision Outcome

Chosen option: **Build structural components first, then add advanced business logic iteratively**.

The first implementation pass should prioritize the application structure, objects, relations, fields, and forms. More complex behaviors such as auto-creation, advanced relationship handling, and alerting logic can then be added and debugged in later passes.

## Consequences

This reduces the chance that one difficult configuration area blocks the rest of the build. It also creates a clearer checkpoint for review before layering on complex automation.

The tradeoff is that the early build may not yet be end-to-end testable, and some design assumptions will remain provisional until the logic layer is added.

## More Information

The discussion explicitly recommended building the application objects, fields, relations, and forms first, skipping or documenting blockers as they arise, and returning later to business logic and workflow details once the structural pieces are in place.
