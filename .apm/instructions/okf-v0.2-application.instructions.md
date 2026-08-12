---
applyTo: "okf/**,.apm/**,apm.yml"
description: "OKF v0.2 + Harness Rules: type required, okf/harness-rules/ as source, targets generated only"
harnessRule: okf-v0.2-application
source: okf/guides/okf-v0.2-application.md
---

# OKF v0.2 + Harness Rules

## Source of truth

- **Harness rules:** `okf/harness-rules/*.md` (`type: Harness Rule`)
- **Playbooks/meta:** `okf/guides/`, `okf/concepts/`, `okf/reference/`
- **Not source:** `.cursor/rules/`, `.agents/skills/` (generated targets)

## OKF v0.2 required

- `type` on every concept
- `okf_version: "0.2"` in `okf/index.md`

## Workflow

1. Edit harness rule in `okf/harness-rules/`
2. Mirror `.apm/instructions/` (`harnessRule` + `source` in frontmatter)
3. Run `apm compile --validate` then `apm install` — targets are generated, not edited manually

Write bundle content in English.

Spec: https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md

Source: `okf/guides/okf-v0.2-application.md`
