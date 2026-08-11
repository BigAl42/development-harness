---
type: Playbook
title: OKF Consume and Maintain
description: Always-on workflow for reading and updating an in-repo OKF bundle during architecture work
tags: [okf, playbook, agent-workflow]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-okf-mdc
    resource: https://github.com/BigAl42/energy-tracker
    title: .cursor/rules/okf.mdc (generalized)
---

# OKF Consume and Maintain

For consumer projects that keep an in-repo `okf/` knowledge bundle.

## When this applies

Architecture, schema, ACL, deploy, push, or other domain work that changes how the system works. Skip for pure typos, copy edits, or UI cosmetics with no behavioral change.

## Consume (before coding)

1. Read `okf/index.md` (check `okf_version`)
2. Open the relevant **domain index**
3. Load matching concepts by `type`, `tags`, or links
4. Respect trust signals (`verified`, `stale_after`, `status`)
5. On conflict: follow [Rules Precedence](/harness-rules/rules-precedence.md) — hard rules win; fix OKF when it drifts

## Maintain (same change)

1. Update or add concepts under the right domain
2. Append an entry to `okf/log.md` (see [OKF Changelog](/guides/okf-changelog-log.md))
3. Align `AGENTS.md` / project rules if must/never changed
4. Run the project OKF validator (e.g. `npm run test:okf`) before merge

## Project wiring

Use a thin always-on rule that points here — see [cursor-rule-okf template](/reference/templates/cursor-rule-okf.mdc). Domain hard rules stay in `AGENTS.md`.

## Related

- [Applying OKF v0.2](/guides/okf-v0.2-application.md)
- [OKF Baseline Capture](/guides/okf-baseline-capture.md)
- [OKF Update After Architecture Change](/guides/okf-update-after-architecture-change.md)
- [OKF Bundle Checklist](/reference/validators/okf-bundle-checklist.md)
