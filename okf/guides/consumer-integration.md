---
type: Playbook
title: Consumer Integration
description: How a consumer repo adds BigAl42/development-harness via APM and dedupes local rules
tags: [apm, consumer, integration, playbook, harness-rules]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-16T06:20:00Z
---

# Consumer Integration

Playbook for **consumer** repositories (e.g. trackers) that depend on `BigAl42/development-harness`. For authoring harness rules in this package, see [Applying OKF v0.2](/guides/okf-v0.2-application.md).

## Goal

- Install portable harness rules via APM
- Keep **only** project-specific hard rules in the consumer repo
- Do not duplicate harness principles as hand-maintained Cursor rules

## Prerequisites

```bash
curl -sSL https://aka.ms/apm-unix | sh   # if APM CLI missing
```

Pin a released tag (never `main` for consumers):

```text
BigAl42/development-harness#v0.5.0
```

## Minimal `apm.yml` (Cursor-only)

Start with Cursor only; add other targets later if needed.

```yaml
name: <repo-name>
version: 0.0.0
targets:
  - cursor
dependencies:
  apm:
    - BigAl42/development-harness#v0.5.0
  mcp: []
```

## Install and validate

```bash
apm install
apm compile --validate
apm compile
```

## What to commit

| Path | Commit? |
|------|---------|
| `apm.yml` | yes |
| `apm.lock.yaml` | yes |
| Project rules (`AGENTS.md`, domain `.cursor/rules/*.mdc` you author) | yes |
| Generated harness deploy output (from this package) | no — do not hand-edit; regenerate with `apm install` |

Project rules **complement** harness rules. They do not replace them.

## Conflict priority

1. Explicit user instruction in the current message  
2. Project rules / `AGENTS.md` in the consumer repo  
3. Harness rules (this package)  
4. General best practices  

If a local hard rule conflicts with harness knowledge (OKF), **local wins** — fix OKF/knowledge in the same change when the consumer has `okf/`.

## Dedup checklist

After install, compare local `.cursor/rules/` and `AGENTS.md` to harness rules.

**Remove or shorten** local text that only repeats:

- English language / coding principles / communication / instruction-following  
- Quality-gates **principle** (keep concrete project commands locally)  
- OKF consume/maintain workflow (when `okf/` exists)  
- Sharing privacy (membership invite-only; no global user directory)  
- Web push privacy (no broadcast; prefs; gone endpoints; no secrets)  
- Mobile web shell (portals; safe areas; ≥16px inputs; ~44px targets)  
- Domain-logic-first (pure calc; metrics before UI)

**Keep** locally:

- Stack hard rules (framework docs, “not X”, self-hosted backend specifics)  
- Concrete paths, collections, scripts, CTAs  
- Concrete quality-gate **commands** (`npm test`, `npx tsc --noEmit`, `npm run test:okf`, …)  
- Domain module boundaries with real file globs  
- Product priority and deploy/git conventions for this repo  

## OKF in the consumer

- If the repo has `okf/`: follow [OKF Knowledge Workflow](/harness-rules/okf-knowledge-workflow.md)  
- If it does **not**: do not create a full OKF baseline unless the user asks; harness OKF rules simply do not apply  

## Finish

- Feature branch + PR: harness dep added, local rules deduped, what stayed project-local  
- Do not invent product features as part of integration  
- New harness-facing docs and commits in **English**

## Related

- Skill: `integrating-development-harness` (agent workflow)  
- [Harness Deployment](/reference/harness-deployment.md)  
- [Harness Rules — Model](/concepts/harness-rules-model.md)
