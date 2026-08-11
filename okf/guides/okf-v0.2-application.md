---
type: Playbook
title: Applying OKF v0.2
description: Rules for creating, maintaining, and consuming OKF v0.2–conformant knowledge bundles in this harness
tags: [okf, spec, authoring, conformance]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:15:00Z
sources:
  - id: okf-spec-v0.2
    resource: https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
    title: Open Knowledge Format v0.2 Specification
    author: team:gcp-knowledge-catalog
---

# Applying OKF v0.2

This bundle **targets OKF version 0.2**. Any agent authoring, migrating, or consuming rules must follow this playbook.

## Conformance (required)

A bundle is OKF v0.2 conformant when:

1. Every non-reserved `.md` file has parseable YAML frontmatter
2. Every frontmatter block has a **non-empty `type` field** — the only always-required field
3. Reserved filenames (`index.md`, `log.md`) follow the specification

Reserved filenames must **not** be used for concept documents.

## Bundle structure

```
okf/
├── index.md              # okf_version: "0.2"
├── log.md
├── harness-rules/        # Harness Rules (type: Harness Rule) — SOURCE OF TRUTH
├── concepts/             # Model, architecture
├── guides/               # Playbooks (OKF authoring, consume/maintain, layering)
└── reference/            # Deployment, templates, validators, extractions
```

Harness rules are **harness-agnostic**. `.cursor/rules/` and similar paths are generated deploy targets only — see [Harness Rules — Model](/concepts/harness-rules-model.md).

For **consumer** in-repo OKF (domain catalogs), see [OKF v0.2 In-Repo Layout](/reference/okf-v0.2-in-repo-layout.md) and [OKF Consume and Maintain](/guides/okf-consume-and-maintain.md).

## Frontmatter fields (v0.2)

| Field | Required | Usage |
|-------|----------|-------|
| `type` | **yes** | e.g. `Harness Rule`, `Playbook`, `Reference` |
| `title` | recommended | Display name |
| `description` | recommended | One sentence for index and search |
| `tags` | optional | Cross-cutting categories |
| `status` | optional | `draft` \| `stable` \| `deprecated` (default: stable) |
| `generated` | optional | `{ by: <actor>, at: <ISO-8601> }` |
| `verified` | optional | List of `{ by, at }` — trust signal |
| `sources` | optional | Provenance with `resource`, optional `id`, `author` |
| `stale_after` | optional | `YYYY-MM-DD` — absolute stale date |

Preserve unknown keys; do not discard them.

## Actor convention

- `human:<name>` — human authorized/confirmed
- `agent/<name>` or `tool/<name>` — agent/tool produced
- `process:<name>` — automated process

Derive trust tier from `verified`: unverified → machine-confirmed → human-reviewed.

## Cross-links

Use bundle-relative links: `[Title](/harness-rules/coding-principles.md)`.

## Authoring workflow (this repo)

1. Create or edit a **harness rule** in `okf/harness-rules/` (`type: Harness Rule`)
2. Validate frontmatter — at least `type`; set `generated` for agent-authored content
3. Update `okf/index.md` and `okf/log.md`
4. Mirror `.apm/instructions/` (`harnessRule` + `source` in frontmatter)
5. Run `apm install` — generates harness targets; **do not** edit `.cursor/rules/` manually

Write all bundle content in English — see [English Language](/harness-rules/english-language.md).

## Consumption workflow (agent)

1. Read bundle root `okf/index.md` → check `okf_version`
2. Load relevant concepts by `type`, `tags`, or index
3. Respect trust signals (`verified`, `stale_after`, `status`) before applying
4. On conflict: follow [Rules Precedence](/harness-rules/rules-precedence.md)

## What does not belong in OKF

- Harness-specific deploy paths (`.cursor/rules/`, `.agents/skills/`) — APM layer
- Project-specific commands (npm, cargo) — target project, not this cross-cutting bundle

## Spec reference

Full norm: [OKF v0.2 SPEC](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
