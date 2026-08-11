---
title: OKF → APM Mapping
description: Wie OKF-Quelldateien in APM-Instructions und Harness-Ziele deployt werden
tags:
  - apm
  - reference
status: active
version: 0.1.0
---

# OKF → APM Mapping

| OKF-Quelle | APM Instruction | applyTo | alwaysApply |
|------------|-----------------|---------|-------------|
| `guides/instruction-following.md` | `.apm/instructions/instruction-following.instructions.md` | `**` | ja |
| `guides/communication.md` | `.apm/instructions/communication.instructions.md` | `**` | ja |
| `guides/coding-principles.md` | `.apm/instructions/coding-principles.instructions.md` | `**` | ja |
| `guides/context-reasoning.md` | `.apm/instructions/context-reasoning.instructions.md` | `**` | ja |
| `guides/quality-gates.md` | `.apm/instructions/quality-gates.instructions.md` | `**` | nein (projekt-anpassbar) |
| `concepts/agent-principles.md` | Skill `okf-rules` (Referenz) | — | — |

## Workflow

1. OKF-Dateien in `okf/` bearbeiten (Source of Truth)
2. Entsprechende `.apm/instructions/*.instructions.md` synchron halten
3. `apm install` im Repo oder im Consumer-Projekt ausführen
4. Optional: projekt-spezifische Erweiterungen als zusätzliche APM-Dependencies

## Consumer-Projekt

```yaml
# apm.yml im Zielprojekt
dependencies:
  apm:
    - BigAl42/development-harness#v0.1.0
```
