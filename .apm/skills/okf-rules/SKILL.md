---
name: okf-rules
description: Apply when loading or applying cross-project OKF rules from the development-harness bundle. Use when setting up agent context, reviewing rule compliance, or syncing OKF source files to APM instructions.
---

# OKF Rules Skill

Lädt und wendet übergreifende Regeln aus dem OKF-Bundle `okf/` an.

## When to Use

- Agent-Kontext für ein neues Projekt einrichten
- Prüfen, ob Antworten und Code den Harness-Regeln entsprechen
- OKF-Quelldateien mit `.apm/instructions/` synchron halten
- Consumer-Projekt mit `BigAl42/development-harness` verbinden

## OKF-Struktur

```
okf/
├── index.md              # Manifest
├── concepts/             # Grundprinzipien
├── guides/               # Anwendbare Regeln
└── reference/            # APM-Mapping
```

## Kern-Guides (always apply)

| Datei | Thema |
|-------|-------|
| `guides/instruction-following.md` | Alle Anweisungen vollständig befolgen |
| `guides/communication.md` | Code-Zitate, Prosa, Links |
| `guides/coding-principles.md` | Scope, Konventionen, Tests |
| `guides/context-reasoning.md` | Konversations-Intent |

## Workflow

1. Relevante OKF-Datei lesen
2. Bei Änderungen: OKF zuerst, dann `.apm/instructions/` spiegeln
3. `apm install` ausführen
4. Mapping siehe `okf/reference/apm-mapping.md`

## Agent-Prinzipien

Siehe `okf/concepts/agent-principles.md` — echte Umgebung, Autonomie, minimale Diffs.
