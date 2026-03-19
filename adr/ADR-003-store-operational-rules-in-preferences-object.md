---
adr: "ADR-003"
title: "Store operational rules in a Preferences object"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "configuration"
  - "preferences"
  - "reusability"
  - "productization"
---

# Store operational rules in a Preferences object

## Context and Problem Statement

The solution requires operational rules that may vary by client or deployment, including check-in frequency, alert grace period, whether alerts are active, and permissible distance from the projected ending location. Hard-coding these rules into logic or forms would reduce reusability and make the solution harder to adapt commercially.

The design direction established an admin-managed Preferences object to hold these rules.

## Decision Drivers

- Need configurability without redesign
- Need to support client-specific operating rules
- Need to improve maintainability of timing and threshold logic
- Need to allow product-style reuse across different deployments
- Need to support show/hide and required/non-required behavior from configuration

## Considered Options

- Hard-code operational rules directly in form logic and workflows
- Store operational rules in a dedicated Preferences object
- Distribute settings across multiple unrelated admin objects

## Decision Outcome

Chosen option: **Store operational rules in a dedicated Preferences object**.

This object is intended to hold check-in frequency, alert grace period, whether alerts are activated, and permissible distance thresholds for final check-in validation. Units and measures are intended to be configurable using category-based time and distance fields.

## Consequences

This improves reusability and makes the solution more adaptable to different client needs. It also creates a clearer administrative boundary between structural design and operating policy.

The tradeoff is additional setup complexity, including management of custom unit categories and configuration-driven behavior on forms and logic.

## More Information

The discussion specifically introduced a Preferences area and described fields for frequency, grace period, alert activation, and permissible distance, including support for configurable units such as minutes, hours, days, meters, kilometers, feet, and miles.
