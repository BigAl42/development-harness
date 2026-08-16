---
type: Reference
title: OKF → APM Mapping
description: Mapping from OKF harness rules to APM instructions (not to Cursor rules)
tags: [apm, reference, harness-rules]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-12T18:15:00Z
---

# OKF → APM Mapping

Harness rules live in `okf/harness-rules/`. APM instructions are the deployable derivation. Harness targets (`.cursor/rules/` etc.) are generated — see [Harness Deployment](/reference/harness-deployment.md).

| Harness Rule (OKF) | APM Instruction | harnessRule | applyTo |
|--------------------|-----------------|-------------|---------|
| `harness-rules/english-language.md` | `english-language.instructions.md` | english-language | `**` |
| `harness-rules/instruction-following.md` | `instruction-following.instructions.md` | instruction-following | `**` |
| `harness-rules/communication.md` | `communication.instructions.md` | communication | `**` |
| `harness-rules/coding-principles.md` | `coding-principles.instructions.md` | coding-principles | `**` |
| `harness-rules/context-reasoning.md` | `context-reasoning.instructions.md` | context-reasoning | `**` |
| `harness-rules/quality-gates.md` | `quality-gates.instructions.md` | quality-gates | `**` |
| `harness-rules/okf-knowledge-workflow.md` | `okf-knowledge-workflow.instructions.md` | okf-knowledge-workflow | `okf/**` |
| `harness-rules/domain-logic-first.md` | `domain-logic-first.instructions.md` | domain-logic-first | lib + test scripts |
| `harness-rules/sharing-privacy.md` | `sharing-privacy.instructions.md` | sharing-privacy | acl / invite / membership |
| `harness-rules/web-push-privacy.md` | `web-push-privacy.instructions.md` | web-push-privacy | push / SW / notifications |
| `harness-rules/mobile-web-shell.md` | `mobile-web-shell.instructions.md` | mobile-web-shell | tsx/jsx/css / shell / nav |
| `harness-rules/design-md.md` | `design-md.instructions.md` | design-md | DESIGN.md + UI/CSS |
| `harness-rules/agent-principles.md` | Skill `harness-rules` (reference) | agent-principles | — |
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | okf-v0.2-application | `okf/**`, `.apm/**`, `apm.yml` |
| `guides/consumer-integration.md` | `consumer-integration.instructions.md` | consumer-integration | `apm.yml`, lockfile, AGENTS, local rules |
| `guides/design-md-application.md` | `design-md-application.instructions.md` | design-md-application | DESIGN.md, apm.yml |

### Skills

| Skill | Path | Role |
|-------|------|------|
| `harness-rules` | `.apm/skills/harness-rules/` | Author/maintain this package |
| `integrating-development-harness` | `.apm/skills/integrating-development-harness/` | Wire this package into a consumer repo |
| `authoring-design-md` | `.apm/skills/authoring-design-md/` | Create/update consumer root DESIGN.md |
