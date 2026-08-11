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

## OKF v0.2

Das Bundle targetiert **[OKF Version 0.2](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)**. Die Anwendung der Spec ist als eigene Instruction deployt:

- OKF-Quelle: `okf/guides/okf-v0.2-application.md`
- APM: `.apm/instructions/okf-v0.2-application.instructions.md`
- Cursor: `.cursor/rules/okf-v0.2-application.mdc`

## Enthaltene OKF-Regeln (v0.1.0)

Extrahiert aus übergreifenden Cursor User Rules und generalisierten Mustern aus [event-pos-desktop](https://github.com/BigAl42/event-pos-desktop):

| Regel | Datei | type |
|-------|-------|------|
| **OKF v0.2 anwenden** | `okf/guides/okf-v0.2-application.md` | Playbook |
| Instruction Following | `okf/guides/instruction-following.md` | Agent Rule |
| Kommunikation | `okf/guides/communication.md` | Agent Rule |
| Coding Principles | `okf/guides/coding-principles.md` | Agent Rule |
| Context Reasoning | `okf/guides/context-reasoning.md` | Agent Rule |
| Quality Gates | `okf/guides/quality-gates.md` | Agent Rule |
| Agent-Prinzipien | `okf/concepts/agent-principles.md` | Playbook |

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

## OKF pflegen (v0.2)

1. [OKF v0.2 anwenden](okf/guides/okf-v0.2-application.md) beachten — `type`-Pflichtfeld, Trust-Signale
2. Regel in `okf/guides/` oder `okf/concepts/` bearbeiten
3. `okf/index.md` und `okf/log.md` aktualisieren
4. Entsprechende Datei unter `.apm/instructions/` synchron halten (siehe `okf/reference/apm-mapping.md`)
5. `apm install` ausführen
6. Version in `apm.yml` bumpen und taggen (`v0.1.0`, …)

## Skills

- **okf-rules** — lädt und wendet das OKF-Bundle an; für Setup und Compliance-Checks

## Links

- [Microsoft APM](https://microsoft.github.io/apm/)
- [OKF vs Cursor Rules vs AGENTS.md](https://bundledex.net/guides/agents-md-vs-cursor-rules-vs-okf/)
