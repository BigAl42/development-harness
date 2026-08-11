---
type: Reference
title: OKF → APM Mapping
description: Wie OKF-v0.2-Quelldateien in APM-Instructions und Harness-Ziele deployt werden
tags: [apm, reference, okf]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:15:00Z
---

# OKF → APM Mapping

| OKF-Quelle | APM Instruction | applyTo | Priorität |
|------------|-----------------|---------|-----------|
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | `**` | immer (Meta) |
| `guides/instruction-following.md` | `instruction-following.instructions.md` | `**` | hoch |
| `guides/communication.md` | `communication.instructions.md` | `**` | hoch |
| `guides/coding-principles.md` | `coding-principles.instructions.md` | `**` | hoch |
| `guides/context-reasoning.md` | `context-reasoning.instructions.md` | `**` | hoch |
| `guides/quality-gates.md` | `quality-gates.instructions.md` | `**` | Template |
| `concepts/agent-principles.md` | Skill `okf-rules` (Referenz) | — | — |

## Workflow

1. OKF-v0.2-Concept in `okf/` bearbeiten (`type` Pflicht)
2. `okf/index.md` und `okf/log.md` aktualisieren
3. Entsprechende `.apm/instructions/` spiegeln
4. `apm install` ausführen

## Consumer-Projekt

```yaml
dependencies:
  apm:
    - BigAl42/development-harness#v0.1.0
```
