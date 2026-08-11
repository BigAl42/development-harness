---
type: Playbook
title: OKF Changelog (log.md)
description: How to maintain okf/log.md as the agent-oriented living changelog
tags: [okf, playbook, changelog]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-okf-log
    resource: https://github.com/BigAl42/energy-tracker
    title: okf/log.md practice (generalized)
---

# OKF Changelog (`log.md`)

`okf/log.md` is the **agent-oriented** dated changelog for knowledge and architecture deltas. It is not a product release notes file.

## When to write

Same PR/change as concept updates — architecture, schema, ACL, deploy, or other domain shifts that agents must know next time.

## Format

```markdown
## YYYY-MM-DD

* **Creation** | **Update** | **Deprecation**: short factual note
* Link concepts when useful: `[Title](/domain/file.md)`
```

Newest dates at the top (or consistently one direction — match the project).

## Quality

- Short bullets; no essays
- What changed for agents, not marketing copy
- Prefer stable paths and type names
- Product-facing changelogs (`WHATS_NEW`, release notes) stay separate

## Pattern note

Projects without a full OKF bundle may use a single living overview (`APP_OVERVIEW.md`) instead — see [Rule Layering](/guides/rule-layering.md).
