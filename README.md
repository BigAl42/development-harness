# development-harness

Portable **Harness Rules** als OKF-v0.2-Bundle + Microsoft APM-Package. Regeln gelten übergreifend für alle Agent-Harnesses — sie sind **nicht** Cursor-Rules, sondern werden daraus (und in Copilot, Claude Code, …) **abgeleitet**.

## Drei Ebenen

```
okf/harness-rules/     ← Definition (Harness Rule, harness-agnostisch)
       ↓
.apm/instructions/     ← APM deploy-Primitive
       ↓
.cursor/rules/ etc.     ← generierte Targets (nicht Source of Truth)
```

| Ebene | Was | Committen? |
|-------|-----|------------|
| Harness Rules | `okf/harness-rules/*.md` | ja |
| APM | `.apm/instructions/` | ja |
| Targets | `.cursor/rules/`, `.agents/skills/` | nein (generiert) |

Details: [okf/concepts/harness-rules-model.md](okf/concepts/harness-rules-model.md)

## Harness Rules (v0.2.0)

| Harness Rule | Datei |
|--------------|-------|
| Agent-Grundprinzipien | `okf/harness-rules/agent-principles.md` |
| Instruction Following | `okf/harness-rules/instruction-following.md` |
| Kommunikation | `okf/harness-rules/communication.md` |
| Coding Principles | `okf/harness-rules/coding-principles.md` |
| Context Reasoning | `okf/harness-rules/context-reasoning.md` |
| Quality Gates (Template) | `okf/harness-rules/quality-gates.md` |

**Projekt-Regeln** (z. B. Kassensystem-Views in event-pos-desktop) bleiben im Ziel-Repo und ergänzen die Harness Rules.

## Setup

```bash
curl -sSL https://aka.ms/apm-unix | sh
apm install
```

## Consumer-Projekt

```yaml
dependencies:
  apm:
    - BigAl42/development-harness#v0.2.0
```

```bash
apm install   # deployt Harness Rules in erkannte Targets
```

## Pflegen

1. Harness Rule in `okf/harness-rules/` bearbeiten (`type: Harness Rule`)
2. `.apm/instructions/` spiegeln
3. `apm install` — Targets werden neu generiert

## Links

- [OKF v0.2 Spec](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
- [Microsoft APM](https://microsoft.github.io/apm/)
- [Harness Deployment](okf/reference/harness-deployment.md)
