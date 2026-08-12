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
| Targets | `.cursor/rules/`, `.agents/skills/`, `AGENTS.md` | no (generated) |

Details: [okf/concepts/harness-rules-model.md](okf/concepts/harness-rules-model.md)

## Harness rules (v0.4.2)

| Harness Rule | File | APM `applyTo` |
|--------------|------|---------------|
| Agent Principles | `okf/harness-rules/agent-principles.md` | (skill) |
| **English Language** | `okf/harness-rules/english-language.md` | `**` |
| Instruction Following | `okf/harness-rules/instruction-following.md` | `**` |
| Communication | `okf/harness-rules/communication.md` | `**` |
| Coding Principles | `okf/harness-rules/coding-principles.md` | `**` |
| Context Reasoning | `okf/harness-rules/context-reasoning.md` | `**` |
| Quality Gates (template) | `okf/harness-rules/quality-gates.md` | `**` |
| OKF Knowledge Workflow | `okf/harness-rules/okf-knowledge-workflow.md` | `okf/**` |
| Domain Logic First | `okf/harness-rules/domain-logic-first.md` | `**/lib/**`, scripts tests |
| Sharing Privacy | `okf/harness-rules/sharing-privacy.md` | acl / invite / membership |
| Web Push Privacy | `okf/harness-rules/web-push-privacy.md` | push / SW / notifications |
| Mobile Web Shell | `okf/harness-rules/mobile-web-shell.md` | tsx/jsx/css / shell / nav |

**Project rules** (domain modules, stack-specific paths, collection names) stay in the target repo and complement harness rules.

All documentation in this package is **English**.

## Setup

```bash
curl -sSL https://aka.ms/apm-unix | sh
apm install
apm compile --validate   # frontmatter + structure; no writes with --validate
```

Pinned harnesses for this package (see `targets:` in `apm.yml`): Cursor, Claude, Copilot, Codex, Gemini, OpenCode, Windsurf.

## Consumer project

```yaml
dependencies:
  apm:
    - BigAl42/development-harness#v0.4.2
```

```bash
apm install              # deploys harness rules to detected / declared targets
apm compile              # writes AGENTS.md / CLAUDE.md / GEMINI.md as needed
apm compile --validate   # CI-friendly check without writing
```

## Maintenance

1. Edit harness rule in `okf/harness-rules/` (`type: Harness Rule`)
2. Mirror `.apm/instructions/` — set a **narrow `applyTo`** for situational rules; keep `**` only for always-on principles
3. Run `apm compile --validate` (or `apm run validate`)
4. Run `apm install` — targets are regenerated

## Links

- [OKF v0.2 Spec](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
- [Microsoft APM](https://microsoft.github.io/apm/)
- [Harness Deployment](okf/reference/harness-deployment.md)
- [APM Instructions & agents](https://microsoft.github.io/apm/producer/author-primitives/instructions-and-agents/)
