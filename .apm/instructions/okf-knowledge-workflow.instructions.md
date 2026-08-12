---
applyTo: "okf/**"
description: "Harness Rule: When okf/ exists — read before structural work; update concepts + log + validate in the same change"
harnessRule: okf-knowledge-workflow
source: okf/harness-rules/okf-knowledge-workflow.md
---

# Harness Rule: OKF Knowledge Workflow

When the repo has `okf/`: read index → domain → concepts before architecture/schema/ACL/deploy/push work. After: update concepts (English) + `okf/log.md` + run project OKF validation. Hard rules override OKF — fix OKF on conflict. No typo/UI-only cosmetics in OKF.

Source: `okf/harness-rules/okf-knowledge-workflow.md`
