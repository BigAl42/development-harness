---
title: BigAl42 Development Harness
description: Übergreifende Agent-Regeln und Skills für alle Projekte
version: 0.1.0
status: active
tags:
  - okf
  - agent-rules
  - apm
  - cursor
author: BigAl42
---

# BigAl42 Development Harness — OKF Bundle

Portable Wissensbasis für AI-Coding-Agenten. Dieses OKF-Bundle ist die **Single Source of Truth** für übergreifende Regeln; APM deployt daraus Instructions und Skills in Cursor, Copilot, Claude Code und andere Harnesses.

## Kategorien

| Pfad | Inhalt |
|------|--------|
| [concepts/agent-principles.md](concepts/agent-principles.md) | Grundprinzipien für Agent-Verhalten |
| [guides/instruction-following.md](guides/instruction-following.md) | Alle Anweisungen vollständig befolgen |
| [guides/communication.md](guides/communication.md) | Kommunikation, Code-Zitate, Prosa-Qualität |
| [guides/coding-principles.md](guides/coding-principles.md) | Code-Schreibprinzipien (Scope, Konventionen) |
| [guides/quality-gates.md](guides/quality-gates.md) | Tests und Builds vor Commit |
| [guides/context-reasoning.md](guides/context-reasoning.md) | Konversationshistorie und Intent |
| [reference/apm-mapping.md](reference/apm-mapping.md) | Mapping OKF → APM → Harness-Ziele |

## Verwendung

1. **Als APM-Package**: In `apm.yml` des Zielprojekts `BigAl42/development-harness` als Dependency eintragen, dann `apm install`.
2. **Direkt**: OKF-Dateien in den Agent-Kontext laden (z. B. `@okf/guides/coding-principles.md`).
3. **Cursor Rules**: Nach `apm install` werden Instructions unter `.github/instructions/` bzw. harness-spezifischen Pfaden deployed.

## Herkunft

Extrahiert aus übergreifenden Cursor User Rules und generalisierten Mustern aus bestehenden Projekten (z. B. event-pos-desktop).
