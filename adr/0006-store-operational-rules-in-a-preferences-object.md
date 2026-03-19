---
id: 0006
title: Store Operational Rules in a Preferences Object
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: configuration
depends-on: []
tags:
  - intelex
  - lone-worker
  - preferences
  - configuration
---

# Store Operational Rules in a Preferences Object

## Context and Problem Statement

The application includes several operational rules that may vary across organizations, including check-in frequency, grace period, alert activation, and permissible distance from expected ending location. These rules should be maintainable without reconfiguration of core objects and forms.

Related ADRs: [0003](./0003-use-configurable-time-driven-check-in-monitoring.md), [0005](./0005-close-lone-worker-period-by-proximity-to-expected-end-location.md).

## Decision Drivers

- Rules will vary by client and possibly by deployment phase
- Productization and reuse are goals
- Administrators need controlled configurability
- Operational settings should be transparent and reportable
- Core architecture should avoid hard-coded client-specific assumptions

## Considered Options

- Store configurable operational rules in a Preferences object
- Hard-code the rules in forms, formulas, and workflow logic
- Scatter settings across multiple unrelated objects
- Keep settings outside the application and rely on deployment notes

## Decision Outcome

Chosen option: **Store configurable operational rules in a Preferences object**.

This centralizes business rules, improves maintainability, and supports a reusable product-like design.

## Consequences

- Good, because administrators have a single place to manage rules
- Good, because future deployments can vary without redesign
- Good, because formulas and workflows can reference one configuration source
- Bad, because preference retrieval logic must be reliable
- Bad, because setup governance is required to avoid invalid combinations

## Confirmation

The implementation is compliant if:

- check-in frequency, grace period, alert activation, and permissible distance are managed from a dedicated settings object or area
- the core logic references those settings rather than hard-coded constants

## Pros and Cons of the Options

### Store configurable operational rules in a Preferences object

- Good, because it centralizes administration
- Good, because it supports commercial reuse
- Good, because it improves clarity of system behavior
- Bad, because it adds one more object and dependency

### Hard-code the rules in forms, formulas, and workflow logic

- Good, because it may be faster initially
- Bad, because every policy change becomes a design change
- Bad, because reuse across clients is weak

### Scatter settings across multiple unrelated objects

- Good, because each object can own its local parameters
- Bad, because governance becomes fragmented
- Bad, because understanding effective behavior becomes difficult

### Keep settings outside the application and rely on deployment notes

- Good, because the application remains simpler
- Bad, because runtime behavior cannot adapt
- Bad, because the implementation diverges from documented policy too easily

## More Information

At minimum, the preferences area should support check-in frequency, alert grace period, alerts active or inactive, permissible final-check-in distance, and supported time and distance units where needed.
