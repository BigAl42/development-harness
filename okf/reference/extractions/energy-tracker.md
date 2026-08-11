---
type: Reference
title: "Extraction: energy-tracker"
description: "Agent-extracted rules and OKF learnings from BigAl42/energy-tracker for harness integration"
tags: [extraction, harness-rules, energy-tracker]
status: reviewed
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T09:55:00Z"
verified:
  - by: agent/cursor-cloud
    at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-rules
    resource: https://github.com/BigAl42/energy-tracker
    title: "energy-tracker cursor rules, AGENTS.md, okf/, skills, CI"
---

# Extraction: energy-tracker

Private PWA (**Vite + React + TypeScript + PocketBase**) for household meter readings, forecasts, push notifications, and VPS deploy. This document inventories agent-facing rules and OKF patterns on **`origin/main`** (as of 2026-08-10) for porting into **`BigAl42/development-harness`** (OKF v0.2 / harness v0.4.0).

Compared reference: **`BigAl42/event-pos-desktop`** (public) — 5 `.cursor/rules`, living doc `APP_OVERVIEW.md`, no `okf/` bundle, no `AGENTS.md`.

---

## 1. Inventory

### 1.1 `.cursor/rules/*.mdc`

| File | `description` | `alwaysApply` | Topics |
|------|---------------|---------------|--------|
| `okf.mdc` | Always-on OKF consume/maintain rules for architecture and schema work | **true** | Read `okf/index.md` → domain index → concepts before arch/schema/ACL/deploy/push work; update concepts + `okf/log.md`; run OKF validation; hard rules in `AGENTS.md` / `.cursor/rules` win; links session-tenant rule; three OKF skills; skip pure typos/UI cosmetics |
| `session-tenant-ui.mdc` | Auth session + household load — never fake empty tenancy | **true** | Boot `authRefresh` / clear stale JWT; separate load **error** vs empty tenant list; no silent `catch { setHouseholds([]) }`; recovery = re-login not “create tenant”; incident-driven |

**Rule composition:** Generic OKF workflow (`okf.mdc`) + cross-cutting incident rule (`session-tenant-ui.mdc`). Domain hard rules live in **`AGENTS.md`**, not split into many `.mdc` files (contrast event-pos: generic view rule + specific slave drilldown rule).

### 1.2 `okf/` bundle

| Item | Detail |
|------|--------|
| **Version / style** | OKF v0.2 in-repo bundle (not Google OKF Harness CLI wiki layout) |
| **Root** | `okf/index.md` (domain catalog), `okf/log.md` (dated changelog) |
| **Domains (6)** | `architecture/`, `schema/`, `acl/`, `deploy/`, `push-pwa/`, `forecast/` |
| **Concept count** | ~38 concept files + 6 domain indexes + root (40 markdown files under `okf/`) |
| **Frontmatter** | `type` + `sources[]` required on concepts; types used: `Concept`, `Constraint`, `Playbook`, `Domain Boundary` |
| **Language** | English in OKF; German product UI copy stays in app |
| **Validator** | `scripts/test-okf-bundle.ts` via `npm run test:okf` |

Notable concepts (harness-relevant patterns):

- `architecture/session-tenant-load.md` — Constraint mirroring `session-tenant-ui.mdc`
- `architecture/stack-boundaries.md`, `client-vs-jobs.md` — browser vs Node job split
- `deploy/health-endpoints.md` — IETF health-check tiers (`/livez` vs `/health`)
- `deploy/backup-restore.md` — pre-deploy local snapshot + optional offsite prep
- `schema/migration-conventions.md` — ordered PocketBase migrations + OKF in same PR
- `push-pwa/push-playbook.md` — opt-in push, no broadcast

### 1.3 Harness dependency

| Artifact | Present |
|----------|---------|
| `apm.yml` | **No** |
| `.apm/instructions/` | **No** |
| `development-harness` package/submodule | **No** |

Agent knowledge is **self-contained** in-repo (`okf/` + `.cursor/rules` + `.cursor/skills` + `AGENTS.md`).

### 1.4 Living docs

| Doc | Present | Role |
|-----|---------|------|
| `APP_OVERVIEW.md` | **No** | — |
| `ARCHITECTURE.md` | **No** | — |
| `AGENTS.md` | **Yes** | Hard must/never; wins over OKF |
| `README.md` | **Yes** | Human onboarding: stack, deploy, scripts, iOS/PWA notes |
| `okf/log.md` | **Yes** | Agent-oriented dated change log (closest to living overview delta) |
| `okf/index.md` | **Yes** | Domain router for agents |

**Pattern:** Replace single `APP_OVERVIEW.md` with **structured OKF domains + `log.md`**, plus **`AGENTS.md` for non-negotiables**.

### 1.5 `.cursor/skills/` (agent skills, not rules)

| Skill | Purpose |
|-------|---------|
| `capturing-okf-baseline` | Bootstrap `okf/` layout, frontmatter, root index, initial log |
| `updating-okf-knowledge` | Post-change workflow: concepts + log + align AGENTS/rules |
| `validating-okf-bundle` | Run `npm run test:okf` before merge |

### 1.6 CI / quality

| Mechanism | Detail |
|-----------|--------|
| `.husky/` | **No** |
| `.github/workflows/ci.yml` | `npm ci` → `lint` → `test` → `build` on PR + push to `main` |
| `.github/workflows/deploy.yml` | Separate deploy pipeline (GHCR images, SSH VPS); not a harness concern |
| **Lint** | `oxlint` (`npm run lint`) |
| **Tests** | Large `npm test` chain: OKF bundle + ~20 domain `tsx`/`bash` scripts (forecast, crop, backup contract, health contract, …) |
| **Build** | `tsc -b && vite build` |

**Project implementation (do not put in Harness Rule body):** `npm run test:okf`, full `npm test`, `npm run lint`, `npm run build`.

### 1.7 Cloud / IDE injection

`AGENTS.md` content is also injected as **cloud agent hard rules** (Cursor Cloud). Same precedence as local agents.

---

## 2. Classification by source

Legend: **A** Harness Rule · **B** Playbook/Reference · **C** Project Rule · **D** Already in harness · **E** Do not extract

| Source | Category | Rationale / harness target |
|--------|----------|----------------------------|
| `AGENTS.md` (stack section) | **C** | PocketBase, Vite PWA, push scripts — project-specific |
| `AGENTS.md` (OKF read/update + test:okf) | **B** | → `okf/guides/okf-consume-and-maintain.md` (template); overlaps harness OKF authoring |
| `AGENTS.md` (push must/never) | **C** | → template `okf/reference/templates/push-opt-in-playbook.md` |
| `AGENTS.md` (WHATS_NEW entry) | **C** | Product changelog pattern |
| `AGENTS.md` (session/tenant must/never) | **A** | → `okf/harness-rules/session-tenant-empty-state.md` (generalize beyond “household”) |
| `AGENTS.md` (iOS/PWA push testing) | **C** | Mobile PWA quirk doc |
| `.cursor/rules/okf.mdc` | **B** | → `okf/guides/okf-consume-and-maintain.md`; link from harness agent bootstrap |
| `.cursor/rules/session-tenant-ui.mdc` | **A** | → `okf/harness-rules/session-tenant-empty-state.md` (duplicate of AGENTS slice — merge one rule) |
| `okf/architecture/session-tenant-load.md` | **C** | Project Constraint; cite harness rule + keep as example in this extraction |
| `okf/index.md`, domain indexes | **B** | → `okf/reference/okf-v0.2-in-repo-layout.md` |
| `okf/log.md` workflow | **B** | → `okf/guides/okf-changelog-log.md` |
| `scripts/test-okf-bundle.ts` | **B** | → `okf/reference/validators/okf-bundle-checklist.md` (language-agnostic checklist; TS impl stays in project) |
| Skills: capturing / updating / validating OKF | **B** | → `okf/guides/` (may merge into existing harness OKF docs) |
| `okf/deploy/health-endpoints.md` | **B** | → `okf/reference/health-check-tiers-ietf.md` |
| `okf/deploy/backup-restore.md` | **B** | → `okf/reference/pre-deploy-data-snapshot.md` |
| `okf/schema/migration-conventions.md` | **C** | PocketBase-specific; keep as project playbook template |
| All other `okf/{schema,acl,forecast,push-pwa,architecture}/*` | **E** | Domain knowledge — stay in energy-tracker |
| `README.md` deploy/architecture tables | **C** | Ops doc for this VPS |
| CI `ci.yml` | **D** | Subsumed by harness **quality-gates** template — project fills commands |
| event-pos-style `tests-vor-commit.mdc` | **D** | energy-tracker relies on CI + agent discipline, not a dedicated always-on commit rule file |
| User rules (communication, coding-principles, …) | **D** | User-level; not repo rules |

---

## 3. Delta analysis

### 3.1 energy-tracker has; event-pos does **not**

| Capability | energy-tracker | event-pos-desktop |
|------------|----------------|-------------------|
| In-repo **OKF bundle** (`okf/` + validator) | Yes (6 domains, 40 files) | No |
| **`AGENTS.md`** hard rules layer | Yes | No (rules only in `.mdc`) |
| **Agent skills** for OKF lifecycle | 3 skills | No |
| **`okf/log.md`** agent changelog | Yes | No (uses `APP_OVERVIEW.md` instead) |
| **Session/tenant empty-state** rule | Yes (incident-hardened) | No |
| **Split CI vs deploy** workflows | Yes | (not compared in depth) |
| **IETF health endpoints** doc + contract test | Yes | No |
| **Pre-deploy backup** hook pattern | Yes | No |
| **PWA / push / PocketBase** domain docs | Yes | N/A (Tauri desktop) |

### 3.2 event-pos has; energy-tracker does **not**

| Capability | event-pos-desktop | energy-tracker |
|------------|-------------------|----------------|
| **`APP_OVERVIEW.md`** single living overview | Yes, alwaysApply rule | No — replaced by OKF + log |
| **5 granular `.mdc` rules** (generic + specific stack) | Yes | Only 2 rules; specifics in AGENTS/OKF |
| **`tests-vor-commit.mdc`** (test + full Tauri build before commit) | Yes | No dedicated rule; CI runs on push/PR |
| **Tauri/Rust dual stack quality gate** | Yes | N/A |
| **View read-only vs mutation** generic rule | Yes | Partially similar patterns in ACL/UI OKF only |
| **Vite handbook/bundle `.mdc`** | Yes | No equivalent rule file |

### 3.3 Gaps: harness vs energy-tracker rules

| Gap | Suggested harness addition |
|-----|----------------------------|
| Stale auth / empty resource list confused with “no data” | **New Harness Rule:** `session-tenant-empty-state.md` |
| Rules precedence (`AGENTS.md` > `.cursor/rules` > OKF) | **New Harness Rule:** `rules-precedence.md` |
| In-repo OKF consume/maintain alwaysApply snippet | **Guide:** `okf-consume-and-maintain.md` + thin `.mdc` template |
| OKF bundle validation in CI | Extend **quality-gates** template with optional knowledge-bundle slot |
| OKF baseline / update / validate skills | **Guides** mirroring the three `.cursor/skills` |
| Living doc without `APP_OVERVIEW` | **Guide:** `okf-changelog-log.md` + **rule-layering** patterns |
| Health check tiers | **Reference:** `health-check-tiers-ietf.md` |
| Pre-deploy data snapshot | **Reference:** `pre-deploy-data-snapshot.md` |
| Commit-time build gate (event-pos style) | Already **quality-gates** — document as project choice: CI-only vs alwaysApply commit rule |

---

## 4. Proposed harness artifacts (action list)

### 4.1 New Harness Rules (`okf/harness-rules/`)

#### `session-tenant-empty-state.md`

Cross-project principle from incident (2026-08-08):

- Validate session/token on boot before showing authenticated shell.
- Resource loaders (tenant, workspace, org) must expose **error** vs **empty**.
- Never map API/auth failure to first-run “create resource” UX.
- Recovery playbook: re-auth / retry before create flows.
- Never silently clear loaded entities in `catch` without error state.

**Generalize terms:** “household” → “tenant scope” / “primary resource”; “PocketBase authStore” → “client session store”.

#### `rules-precedence.md`

1. Explicit user instruction in the current message
2. Project hard rules (`AGENTS.md` or equivalent)
3. Project harness targets (`.cursor/rules/*.mdc`, …)
4. Project OKF concepts (explanatory; fix OKF when conflict)
5. Portable Harness Rules (this package)
6. General best practices

### 4.2 New guides (`okf/guides/`)

| Guide | From |
|-------|------|
| `okf-consume-and-maintain.md` | `okf.mdc` |
| `okf-changelog-log.md` | `okf/log.md` practice |
| `okf-baseline-capture.md` | skill `capturing-okf-baseline` |
| `okf-update-after-architecture-change.md` | skill `updating-okf-knowledge` |
| `rule-layering.md` | Pattern A vs B (overview doc vs OKF bundle) |

### 4.3 New references (`okf/reference/`)

| Reference | From |
|-----------|------|
| `okf-v0.2-in-repo-layout.md` | energy-tracker `okf/` structure |
| `validators/okf-bundle-checklist.md` | `scripts/test-okf-bundle.ts` behavior |
| `health-check-tiers-ietf.md` | `okf/deploy/health-endpoints.md` |
| `pre-deploy-data-snapshot.md` | `okf/deploy/backup-restore.md` phase 1 |
| `extractions/energy-tracker.md` | this file |

### 4.4 Project templates (stay out of harness rules body)

| Template path (suggested) | Content |
|---------------------------|---------|
| `okf/reference/templates/AGENTS-hard-rules.md` | Stack + must/never sections to copy |
| `okf/reference/templates/cursor-rule-okf.mdc` | alwaysApply OKF pointer |
| `okf/reference/templates/push-opt-in-playbook.md` | From AGENTS push section |

---

## 5. Rule composition (pattern note)

**energy-tracker:** thin always-on rules → heavy **`AGENTS.md`** → deep **`okf/`** domains.

**event-pos-desktop:** several always-on **`.mdc`** layers (generic view architecture + specific slave drilldown + tests + vite/handbook + APP_OVERVIEW sync).

**Harness recommendation:** Document both patterns in `okf/guides/rule-layering.md`:

- *Pattern A (overview doc):* `APP_OVERVIEW.md` + sync rule — good for single-app UX catalogs.
- *Pattern B (OKF bundle):* `AGENTS.md` + `okf/` + `log.md` — good for multi-domain backends and ops.

---

## 6. Project-only command map (implementation)

For **`quality-gates`** project profile — **not** harness rule prose:

| Gate | energy-tracker command |
|------|------------------------|
| Lint | `npm run lint` |
| Unit/domain tests | `npm test` |
| OKF bundle | `npm run test:okf` |
| Production build | `npm run build` |
| Optional pre-commit (not enforced by rule file) | same as CI |

---

## 7. Extraction metadata

| Field | Value |
|-------|-------|
| Repo | `BigAl42/energy-tracker` (private) |
| Branch analyzed | `origin/main` |
| `.mdc` count | 2 |
| OKF domains | 6 |
| Harness dependency | None |
| Harness integration | v0.4.0 — §4.1–4.4 implemented; this extraction `status: reviewed` |

---

## 8. Integration checklist (maintainer)

- [x] Store this extraction under `okf/reference/extractions/energy-tracker.md`
- [x] Draft harness rules from §4.1; cross-link from `quality-gates` and `instruction-following`
- [x] Add guides §4.2 and references §4.3–4.4
- [x] Add APM mirror stubs under `.apm/instructions/` for new harness rules
- [x] Do **not** copy PocketBase/push/forecast OKF into harness (Category E)
- [ ] Optionally consume `development-harness` from energy-tracker via APM (consumer-side)
