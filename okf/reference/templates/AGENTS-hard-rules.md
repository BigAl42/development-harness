---
type: Reference
title: "Template: AGENTS.md hard rules"
description: Copy-paste skeleton for project non-negotiable must/never rules
tags: [template, agents, project-rules]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
---

# Template: `AGENTS.md` hard rules

Copy into the consumer repo as `AGENTS.md`. Fill stack and must/never. This file **wins** over project OKF when they conflict — see [Rules Precedence](/harness-rules/rules-precedence.md).

```markdown
# Agent hard rules

## Stack (project-specific)

- Runtime / framework / data store — …
- Primary commands: lint, test, build, …

## Must

- …
- On architecture/schema change: update `okf/` + `okf/log.md` and run OKF validation
- Session/tenant loaders: distinguish error vs empty (see harness rule session-tenant-empty-state)

## Never

- …
- Never map auth/load failure to “create tenant” first-run UX
- Never silently `catch` and clear entity lists without error state

## Quality gates (concrete)

- Lint: `…`
- Test: `…`
- OKF (if present): `…`
- Build: `…`
```
