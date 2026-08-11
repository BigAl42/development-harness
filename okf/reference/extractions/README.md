---
type: Reference
title: Extractions project learnings
description: Index of rule/OKF extractions from consumer projects for harness integration
tags: [extraction, reference]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
---

# Extractions

Structured handoffs from consumer repos (private or public). Agents in other workspaces write here when multi-repo access is unavailable.

| Extraction | Repo | Status |
|------------|------|--------|
| [energy-tracker](energy-tracker.md) | BigAl42/energy-tracker | reviewed |

## How to add

1. Follow the extraction schema (inventory → classification A–E → proposed artifacts)
2. Store as `okf/reference/extractions/<repo-kurzname>.md` with `type: Reference`
3. Open a harness PR; implement Category A/B in the same or follow-up PR
4. Mark `status: reviewed` when integrated
