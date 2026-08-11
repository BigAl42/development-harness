---
type: Reference
title: OKF v0.2 In-Repo Layout
description: Recommended folder layout for a project OKF knowledge bundle (domain catalog style)
tags: [okf, reference, layout]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-okf-layout
    resource: https://github.com/BigAl42/energy-tracker
    title: energy-tracker okf/ six-domain layout (generalized)
---

# OKF v0.2 In-Repo Layout

Layout for **project** knowledge bundles (not the harness package itself).

```
okf/
├── index.md                 # okf_version: "0.2" — domain catalog / router
├── log.md                   # dated agent changelog
├── <domain>/                # e.g. architecture, schema, acl, deploy
│   ├── index.md             # domain index
│   └── *.md                 # concepts (type required)
└── …
```

## Compared to this harness package

| Project OKF | development-harness |
|-------------|---------------------|
| Domain concepts (`Concept`, `Constraint`, …) | `harness-rules/`, `guides/`, `reference/` |
| Product architecture | Portable agent rules |
| Stays in the app repo | Distributed via APM |

## Types commonly used in projects

`Concept`, `Constraint`, `Playbook`, `Domain Boundary`, `Reference` — always with non-empty `type`.

## Related

- [Applying OKF v0.2](/guides/okf-v0.2-application.md)
- [OKF Baseline Capture](/guides/okf-baseline-capture.md)
- [OKF Bundle Checklist](/reference/validators/okf-bundle-checklist.md)
