---
adr: "ADR-002"
title: "Use a single end-user check-in form for start, progress, and end-of-day activity"
status: "proposed"
date: "2026-03-19"
deciders:
  - "Dave McLean"
consulted:
  - "Liv Chug"
informed: []
tags:
  - "ui"
  - "form-strategy"
  - "usability"
---

# Use a single end-user check-in form for start, progress, and end-of-day activity

## Context and Problem Statement

The solution needs an end-user interaction model that is simple enough for repeated use in the field while still capturing start-of-period information, periodic check-ins, and final closure behavior. Using multiple forms could make the workflow more explicit, but would also add complexity for workers who need a fast and repeatable process.

The design discussion favored a simplified end-user experience centered on one check-in form.

## Decision Drivers

- Need to reduce friction for end users
- Need to support repeated field use throughout the day
- Need to capture both routine and final check-ins within a consistent interaction pattern
- Need to keep the end-user workflow simpler than the supervisor workflow

## Considered Options

- Use separate forms for initial check-in, recurring check-ins, and end-of-day closure
- Use a single end-user check-in form with behavior that supports different points in the lone-worker period
- Use a predominantly background or automatic process with minimal user form interaction

## Decision Outcome

Chosen option: **Use a single end-user check-in form**.

The form captures the employee, check-in time, check-in location, notes, and, on initial use, expected ending location and expected end time for the lone-worker period. Final closure is also handled through the same overall user-facing check-in experience rather than by introducing a separate end-user form.

## Consequences

This improves usability and lowers training burden by presenting one consistent end-user pattern. It also aligns well with mobile or field-oriented use where simplicity matters.

The form will need conditional behavior so that some fields are only relevant at certain points in the process. That increases the importance of defaults, read-only behavior, and automation to avoid confusion.

## More Information

The discussion explicitly emphasized wanting one form for the end user while giving supervisors more control in their own alert-handling flow. The expected ending location and end-time inputs were introduced as part of this unified check-in pattern.
