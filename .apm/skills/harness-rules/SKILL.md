---
name: harness-rules
description: Apply when loading, authoring, or deploying portable Harness Rules from the OKF v0.2 bundle. Use for cross-project agent context, OKF conformance, or mirroring harness-rules to APM instructions — not for editing Cursor rules directly.
---

# Harness Rules Skill

Portable **Harness Rules** aus `okf/harness-rules/` — harness-agnostisch, nicht Cursor-spezifisch.

## When to Use

- Harness Rules konsumieren oder schreiben
- OKF v0.2 + Harness-Rules-Modell anwenden
- OKF → APM Instructions spiegeln
- Consumer-Projekt mit `BigAl42/development-harness` verbinden

## Nicht tun

- Harness Rules **nicht** direkt in `.cursor/rules/` pflegen — das sind generierte Targets
- Projekt-spezifische Regeln **nicht** ins Harness-Package legen

## Modell

1. **Source:** `okf/harness-rules/*.md` (`type: Harness Rule`)
2. **APM:** `.apm/instructions/*.instructions.md`
3. **Targets:** `.cursor/rules/`, `.github/instructions/` (generiert via `apm install`)

Siehe [Harness Rules — Modell](/okf/concepts/harness-rules-model.md).

## Spec

https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
