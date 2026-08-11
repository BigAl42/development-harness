---
type: Reference
title: Harness Deployment
description: Ableitungskette von OKF Harness Rules zu APM Instructions und Harness-Targets
tags: [harness-rules, apm, deployment]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# Harness Deployment

## Ableitungskette

| Harness Rule (OKF) | APM Instruction | Cursor (generiert) | Copilot (generiert) |
|--------------------|-----------------|--------------------|---------------------|
| `harness-rules/instruction-following.md` | `instruction-following.instructions.md` | `.cursor/rules/instruction-following.mdc` | `.github/instructions/` |
| `harness-rules/communication.md` | `communication.instructions.md` | `.cursor/rules/communication.mdc` | … |
| `harness-rules/coding-principles.md` | `coding-principles.instructions.md` | `.cursor/rules/coding-principles.mdc` | … |
| `harness-rules/context-reasoning.md` | `context-reasoning.instructions.md` | `.cursor/rules/context-reasoning.mdc` | … |
| `harness-rules/quality-gates.md` | `quality-gates.instructions.md` | `.cursor/rules/quality-gates.mdc` | … |
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | `.cursor/rules/okf-v0.2-application.mdc` | … |

## Producer-Repo (development-harness)

- **Committen:** `okf/harness-rules/`, `.apm/instructions/`, `apm.yml`, `apm.lock.yaml`
- **Nicht committen:** `.cursor/rules/`, `.agents/skills/` (generierte Targets — siehe `.gitignore`)

## Consumer-Projekt

```yaml
# apm.yml
dependencies:
  apm:
    - BigAl42/development-harness#v0.2.0
```

```bash
apm install    # deployt Harness Rules in erkannte Targets
```

Projekt-eigene Regeln bleiben im Consumer-Repo und ergänzen — ersetzen nicht — die Harness Rules.

## Workflow bei Änderungen

1. Harness Rule in `okf/harness-rules/` bearbeiten
2. `.apm/instructions/` spiegeln (`harnessRule`-Referenz beibehalten)
3. `apm install` im Producer oder Consumer
4. Generierte Targets entstehen neu — nicht manuell editieren
