---
id: 0005
title: Close Lone Worker Period by Proximity to Expected End Location
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: business-rules
depends-on:
  - 0006
  - 0011
tags:
  - intelex
  - lone-worker
  - geolocation
  - closeout
---

# Close Lone Worker Period by Proximity to Expected End Location

## Context and Problem Statement

The application needs a practical way to determine when a worker has completed their lone worker period. Time alone is not sufficient, because workers may finish early, late, or deviate from the expected schedule.

Related ADRs: [0006](./0006-store-operational-rules-in-a-preferences-object.md), [0011](./0011-record-lone-worker-completion-intent-at-the-first-check-in.md), [0004](./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md).

## Decision Drivers

- The application must recognize completion of a lone worker period
- Location matters more than planned end time in many field scenarios
- The completion rule should be configurable
- The design should reduce false positives while remaining practical
- The approach should work with geolocation data captured at check-in

## Considered Options

- Mark the lone worker period complete when a check-in occurs within a configurable distance of the expected end location
- Require the user to explicitly click an end period action
- Mark the period complete automatically at the expected end time
- Require supervisor approval for all closures

## Decision Outcome

Chosen option: **Mark the lone worker period complete when a check-in occurs within a configurable distance of the expected end location**.

This aligns completion with physical return rather than only schedule intent.

## Consequences

- Good, because the completion rule is anchored in the worker’s expected return location
- Good, because the rule is configurable for different operating contexts
- Good, because users do not need a separate closeout workflow in the normal case
- Bad, because GPS accuracy and edge cases may create false positives or false negatives
- Bad, because the logic is not perfect and may still require supervisor override

## Confirmation

The implementation is compliant if:

- the first check-in can capture expected ending location
- subsequent check-ins calculate distance from that location
- the parent record can be closed when the measured distance is within the configured tolerance
- a supervisor can override and close the record when appropriate

## Pros and Cons of the Options

### Mark the lone worker period complete when a check-in occurs within a configurable distance of the expected end location

- Good, because it is operationally practical
- Good, because it aligns with the field use case
- Good, because it supports configurable distance thresholds
- Bad, because geolocation data quality can vary

### Require the user to explicitly click an end period action

- Good, because it is explicit
- Good, because it may reduce ambiguity
- Bad, because it adds one more step for users
- Bad, because users may forget to do it

### Mark the period complete automatically at the expected end time

- Good, because it is easy to automate
- Bad, because it does not verify actual return
- Bad, because it could mask real risk

### Require supervisor approval for all closures

- Good, because oversight is strong
- Bad, because it creates unnecessary administrative effort for normal cases
- Bad, because it slows down closure of compliant periods

## More Information

The acceptable distance should be stored in preferences and should support multiple units. Supervisor alerts should support a manual end-of-day closure when the worker did return safely but did not complete the normal final check-in.
