---
type: Reference
title: "Template: Push opt-in playbook"
description: Project template for opt-in push notifications — no broadcast without consent
tags: [template, push, pwa, privacy]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-push-agents
    resource: https://github.com/BigAl42/energy-tracker
    title: AGENTS.md push must/never (template only)
---

# Template: Push opt-in playbook

Project-specific. Copy into project OKF or `AGENTS.md` and fill implementation details.

## Must

- Send push only to users/devices that **opted in**
- Persist subscription/consent with clear scope
- Provide a path to unsubscribe / disable

## Never

- Broadcast to all users without consent
- Re-enable push silently after user opt-out
- Treat missing permission as implied consent

## Project slots

- Permission / VAPID / service-worker paths: …
- Backend send job vs client: …
- Test devices / iOS PWA notes: …
