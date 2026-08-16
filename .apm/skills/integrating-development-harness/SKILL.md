---
name: integrating-development-harness
description: >-
  Integrate BigAl42/development-harness into a consumer repo via APM (apm.yml,
  install, compile, dedupe local Cursor/AGENTS rules). Use when adding or
  upgrading the harness dependency, or when the user asks to wire harness rules
  into a project.
---

# Integrating development-harness

Follow the playbook [Consumer Integration](/okf/guides/consumer-integration.md) in the harness package. Summary workflow below.

## When

- User asks to add/upgrade `BigAl42/development-harness`
- Repo has no `apm.yml` harness dep yet, or pin is outdated
- Local rules heavily duplicate portable principles

## Do

1. Ensure APM CLI: `curl -sSL https://aka.ms/apm-unix | sh` if `apm` missing  
2. Create/update root `apm.yml`:
   - `dependencies.apm`: `BigAl42/development-harness#v0.6.0` (or newer tag the user names)
   - Default `targets: [cursor]` unless the user asks for more harnesses  
3. Run `apm install`, then `apm compile --validate`, then `apm compile`  
4. Commit `apm.yml` and `apm.lock.yaml`  
5. Deduplicate local `.cursor/rules/` and `AGENTS.md` using the playbook checklist  
6. Keep concrete quality-gate **commands** and stack/domain rules in the consumer  
7. If this is a UI product and root `DESIGN.md` is missing, create it with skill `authoring-design-md` (same PR or follow-up — ask if unclear)  
8. Open a PR: harness dep + dedupe summary; no unrelated product work  

## Do not

- Hand-edit generated files from the harness package  
- Put project-specific commands, domain paths, or product colors into the harness package  
- Create a full `okf/` baseline unless the user asks  
- Expand `targets` beyond Cursor unless requested  

## Priority

User instruction > consumer project rules / `AGENTS.md` > harness rules > best practices.

## Related

- Playbook: `okf/guides/consumer-integration.md`  
- Skill `authoring-design-md` — consumer `DESIGN.md`  
- [Harness Deployment](/okf/reference/harness-deployment.md)  
- Skill `harness-rules` — authoring/maintaining the harness package itself
