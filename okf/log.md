# Directory Update Log

## 2026-08-16

* **Creation**: Consumer integration playbook + skill `integrating-development-harness` (v0.5.0)
* **Update**: APM instruction mirror, index, README, mapping

## 2026-08-12

* **Update**: Genericize situational rules (v0.4.2) — drop project nouns (`household`, `whats-new`, app-specific nav paths) from rule text and `applyTo`
* **Update**: P0 APM alignment (v0.4.1) — narrow `applyTo` on situational instructions; pin `targets:` in `apm.yml`; document `apm compile --validate`; CI workflow
* **Creation**: Harness rules extracted from energy-tracker + kredit-tracker (v0.4.0)
  - `okf-knowledge-workflow` — consume/maintain OKF in consumer repos
  - `domain-logic-first` — pure calc, metrics before UI, parallel module isolation
  - `sharing-privacy` — membership ACL, invite-only, no global user directory
  - `web-push-privacy` — no broadcast, preference gates, endpoint hygiene, no VAPID in git
  - `mobile-web-shell` — portals for fixed overlays, safe areas, touch/input defaults
* **Update**: APM instructions, index, README, deployment/mapping tables

## 2026-08-11

* **Update**: English-only harness rule; full bundle translated to English (v0.3.0)
* **Update**: Harness rules model — rules in `okf/harness-rules/`; `.cursor/rules/` generated only (gitignored)
* **Update**: OKF v0.2 conformance and meta playbook
* **Creation**: Initial bundle (extracted from Cursor user rules and event-pos-desktop)
