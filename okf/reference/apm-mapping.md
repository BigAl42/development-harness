---
type: Reference
title: OKF → APM Mapping
description: Mapping von OKF Harness Rules zu APM Instructions (nicht zu Cursor Rules)
tags: [apm, reference, harness-rules]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# OKF → APM Mapping

Harness Rules leben in `okf/harness-rules/`. APM Instructions sind die deploybare Ableitung. Harness-Targets (`.cursor/rules/` etc.) werden generiert — siehe [Harness Deployment](/reference/harness-deployment.md).

| Harness Rule (OKF) | APM Instruction | harnessRule |
|--------------------|-----------------|-------------|
| `harness-rules/instruction-following.md` | `instruction-following.instructions.md` | instruction-following |
| `harness-rules/communication.md` | `communication.instructions.md` | communication |
| `harness-rules/coding-principles.md` | `coding-principles.instructions.md` | coding-principles |
| `harness-rules/context-reasoning.md` | `context-reasoning.instructions.md` | context-reasoning |
| `harness-rules/quality-gates.md` | `quality-gates.instructions.md` | quality-gates |
| `harness-rules/agent-principles.md` | Skill `harness-rules` (Referenz) | agent-principles |
| `guides/okf-v0.2-application.md` | `okf-v0.2-application.instructions.md` | okf-v0.2-application |
