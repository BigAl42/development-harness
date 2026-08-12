---
type: Harness Rule
title: OKF Knowledge Workflow
description: When a repo has okf/, read it before structural work and update it in the same change
tags: [harness-rules, okf, knowledge, maintenance]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T05:45:00Z
sources:
  - id: energy-tracker-okf-mdc
    resource: /energy-tracker/.cursor/rules/okf.mdc
    title: OKF always-on rule (generalized)
  - id: energy-tracker-agents
    resource: /energy-tracker/AGENTS.md
    title: Hard rules vs OKF knowledge
---

# OKF Knowledge Workflow

Applies when the target repo contains an `okf/` bundle. Skip if there is no OKF.

## Before structural work

Before architecture, schema, ACL, deploy, notifications/push, or similar cross-cutting work:

1. Read `okf/index.md`
2. Open the relevant domain `index.md`
3. Read the concept files you will touch

## After such a change (same PR / commit set)

- Update or add OKF concepts (**English**)
- Append `okf/log.md`
- Run the project OKF validation command (commonly `npm run test:okf`)

## Priority

Hard rules in `AGENTS.md` and project `.cursor/rules` **override** OKF. On conflict, fix OKF in the same change.

## Do not put in OKF

Pure typos, copy tweaks, or UI-only cosmetics with no behavioral or schema impact.

## Boundary

Concrete domain indexes and validation scripts stay in the target repo. This rule defines the **consume/maintain** principle only.
