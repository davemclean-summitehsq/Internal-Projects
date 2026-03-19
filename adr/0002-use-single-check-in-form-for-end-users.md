---
id: 0002
title: Use a Single Check-In Form for End Users
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Lone Worker project team
category: user-experience
depends-on:
  - 0001
tags:
  - intelex
  - lone-worker
  - forms
  - ux
---

# Use a Single Check-In Form for End Users

## Context and Problem Statement

Workers need a simple, repeatable experience for checking in during a lone worker period. The application should minimize end-user confusion and avoid requiring workers to choose among multiple similar forms or workflows.

Related ADRs: [0001](./0001-use-parent-child-record-model.md), [0007](./0007-auto-populate-employee-and-supervisor-context.md), [0011](./0011-record-lone-worker-completion-intent-at-the-first-check-in.md).

## Decision Drivers

- The end-user experience must be simple
- Workers may be mobile, distracted, or operating under time pressure
- The form should support both the first and subsequent check-ins with minimal friction
- The solution should reduce training burden
- The design should still capture additional data needed at the first check-in

## Considered Options

- Use one primary check-in form for all worker interactions
- Use separate forms for start-of-day, mid-day, and final check-in
- Use a wizard or multi-step process
- Use no dedicated form and rely on task-driven prompts only

## Decision Outcome

Chosen option: **Use one primary check-in form for all worker interactions**.

This keeps the worker experience simple while still allowing the system to interpret whether the check-in starts, continues, or ends a lone worker period.

## Consequences

- Good, because the worker only has to learn one primary interaction pattern
- Good, because mobile adoption and ease of use should improve
- Good, because the same form can drive creation or updating of the parent record
- Bad, because some fields may need conditional behavior depending on whether it is the first or later check-in
- Bad, because final check-in behavior must be inferred or automated rather than explicitly separated

## Confirmation

The implementation is compliant if:

- workers access one main check-in entry point
- the same form can support first and subsequent check-ins
- conditional behavior exists for expected ending details when required

## Pros and Cons of the Options

### Use one primary check-in form for all worker interactions

- Good, because it minimizes cognitive load
- Good, because it supports reuse of validation and automation
- Good, because it simplifies training
- Bad, because the form may need more conditional logic

### Use separate forms for start-of-day, mid-day, and final check-in

- Good, because each form can be narrowly tailored
- Bad, because workers must understand which form to use when
- Bad, because maintenance effort increases
- Bad, because user error risk increases

### Use a wizard or multi-step process

- Good, because it can guide the worker through a structured sequence
- Neutral, because it may fit complex processes
- Bad, because it is heavier than needed for fast check-ins
- Bad, because repeated daily use may become cumbersome

### Use no dedicated form and rely on task-driven prompts only

- Good, because it emphasizes exception handling
- Bad, because regular check-ins become less natural
- Bad, because it weakens the normal-use path

## More Information

The first check-in should capture additional information such as expected ending time and expected ending location. Later check-ins can reuse the same form with those values displayed or inferred from the parent record.
