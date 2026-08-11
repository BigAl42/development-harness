# development-harness

Übergreifender **APM-Package** mit **OKF-Bundle** (Open Knowledge Format) für AI-Coding-Agenten — Regeln und Skills, die in allen BigAl42-Projekten wiederverwendet werden.

## Architektur

```
development-harness/
├── okf/                    # OKF Source of Truth (portabel, tool-agnostisch)
├── .apm/
│   ├── instructions/       # APM Instructions (deployt nach apm install)
│   └── skills/             # APM Skills
├── apm.yml                 # Package-Manifest
└── apm.lock.yaml           # Pinning (nach apm install)
```

**Schichten:**

1. **OKF** (`okf/`) — strukturiertes Markdown mit YAML-Frontmatter, versioniert in Git
2. **APM** (`.apm/`) — deploybare Primitives für Cursor, Copilot, Claude Code, …
3. **Harness-Ziele** — nach `apm install` z. B. `.agents/skills/`, `.github/instructions/`

## Enthaltene OKF-Regeln (v0.1.0)

Extrahiert aus übergreifenden Cursor User Rules und generalisierten Mustern aus [event-pos-desktop](https://github.com/BigAl42/event-pos-desktop):

| Regel | Datei | alwaysApply |
|-------|-------|-------------|
| Instruction Following | `okf/guides/instruction-following.md` | ja |
| Kommunikation | `okf/guides/communication.md` | ja |
| Coding Principles | `okf/guides/coding-principles.md` | ja |
| Context Reasoning | `okf/guides/context-reasoning.md` | ja |
| Quality Gates | `okf/guides/quality-gates.md` | Template (projekt-anpassbar) |
| Agent-Prinzipien | `okf/concepts/agent-principles.md` | via Skill |

Projekt-spezifische Regeln (z. B. Kassensystem-Views in event-pos-desktop) bleiben im jeweiligen Projekt.

## Setup

### APM installieren

```bash
curl -sSL https://aka.ms/apm-unix | sh
```

### In diesem Repo (Producer)

```bash
apm install
```

### In einem Consumer-Projekt

```yaml
# apm.yml
name: mein-projekt
version: 1.0.0
dependencies:
  apm:
    - BigAl42/development-harness#v0.1.0
```

```bash
apm install
```

## OKF pflegen

1. Regel in `okf/guides/` oder `okf/concepts/` bearbeiten
2. Entsprechende Datei unter `.apm/instructions/` synchron halten (siehe `okf/reference/apm-mapping.md`)
3. `okf/log.md` aktualisieren
4. `apm install` ausführen
5. Version in `apm.yml` bumpen und taggen (`v0.1.0`, …)

## Skills

- **okf-rules** — lädt und wendet das OKF-Bundle an; für Setup und Compliance-Checks

## Links

- [Microsoft APM](https://microsoft.github.io/apm/)
- [OKF vs Cursor Rules vs AGENTS.md](https://bundledex.net/guides/agents-md-vs-cursor-rules-vs-okf/)
