---
type: Reference
title: OKF → APM Mapping
description: Mapping from OKF harness rules to APM instructions (not to Cursor rules)
tags: [apm, reference, harness-rules]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# OKF → APM Mapping

Harness rules live in `okf/harness-rules/`. APM instructions are the deployable derivation. Harness targets (`.cursor/rules/` etc.) are generated — see [Harness Deployment](/reference/harness-deployment.md).

| Harness Rule (OKF) | APM Instruction | harnessRule |
|--------------------|-----------------|-------------|
| `harness-rules/english-language.md` | `english-language.instructions.md` | english-language |
| `harness-rules/instruction-following.md` | `instruction-following.instructions.md` | instruction-following |
| `harness-rules/communication.md` | `communication.instructions.md` | communication |
| `harness-rules/coding-principles.md` | `coding-principles.instructions.md` | coding-principles |
| `harness-rules/context-reasoning.md` | `context-reasoning.instructions.md` | context-reasoning |
| `harness-rules/quality-gates.md` | `quality-gates.instructions.md` | quality-gates |
| `harness-rules/okf-knowledge-workflow.md` | `okf-knowledge-workflow.instructions.md` | okf-knowledge-workflow |
| `harness-rules/domain-logic-first.md` | `domain-logic-first.instructions.md` | domain-logic-first |
| `harness-rules/sharing-privacy.md` | `sharing-privacy.instructions.md` | sharing-privacy |
| `harness-rules/web-push-privacy.md` | `web-push-privacy.instructions.md` | web-push-privacy |
| `harness-rules/mobile-web-shell.md` | `mobile-web-shell.instructions.md` | mobile-web-shell |
| `harness-rules/agent-principles.md` | Skill `harness-rules` (reference) | agent-principles |
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | okf-v0.2-application |
