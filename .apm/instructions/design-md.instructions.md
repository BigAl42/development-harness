---
applyTo: "DESIGN.md,**/DESIGN.md,**/*.{css,scss},**/globals.css,**/tailwind*.{js,ts,cjs,mjs},**/*.{tsx,jsx,vue,svelte}"
description: "Harness Rule: Read/create/update Google Labs DESIGN.md for UI work — tokens normative"
harnessRule: design-md
source: okf/harness-rules/design-md.md
---

# Harness Rule: DESIGN.md Visual Identity

Before substantive UI work, read repo-root `DESIGN.md` (Google Labs format: YAML tokens + markdown rationale). Tokens are normative. If missing for a UI product, create it (skill `authoring-design-md`). Update DESIGN.md in the same PR as intentional visual changes. Lint with `npx @google/design.md lint DESIGN.md` when available. Product tokens stay in the consumer repo.

Source: `okf/harness-rules/design-md.md`
