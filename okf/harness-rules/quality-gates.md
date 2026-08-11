---
type: Harness Rule
title: Quality Gates Before Commit
description: Tests, builds, and optional knowledge-bundle checks before commit — template for consumers
tags: [harness-rules, testing, ci, commit, okf]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T08:09:00Z"
sources:
  - id: event-pos-tests-vor-commit
    resource: /event-pos-desktop/.cursor/rules/tests-vor-commit.mdc
    title: tests-vor-commit (generalized)
  - id: energy-tracker-quality
    resource: https://github.com/BigAl42/energy-tracker
    title: CI lint/test/build + optional test:okf (generalized)
---

# Quality Gates Before Commit

**Concrete commands** belong in project rules (`AGENTS.md`, `.mdc`) of the target repo — not in this harness rule body.

## Tests

All relevant tests must pass before commit. New or changed behavior should have matching coverage when the project expects it.

## Build

Verify production/release build when changes affect the build. Multi-stack projects may require more than one build step (e.g. frontend + native).

## Knowledge bundle (optional)

If the project has an in-repo OKF (or similar) validator, run it when concepts or architecture docs changed — see [OKF Bundle Checklist](/reference/validators/okf-bundle-checklist.md).

## Hooks and CI

- Respect pre-commit hooks when present.
- **Project choice:** always-on commit rule (event-pos style) **or** CI-on-PR discipline (energy-tracker style). Document which one applies in the project.

## Boundary

This harness rule defines the **principle**. Project rules fill lint/test/build/OKF commands.

## Related

- [Session and Tenant Empty State](/harness-rules/session-tenant-empty-state.md) — do not ship silent empty-state bugs without tests when touching auth/tenancy
- [Rule Layering](/guides/rule-layering.md)
