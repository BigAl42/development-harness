---
type: Reference
title: Harness Deployment
description: Derivation chain from OKF harness rules to APM instructions and harness targets
tags: [harness-rules, apm, deployment]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# Harness Deployment

## Derivation chain

| Harness Rule (OKF) | APM Instruction | Cursor (generated) | Copilot (generated) |
|--------------------|-----------------|--------------------|---------------------|
| `harness-rules/english-language.md` | `english-language.instructions.md` | `.cursor/rules/english-language.mdc` | `.github/instructions/` |
| `harness-rules/instruction-following.md` | `instruction-following.instructions.md` | `.cursor/rules/instruction-following.mdc` | `.github/instructions/` |
| `harness-rules/communication.md` | `communication.instructions.md` | `.cursor/rules/communication.mdc` | … |
| `harness-rules/coding-principles.md` | `coding-principles.instructions.md` | `.cursor/rules/coding-principles.mdc` | … |
| `harness-rules/context-reasoning.md` | `context-reasoning.instructions.md` | `.cursor/rules/context-reasoning.mdc` | … |
| `harness-rules/quality-gates.md` | `quality-gates.instructions.md` | `.cursor/rules/quality-gates.mdc` | … |
| `harness-rules/okf-knowledge-workflow.md` | `okf-knowledge-workflow.instructions.md` | `.cursor/rules/okf-knowledge-workflow.mdc` | … |
| `harness-rules/domain-logic-first.md` | `domain-logic-first.instructions.md` | `.cursor/rules/domain-logic-first.mdc` | … |
| `harness-rules/sharing-privacy.md` | `sharing-privacy.instructions.md` | `.cursor/rules/sharing-privacy.mdc` | … |
| `harness-rules/web-push-privacy.md` | `web-push-privacy.instructions.md` | `.cursor/rules/web-push-privacy.mdc` | … |
| `harness-rules/mobile-web-shell.md` | `mobile-web-shell.instructions.md` | `.cursor/rules/mobile-web-shell.mdc` | … |
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | `.cursor/rules/okf-v0.2-application.mdc` | … |

## Producer repo (development-harness)

- **Commit:** `okf/harness-rules/`, `.apm/instructions/`, `apm.yml`, `apm.lock.yaml`
- **Do not commit:** `.cursor/rules/`, `.agents/skills/` (generated targets — see `.gitignore`)

## Consumer project

```yaml
# apm.yml
dependencies:
  apm:
    - BigAl42/development-harness#v0.4.0
```

```bash
apm install    # deploys harness rules to detected targets
```

Project-specific rules stay in the consumer repo and **complement** — not replace — harness rules.

## Change workflow

1. Edit harness rule in `okf/harness-rules/`
2. Mirror `.apm/instructions/` (keep `harnessRule` reference)
3. Run `apm install` in producer or consumer
4. Generated targets are recreated — do not edit manually
