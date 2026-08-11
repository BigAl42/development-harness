---
type: Reference
title: OKF Bundle Checklist
description: Language-agnostic validation checklist for in-repo OKF v0.2 bundles
tags: [okf, reference, validation]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-test-okf-bundle
    resource: https://github.com/BigAl42/energy-tracker
    title: scripts/test-okf-bundle.ts behavior (checklist only)
---

# OKF Bundle Checklist

Implement as a project script (e.g. `npm run test:okf`). This reference lists **what** to check, not a language-specific harness.

## Required checks

1. `okf/index.md` exists and declares `okf_version: "0.2"` (or supported version)
2. `okf/log.md` exists
3. Every non-reserved `.md` under `okf/` has parseable YAML frontmatter
4. Every frontmatter has a **non-empty `type`**
5. Reserved names `index.md` / `log.md` are not used as concept documents outside their roles
6. Links in indexes resolve to existing files (optional but recommended)
7. Unknown frontmatter keys are preserved (do not strip)

## Recommended checks

- `status` values in `{draft, stable, deprecated}` when present
- `sources` present on concepts that claim provenance
- Domain folders each have an index when the project uses domain catalogs

## Quality gates

Wire the validator into the project test command and optionally into CI. See [Quality Gates](/harness-rules/quality-gates.md) — knowledge-bundle slot.
