---
type: Playbook
title: OKF Update After Architecture Change
description: Post-change workflow to keep concepts, log, AGENTS, and rules aligned
tags: [okf, playbook, maintenance]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-updating-okf-knowledge
    resource: https://github.com/BigAl42/energy-tracker
    title: .cursor/skills/updating-okf-knowledge (generalized)
---

# OKF Update After Architecture Change

Run this in the **same** change as the code when architecture, schema, ACL, deploy, or similar behavior shifts.

## Checklist

1. **Concepts** — create/update/deprecate under the right domain; set `status` if needed
2. **`okf/log.md`** — dated bullet (see [OKF Changelog](/guides/okf-changelog-log.md))
3. **`okf/index.md` / domain indexes** — link new concepts
4. **`AGENTS.md` / project rules** — if must/never changed, update hard rules first, then OKF
5. **Validate** — run the project OKF validator before merge
6. **Precedence** — if OKF and hard rules disagree, hard rules win; fix OKF ([Rules Precedence](/harness-rules/rules-precedence.md))

## Skip when

Pure typos, formatting, or UI cosmetics with no behavioral or contractual change.

## Related

- [OKF Consume and Maintain](/guides/okf-consume-and-maintain.md)
- [OKF Bundle Checklist](/reference/validators/okf-bundle-checklist.md)
