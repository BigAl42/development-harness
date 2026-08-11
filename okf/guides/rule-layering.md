---
type: Playbook
title: Rule Layering
description: Two patterns for project agent knowledge — living overview vs OKF bundle plus AGENTS.md
tags: [harness-rules, playbook, composition]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-vs-event-pos-layering
    resource: https://github.com/BigAl42/energy-tracker
    title: Pattern B from energy-tracker vs Pattern A from event-pos-desktop
  - id: event-pos-overview
    resource: https://github.com/BigAl42/event-pos-desktop
    title: APP_OVERVIEW.md + granular .mdc rules
---

# Rule Layering

Consumer projects combine **portable Harness Rules** with local project knowledge. Two proven patterns:

## Pattern A — Living overview

**Examples:** event-pos-desktop (`APP_OVERVIEW.md` + several always-on `.mdc` rules)

| Layer | Role |
|-------|------|
| Harness Rules (APM) | Cross-project principles |
| Granular `.mdc` rules | Generic UI/architecture + specific extensions |
| `APP_OVERVIEW.md` (+ sync rule) | Single living catalog of views, flows, paths |

**Fits:** Single-app UX catalogs, desktop apps with few domains, teams that want one short overview file.

## Pattern B — OKF bundle + hard rules

**Examples:** energy-tracker (`AGENTS.md` + `okf/` domains + thin `.mdc`)

| Layer | Role |
|-------|------|
| Harness Rules (APM) | Cross-project principles |
| `AGENTS.md` | Non-negotiable must/never (wins over OKF) |
| Thin always-on `.mdc` | Pointers (OKF consume, session empty-state, …) |
| `okf/` domains + `log.md` | Deep domain knowledge + agent changelog |

**Fits:** Multi-domain backends, ops/deploy/schema-heavy systems, projects that need validators and domain indexes.

## Composition tips

- Prefer **generic rule + specific extension** over duplicating the same principle in many files
- Keep **concrete commands** in project rules / templates, not in Harness Rule bodies
- See [Rules Precedence](/harness-rules/rules-precedence.md) for conflict order
- Optional: cite `harnessRule: <name>` in project rule frontmatter for provenance

## Choosing

| Signal | Prefer |
|--------|--------|
| Few domains, heavy UI navigation | Pattern A |
| Many domains, schema/ACL/deploy | Pattern B |
| Need automated knowledge validation | Pattern B |
| Want <120-line single overview | Pattern A |
