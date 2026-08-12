---
type: Harness Rule
title: Web Push Privacy
description: No broadcast push; preference gates; purge gone endpoints; never commit VAPID secrets
tags: [harness-rules, push, pwa, privacy, secrets]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T05:45:00Z
sources:
  - id: energy-tracker-agents-push
    resource: /energy-tracker/AGENTS.md
    title: Push must/never (generalized)
---

# Web Push Privacy

Applies when the project sends Web Push (or similar) notifications.

## Targeting

- **Never** expose or use public broadcast-to-all-users push endpoints
- Send only to a specific user (or an explicit, audited recipient set)
- Require: notifications enabled ∧ relevant preference subtype ∧ ≥1 active subscription

## Preferences

Keep distinct notification categories as separate preferences (e.g. product announcements vs reminders). Do not collapse unrelated prefs into one toggle.

## Endpoint hygiene

Delete subscriptions that return gone/expired responses (typically HTTP 404/410).

## Account export / delete

If the product supports export or account deletion, include push subscriptions and notification preferences in those paths.

## Secrets

Never commit VAPID private keys, `.env` secrets, or equivalent credentials.

## Boundary

Concrete helpers (`sendPushToUser`, cron vs one-shot jobs, `WHATS_NEW` arrays) stay in project rules.
