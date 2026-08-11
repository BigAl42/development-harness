---
type: Playbook
title: OKF Baseline Capture
description: Bootstrap an in-repo OKF v0.2 layout, root index, and initial log
tags: [okf, playbook, bootstrap]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-capturing-okf-baseline
    resource: https://github.com/BigAl42/energy-tracker
    title: .cursor/skills/capturing-okf-baseline (generalized)
---

# OKF Baseline Capture

Bootstrap a **project** OKF bundle (domain knowledge), distinct from this harness package’s portable rules.

## Steps

1. Create `okf/index.md` with `okf_version: "0.2"` and a domain catalog
2. Create `okf/log.md` with an initial dated entry
3. Add domain folders (e.g. `architecture/`, `schema/`, …) each with a domain index
4. Capture first concepts with YAML frontmatter — at least `type`; prefer `title`, `description`, `sources`
5. Wire validation: script + `npm run test:okf` (or equivalent) — see [OKF Bundle Checklist](/reference/validators/okf-bundle-checklist.md)
6. Add thin always-on rule / skill pointers — templates under [reference/templates](/reference/templates/AGENTS-hard-rules.md)
7. Document must/never in `AGENTS.md` — OKF must not silently contradict them

## Layout reference

See [OKF v0.2 In-Repo Layout](/reference/okf-v0.2-in-repo-layout.md).

## Do not

- Put portable Harness Rules here — those live in `development-harness`
- Use reserved names (`index.md`, `log.md`) for concept documents
- Skip `type` on any concept file
