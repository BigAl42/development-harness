---
name: harness-rules
description: Apply when loading, authoring, or deploying portable Harness Rules from the OKF v0.2 bundle. Use for cross-project agent context, OKF conformance, or mirroring harness-rules to APM instructions — not for editing Cursor rules directly.
---

# Harness Rules Skill

Portable **Harness Rules** from `okf/harness-rules/` — harness-agnostic, not Cursor-specific.

## When to Use

- Consume or write harness rules
- Apply OKF v0.2 + harness rules model
- Mirror OKF → APM instructions
- Connect consumer project to `BigAl42/development-harness`

## Do Not

- Do **not** maintain harness rules directly in `.cursor/rules/` — those are generated targets
- Do **not** put project-specific rules in the harness package

## Model

1. **Source:** `okf/harness-rules/*.md` (`type: Harness Rule`)
2. **APM:** `.apm/instructions/*.instructions.md`
3. **Targets:** `.cursor/rules/`, `.github/instructions/` (generated via `apm install`)

See [Harness Rules — Model](/okf/concepts/harness-rules-model.md).

All bundle text is English — see [English Language](/okf/harness-rules/english-language.md).

Conflict order: [Rules Precedence](/okf/harness-rules/rules-precedence.md).
Project patterns: [Rule Layering](/okf/guides/rule-layering.md).
Consumer extractions: [Extractions](/okf/reference/extractions/README.md).

## Spec

https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
