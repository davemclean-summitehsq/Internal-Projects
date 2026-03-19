# ADR Metadata Convention

This project uses a lightweight metadata convention in YAML front matter at the top of each ADR.

## Required fields

- `id` — zero-padded ADR number, for example `0001`
- `title` — ADR title
- `status` — one of `proposed`, `accepted`, `superseded`, `deprecated`
- `date` — ISO date of creation or latest material revision
- `decision-makers` — people accountable for the decision
- `consulted` — people materially consulted
- `informed` — people who should be informed
- `category` — practical grouping label such as `data-model`, `workflow`, `configuration`
- `tags` — optional list of useful search labels

## Optional fields

- `supersedes` — ADR IDs replaced by this one
- `superseded-by` — ADR ID that replaces this one
- `depends-on` — ADR IDs that should exist first or strongly influence this ADR
- `deciders-notes` — brief note for governance context

## Example

```yaml
---
id: 0001
title: Use Parent-Child Record Model for Lone Worker Tracking
status: proposed
date: 2026-03-18
decision-makers:
  - Dave McLean
consulted:
  - Liv Chug
informed:
  - Project team
category: data-model
depends-on: []
tags:
  - intelex
  - lone-worker
  - data-model
---
```

## Notes

- Use `proposed` until the ADR is reviewed and approved.
- When an ADR is replaced, keep the old file and mark it `superseded`.
- Prefer stable relative links between ADRs, for example `./0004-escalate-missed-check-ins-via-supervisor-alert-workflow.md`.
- Keep the filename aligned to the title and ID for predictable linking.
