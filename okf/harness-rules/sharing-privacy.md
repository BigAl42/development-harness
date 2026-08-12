---
type: Harness Rule
title: Sharing Privacy
description: Membership-scoped sharing — invite by identifier, never list all accounts
tags: [harness-rules, privacy, acl, multi-tenant, household]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T05:45:00Z
sources:
  - id: kredit-tracker-household
    resource: /kredit-tracker/.cursor/rules/household.mdc
    title: Household ACL (generalized)
  - id: kredit-tracker-core
    resource: /kredit-tracker/.cursor/rules/credit-tracker-core.mdc
    title: Invite-only sharing
  - id: energy-tracker-household-membership
    resource: /energy-tracker/okf/acl/household-membership.md
    title: Household membership / invite by email
---

# Sharing Privacy

For apps that share data inside a **membership group** (household, workspace, team) rather than a global social graph.

## Sharing boundary

- ACL for domain data is **membership-scoped** (group + role), not a public user directory
- Partners/members see shared domain data per membership rules — do not invent per-row share tables without need

## Invites

- Add members by **explicit invite** (email or other opaque identifier the product already uses)
- **Never** list or search all accounts for a picker
- Keep pending invites distinct from active members; allow cancel where the product supports it

## Directory rules

User list/search endpoints stay self- or membership-constrained. Opening `users` for expand/display must not become a global directory.

## Boundary

Concrete collection names, invite APIs, and role matrices belong in project rules / OKF.
