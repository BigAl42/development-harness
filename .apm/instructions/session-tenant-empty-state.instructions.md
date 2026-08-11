---
applyTo: "**"
description: "Harness Rule: Never treat auth/load failure as empty tenant or first-run create UX"
harnessRule: session-tenant-empty-state
source: okf/harness-rules/session-tenant-empty-state.md
---

# Harness Rule: Session and Tenant Empty State

Validate session on boot. Separate load **error** vs **empty** tenant scope. Never map auth/API failure to first-run create UX. Never silently clear entity lists in `catch` without error state.

Source: `okf/harness-rules/session-tenant-empty-state.md`
