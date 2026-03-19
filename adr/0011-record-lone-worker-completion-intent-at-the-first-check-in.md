---
id: 0011
title: Record Lone Worker Completion Intent at the First Check-In
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
  - 0001
  - 0002
tags:
  - intelex
  - lone-worker
  - geolocation
  - planning
---

# Record Lone Worker Completion Intent at the First Check-In

## Context and Problem Statement

The application needs enough information at the start of a lone worker period to determine when the period should be considered complete and where the worker is expected to return. Without this information, later completion logic becomes guesswork.

Related ADRs: [0002](./0002-use-single-check-in-form-for-end-users.md), [0005](./0005-close-lone-worker-period-by-proximity-to-expected-end-location.md).

## Decision Drivers

- The system needs an expected end condition
- Static defaults such as a permanent home base may create false positives
- Workers may start and end from different operational locations on different days
- Final check-in logic depends on comparing actual versus expected end location

## Considered Options

- Capture expected ending time and expected ending location at the first check-in of each lone worker period
- Use a permanent employee home base only
- Ask admins or supervisors to pre-assign expected ending details
- Do not capture expected ending details and rely only on manual closure

## Decision Outcome

Chosen option: **Capture expected ending time and expected ending location at the first check-in of each lone worker period**.

This reflects day-specific field reality better than fixed defaults and enables practical automated closeout logic.

## Consequences

- Good, because each lone worker period has an explicit expected return context
- Good, because it reduces false positives caused by static defaults
- Good, because proximity-based completion becomes feasible
- Bad, because the first check-in form requires more information than later check-ins
- Bad, because users may still enter imperfect intent data

## Confirmation

The implementation is compliant if:

- the first check-in for a new lone worker period captures expected ending time and expected ending location
- those values are stored on the parent Lone Worker record
- later completion logic references those values

## Pros and Cons of the Options

### Capture expected ending time and expected ending location at the first check-in of each lone worker period

- Good, because it supports day-specific reality
- Good, because it improves closeout automation
- Bad, because it adds required fields at period start

### Use a permanent employee home base only

- Good, because setup is simpler
- Bad, because it can be wrong on many days
- Bad, because it risks false positives and false negatives

### Ask admins or supervisors to pre-assign expected ending details

- Good, because oversight is stronger
- Bad, because it creates administrative overhead
- Bad, because plans may change during the day

### Do not capture expected ending details and rely only on manual closure

- Good, because the worker flow is shorter
- Bad, because automation for completion is weak
- Bad, because supervisors must close records more often

## More Information

This decision pairs directly with the proximity-based completion decision and should be implemented together.
