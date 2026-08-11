---
type: Reference
title: Pre-Deploy Data Snapshot
description: Take a local (and optionally offsite) data snapshot before risky deploys
tags: [deploy, backup, reference]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-backup-restore
    resource: https://github.com/BigAl42/energy-tracker
    title: okf/deploy/backup-restore.md phase 1 (generalized)
---

# Pre-Deploy Data Snapshot

## Principle

Before a deploy that can mutate schema or production data:

1. **Local snapshot** of the authoritative data store (DB dump, volume snapshot, or project backup script)
2. **Verify** the snapshot is readable / restorable at a smoke level when practical
3. **Optional offsite copy** when the project’s RPO requires it
4. Only then run the deploy

## Boundary

Concrete backup commands, retention, and restore runbooks belong in the **project**. This reference states the gate only.

## Related

- [Quality Gates](/harness-rules/quality-gates.md) — project may list snapshot as a pre-deploy gate
