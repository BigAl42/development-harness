---
type: Harness Rule
title: Sharing Privacy
description: Membership-scoped sharing — invite by identifier, never list all accounts
tags: [harness-rules, privacy, acl, multi-tenant, sharing]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T18:30:00Z
sources:
  - id: kredit-tracker-membership-acl
    resource: kredit-tracker membership ACL project rule
    title: Membership ACL (generalized from project rule)
  - id: kredit-tracker-core-invites
    resource: kredit-tracker core always-on project rule
    title: Invite-only sharing (generalized)
  - id: energy-tracker-membership
    resource: energy-tracker ACL membership concept
    title: Membership / invite-by-identifier (generalized)
---

# Sharing Privacy

For apps that share data inside a **membership group** (workspace, team, org unit, or similar) rather than a global social graph.

## Sharing boundary

- ACL for domain data is **membership-scoped** (group + role), not a public user directory
- Members see shared domain data per membership rules — do not invent per-row share tables without need

## Invites

- Add members by **explicit invite** (email or other opaque identifier the product already uses)
- **Never** list or search all accounts for a picker
- Keep pending invites distinct from active members; allow cancel where the product supports it

## Directory rules

User list/search endpoints stay self- or membership-constrained. Opening `users` for expand/display must not become a global directory.

## Boundary

Concrete group names, invite APIs, and role matrices belong in project rules / OKF.
