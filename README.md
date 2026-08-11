# development-harness

Portable **Harness Rules** as an OKF v0.2 bundle + Microsoft APM package. Rules apply across all agent harnesses — they are **not** Cursor rules; they are **derived** into Cursor, Copilot, Claude Code, and others.

## Three layers

```
okf/harness-rules/     ← definition (Harness Rule, harness-agnostic)
       ↓
.apm/instructions/     ← APM deploy primitives
       ↓
.cursor/rules/ etc.     ← generated targets (not source of truth)
```

| Layer | What | Commit? |
|-------|------|---------|
| Harness rules | `okf/harness-rules/*.md` | yes |
| APM | `.apm/instructions/` | yes |
| Targets | `.cursor/rules/`, `.agents/skills/` | no (generated) |

Details: [okf/concepts/harness-rules-model.md](okf/concepts/harness-rules-model.md)

## Harness rules (v0.4.0)

| Harness Rule | File |
|--------------|------|
| Agent Principles | `okf/harness-rules/agent-principles.md` |
| **English Language** | `okf/harness-rules/english-language.md` |
| Instruction Following | `okf/harness-rules/instruction-following.md` |
| **Rules Precedence** | `okf/harness-rules/rules-precedence.md` |
| Communication | `okf/harness-rules/communication.md` |
| Coding Principles | `okf/harness-rules/coding-principles.md` |
| Context Reasoning | `okf/harness-rules/context-reasoning.md` |
| **Session / Tenant Empty State** | `okf/harness-rules/session-tenant-empty-state.md` |
| Quality Gates (template) | `okf/harness-rules/quality-gates.md` |

**Project rules** (e.g. POS views, energy-tracker AGENTS/OKF) stay in the target repo and complement harness rules. See [Rule Layering](okf/guides/rule-layering.md).

Consumer learnings: [okf/reference/extractions/](okf/reference/extractions/README.md).

All documentation in this package is **English**.

## Setup

```bash
curl -sSL https://aka.ms/apm-unix | sh
apm install
```

## Consumer project

```yaml
dependencies:
  apm:
    - BigAl42/development-harness#v0.4.0
```

```bash
apm install   # deploys harness rules to detected targets
```

## Maintenance

1. Edit harness rule in `okf/harness-rules/` (`type: Harness Rule`)
2. Mirror `.apm/instructions/`
3. Run `apm install` — targets are regenerated

## Links

- [OKF v0.2 Spec](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
- [Microsoft APM](https://microsoft.github.io/apm/)
- [Harness Deployment](okf/reference/harness-deployment.md)
