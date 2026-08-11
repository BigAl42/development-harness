---
type: Harness Rule
title: Rules Precedence
description: Conflict resolution across user instructions, project hard rules, OKF, and harness rules
tags: [harness-rules, compliance, precedence]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T11:35:00Z"
sources:
  - id: energy-tracker-agents-precedence
    resource: https://github.com/BigAl42/energy-tracker
    title: AGENTS.md wins over OKF / cursor rules (generalized)
---

# Rules Precedence

When instructions conflict, apply this order (highest first):

1. **Explicit user instruction** in the current message
2. **Project hard rules** — `AGENTS.md` or equivalent non-negotiable must/never list (including the same text injected as cloud hard rules)
3. **Project harness targets** — e.g. `.cursor/rules/*.mdc`, `.github/instructions/`
4. **Project OKF concepts** — explanatory domain knowledge; if they conflict with hard rules, **fix the OKF** (and `okf/log.md`), do not silently override hard rules
5. **Portable Harness Rules** (this package)
6. **General best practices**

## Notes

- Hard rules **win** over OKF. OKF explains and documents; it does not soften must/never constraints.
- Harness rules are cross-project defaults. Project layers may tighten them; they should not invent conflicting silent exceptions without updating the higher layer.
- See [Instruction Following](/harness-rules/instruction-following.md) for the obligation to follow instructions completely.
- See [Rule Layering](/guides/rule-layering.md) for Pattern A (overview doc) vs Pattern B (OKF bundle).
