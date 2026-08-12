---
applyTo: "**"
description: "Harness Rule: Pure domain calc without I/O; test metrics before UI; keep parallel modules decoupled"
harnessRule: domain-logic-first
source: okf/harness-rules/domain-logic-first.md
---

# Harness Rule: Domain Logic First

Domain math in libs without DB/network. New metrics: calc + tests before UI. Parallel domains: no cross-imports in core libs except deliberate bridges; “apply” bridges must write state.

Source: `okf/harness-rules/domain-logic-first.md`
