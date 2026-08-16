---
type: Harness Rule
title: DESIGN.md Visual Identity
description: Use Google Labs DESIGN.md as the visual source of truth for UI work in consumer repos
tags: [harness-rules, design, ui, design-md, frontend]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-16T07:55:00Z
sources:
  - id: google-labs-design-md
    resource: https://github.com/google-labs-code/design.md
    title: DESIGN.md format specification (Google Labs)
  - id: google-labs-design-md-spec
    resource: https://github.com/google-labs-code/design.md/blob/main/docs/spec.md
    title: DESIGN.md Format Spec
---

# DESIGN.md Visual Identity

Consumer UI repos use a root **`DESIGN.md`** per the [Google Labs DESIGN.md](https://github.com/google-labs-code/design.md) format: YAML design tokens + markdown rationale.

## When

Applies when the agent creates or changes **user-facing UI** (layout, color, typography, components, spacing, visual polish).

## Must

1. **Before** substantive UI work: read the consumer repo’s `DESIGN.md` (repo root by default)
2. Treat **YAML tokens as normative**; prose explains *why* and how to apply them
3. If `DESIGN.md` is missing and the product has (or is getting) a visual UI: **create** it in the same change using skill `authoring-design-md` / playbook [Applying DESIGN.md](/guides/design-md-application.md)
4. After intentional visual changes: **update** `DESIGN.md` tokens and matching prose in the same PR
5. Prefer `npx @google/design.md lint DESIGN.md` (or `npx -p @google/design.md designmd lint DESIGN.md`) when the package is available

## Never

- Invent a parallel one-off palette/typography in code that contradicts `DESIGN.md`
- Hand-wave “make it pretty” without tokens when a DESIGN.md exists
- Put product-specific colors/fonts into the **harness package** — those belong in the consumer `DESIGN.md`

## Boundary

- Harness defines **format + workflow**
- Consumer `DESIGN.md` defines **this product’s** visual identity
- Stack wiring (CSS variables, Tailwind theme export) stays in the consumer project

## Related

- [Applying DESIGN.md](/guides/design-md-application.md)
- Skill `authoring-design-md`
