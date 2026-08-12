---
type: Reference
title: Harness Deployment
description: Derivation chain from OKF harness rules to APM instructions and harness targets
tags: [harness-rules, apm, deployment]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-12T18:15:00Z
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

## `applyTo` scoping (Minimal Context)

APM loads instructions by glob. Prefer **narrow** globs for situational rules so agents only see them when editing matching files.

| Kind | Example `applyTo` | Rules |
|------|-------------------|-------|
| Always-on | `**` | English, coding principles, quality-gates template, … |
| OKF / APM authoring | `okf/**`, `.apm/**` | OKF workflow, OKF v0.2 application |
| Domain calc | `**/lib/**`, `**/scripts/test-*` | Domain logic first |
| Sharing / ACL | `**/acl/**`, `**/invite*`, `**/member*`, `**/workspace*` | Sharing privacy |
| Push / PWA | `**/push*`, `**/service-worker*`, `**/notification*` | Web push privacy |
| Mobile UI | `**/*.{tsx,jsx,css}`, `**/shell*`, `**/nav*` | Mobile web shell |

Missing `applyTo` folds the instruction into compiled root context (`AGENTS.md`, …) instead of a path-scoped rule file. See [APM instructions docs](https://microsoft.github.io/apm/producer/author-primitives/instructions-and-agents/).

## Producer repo (development-harness)

- **Commit:** `okf/harness-rules/`, `.apm/instructions/`, `apm.yml`, `apm.lock.yaml`
- **Do not commit:** `.cursor/rules/`, `.agents/skills/`, generated `AGENTS.md` / `CLAUDE.md` / `GEMINI.md` (see `.gitignore`)
- **`targets:`** in `apm.yml` pins compile/install harnesses (avoid machine-dependent auto-detect)

## Consumer project

```yaml
# apm.yml
dependencies:
  apm:
    - BigAl42/development-harness#v0.4.2
```

```bash
apm install                 # deploys primitives to declared/detected targets
apm compile                 # writes root context files for non-Copilot harnesses
apm compile --validate      # CI: frontmatter + structure, no writes
```

Project-specific rules stay in the consumer repo and **complement** — not replace — harness rules.

## Change workflow

1. Edit harness rule in `okf/harness-rules/`
2. Mirror `.apm/instructions/` (keep `harnessRule` + `source`; set `applyTo`)
3. Run `apm compile --validate` (or `apm run validate`)
4. Run `apm install` in producer or consumer
5. Generated targets are recreated — do not edit manually
