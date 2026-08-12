---
type: Harness Rule
title: Domain Logic First
description: Pure domain calc without I/O; test metrics before UI; keep parallel modules decoupled
tags: [harness-rules, architecture, testing, domain]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T05:45:00Z
sources:
  - id: kredit-tracker-agents
    resource: /kredit-tracker/AGENTS.md
    title: Calc-first / module boundaries (generalized)
  - id: kredit-tracker-vorsorge
    resource: /kredit-tracker/.cursor/rules/vorsorge.mdc
    title: Pure calc + test then UI
  - id: kredit-tracker-loans
    resource: /kredit-tracker/.cursor/rules/loans-annuity.mdc
    title: Domain isolation
---

# Domain Logic First

## Pure calculation

Put domain math and projections in library modules **without** database, network, or framework I/O so they stay unit-testable.

## Metrics before chrome

For new KPIs, CTAs driven by numbers, or “close the gap” style features: implement calculation + tests first, then wire UI. Do not ship display-only text that claims a metric the lib does not compute.

## Parallel modules

When the product has parallel domains (e.g. loans vs retirement, meters vs tariffs), keep core libs free of cross-imports except deliberate UI or application-layer bridges.

If a bridge means “apply / take over” a value, **write** the target state — do not only link to another screen.

## Boundary

File paths, test script names, and domain names belong in project rules. See also [Coding Principles](/harness-rules/coding-principles.md) and [Quality Gates](/harness-rules/quality-gates.md).
