---
type: Harness Rule
title: Session and Tenant Empty State
description: Never treat auth or load failures as an empty tenant or first-run create flow
tags: [harness-rules, auth, tenancy, ux, reliability]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-session-tenant
    resource: https://github.com/BigAl42/energy-tracker
    title: session-tenant-ui.mdc / AGENTS.md session-tenant must-never (generalized)
---

# Session and Tenant Empty State

Cross-project principle: do not confuse **auth failure**, **load error**, and **genuinely empty** tenant/resource scope.

## Terms

| Term | Meaning |
|------|---------|
| **Session** | Client auth state (token, session store, cookie) |
| **Tenant scope** | Primary multi-tenant resource (tenant, workspace, org, household, …) |
| **Empty** | Authenticated load succeeded; zero entities |
| **Error** | Auth invalid/expired, network failure, or API error |

## Rules

1. **Validate session on boot** before rendering an authenticated shell. Refresh or clear stale credentials; do not assume a stored token is valid.
2. **Separate error vs empty** in resource loaders. UI and state must distinguish “load failed” from “no tenants yet”.
3. **Never map failures to first-run create UX.** Auth or API failure must not open “create tenant / workspace” as the default recovery.
4. **Recovery before create.** Prefer re-auth, retry, or explicit error with retry — not silent redirect into create flows.
5. **No silent catch that clears entities.** Do not `catch` and set the list to `[]` without setting an error state. That fabricates “empty tenancy”.

## Boundary

Concrete session APIs and resource names belong in **project rules** or project OKF constraints. This harness rule states the principle only.

## Related

- [Rules Precedence](/harness-rules/rules-precedence.md)
- [Context Reasoning](/harness-rules/context-reasoning.md)
- [Quality Gates](/harness-rules/quality-gates.md)
