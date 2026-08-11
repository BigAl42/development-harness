---
applyTo: "**"
description: "OKF v0.2 + Harness Rules: type-Pflichtfeld, okf/harness-rules/ als Source, Targets nur generiert"
harnessRule: okf-v0.2-application
source: okf/guides/okf-v0.2-application.md
---

# OKF v0.2 + Harness Rules

## Source of Truth

- **Harness Rules:** `okf/harness-rules/*.md` (`type: Harness Rule`)
- **Playbooks/Meta:** `okf/guides/`, `okf/concepts/`, `okf/reference/`
- **Nicht** Source: `.cursor/rules/`, `.agents/skills/` (generierte Targets)

## OKF v0.2 Pflicht

- `type` auf jedem Concept
- `okf_version: "0.2"` in `okf/index.md`

## Workflow

1. Harness Rule in `okf/harness-rules/` bearbeiten
2. `.apm/instructions/` spiegeln (`harnessRule` + `source` im Frontmatter)
3. `apm install` — Targets werden generiert, nicht manuell gepflegt

Spec: https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md

Quelle: `okf/guides/okf-v0.2-application.md`
