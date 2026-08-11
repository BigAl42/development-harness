---
type: Reference
title: Harness Rules — Model
description: What harness rules are and how they differ from project rules and deploy targets
tags: [harness-rules, architecture, okf]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# Harness Rules — Model

## Three layers

```
┌─────────────────────────────────────────────────────────┐
│  1. Harness Rules (OKF)     okf/harness-rules/*.md      │
│     Portable, harness-agnostic, versioned               │
│     type: Harness Rule                                  │
└──────────────────────────┬──────────────────────────────┘
                           │ derived / mirrored
┌──────────────────────────▼──────────────────────────────┐
│  2. APM Instructions        .apm/instructions/*.md      │
│     Deploy primitives for all harnesses                 │
└──────────────────────────┬──────────────────────────────┘
                           │ apm install (per target)
┌──────────────────────────▼──────────────────────────────┐
│  3. Harness targets (generated, not source of truth)     │
│     Cursor:  .cursor/rules/*.mdc                         │
│     Copilot: .github/instructions/                       │
│     Agents:  .agents/skills/                             │
└──────────────────────────────────────────────────────────┘
```

## Harness rule vs. project rule

| | Harness Rule | Project Rule |
|---|--------------|--------------|
| **Scope** | Cross-project, all repos | One repo / domain |
| **Location** | `development-harness/okf/harness-rules/` | Target project (e.g. `.cursor/rules/`) |
| **Example** | Coding principles, English language | POS views, Tauri build |
| **Distribution** | APM package | Local in project |

## Harness rule vs. Cursor rule

A **Cursor rule** (`.mdc`) is a **deploy target**, not the definition.

- Definition: `okf/harness-rules/<name>.md` (OKF v0.2, `type: Harness Rule`)
- Derivation: `.apm/instructions/<name>.instructions.md`
- Deploy: `apm install` writes `.cursor/rules/<name>.mdc` (when Cursor target is active)

**Never** maintain harness rules directly as `.cursor/rules/` — that is harness-specific and not portable.

## Consumption priority

1. Explicit user instruction
2. Project rules in the target repo
3. Harness rules (this package)
4. General best practices

## Related

- [Harness Deployment](/reference/harness-deployment.md)
- [Applying OKF v0.2](/guides/okf-v0.2-application.md)
