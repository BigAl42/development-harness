---
applyTo: "apm.yml,apm.lock.yaml,AGENTS.md,.cursor/rules/**,.gitignore"
description: "Playbook: integrate BigAl42/development-harness via APM — install, Cursor-only targets, dedupe local rules"
harnessRule: consumer-integration
source: okf/guides/consumer-integration.md
---

# Consumer Integration

Add `BigAl42/development-harness#v0.5.0` under `dependencies.apm`, set `targets: [cursor]` unless asked otherwise. Run `apm install` then `apm compile --validate` / `apm compile`. Commit `apm.yml` + `apm.lock.yaml`. Deduplicate local rules that only repeat harness principles; keep stack/domain/commands. Priority: user > project rules > harness. Full playbook: `okf/guides/consumer-integration.md` (in the harness package). Use skill `integrating-development-harness`.

Source: `okf/guides/consumer-integration.md`
