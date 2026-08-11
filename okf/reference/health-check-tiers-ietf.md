---
type: Reference
title: Health Check Tiers (IETF-style)
description: Separate liveness and readiness/health endpoints for deployable services
tags: [deploy, health, reference]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-health-endpoints
    resource: https://github.com/BigAl42/energy-tracker
    title: okf/deploy/health-endpoints.md (generalized)
---

# Health Check Tiers (IETF-style)

## Principle

Expose at least two tiers:

| Tier | Typical path | Meaning |
|------|--------------|---------|
| **Liveness** | `/livez` | Process is up; orchestrator should not kill solely for dependency issues |
| **Readiness / health** | `/health` or `/readyz` | Ready to serve traffic; may fail when critical dependencies are down |

Do not overload a single endpoint for both “is the process alive?” and “are dependencies OK?” unless the project documents that choice explicitly.

## Project work

- Document paths and failure semantics in project OKF or ops docs
- Prefer contract tests for status codes and payload shape
- Exact paths and payloads stay in the consumer repo
