---
type: Playbook
title: Applying DESIGN.md
description: Create and maintain consumer DESIGN.md files per the Google Labs format so agents share one visual identity
tags: [design-md, playbook, ui, frontend, tokens]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-16T07:55:00Z
sources:
  - id: google-labs-design-md
    resource: https://github.com/google-labs-code/design.md
    title: DESIGN.md format specification
  - id: google-labs-design-md-spec
    resource: https://github.com/google-labs-code/design.md/blob/main/docs/spec.md
    title: DESIGN.md Format Spec
---

# Applying DESIGN.md

Playbook for **consumer** repos. Spec: [google-labs-code/design.md](https://github.com/google-labs-code/design.md) (`docs/spec.md`). Format version is currently `alpha`.

## Goal

Give coding agents a persistent visual identity: machine-readable tokens + human rationale in one `DESIGN.md` at the repo root.

## File structure

1. **YAML front matter** (`---` … `---`) — normative tokens  
2. **Markdown body** — `##` sections in canonical order  

### Token schema (summary)

```yaml
version: alpha          # optional
name: <string>
description: <string>   # optional
omitted: []             # optional intentional omissions
colors:
  primary: "#…"
typography:
  body-md:
    fontFamily: …
    fontSize: 16px
rounded:
  sm: 4px
spacing:
  md: 16px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
```

Use `{path.to.token}` references inside `components`. Prefer hex colors unless the product already standardizes another CSS color space.

### Section order (present sections only)

1. Overview (alias: Brand & Style)  
2. Colors  
3. Typography  
4. Layout (alias: Layout & Spacing)  
5. Elevation & Depth  
6. Shapes  
7. Components  
8. Do's and Don'ts  

Unknown `##` sections are allowed; duplicate section headings are not.

## Create (consumer has no DESIGN.md)

1. Infer brand from existing UI, CSS variables, screenshots, or product brief  
2. Write root `DESIGN.md` with at least: `name`, `colors` (include `primary`), `typography`, Overview + Colors + Typography prose  
3. Add Layout / Shapes / Components / Do's and Don'ts when enough signal exists; otherwise list gaps under `omitted:` with reasons  
4. Lint: `npx @google/design.md lint DESIGN.md`  
5. Point UI agents at it (harness rule `design-md` after `apm install`)

Do **not** invent a second design system alongside an existing documented brand — capture what the product already uses.

## Update

- Visual change in the same PR → update tokens **and** matching prose  
- Broken `{token}` refs or contrast failures → fix before merge when lint is in use  
- Optional export for tooling:  
  `npx @google/design.md export --format css-tailwind DESIGN.md`  
  `npx @google/design.md export --format dtcg DESIGN.md`

## Minimal skeleton

```markdown
---
version: alpha
name: Example Product
colors:
  primary: "#1A1C1E"
  secondary: "#6C7278"
  tertiary: "#B8422E"
  neutral: "#F7F5F2"
  on-primary: "#F7F5F2"
typography:
  h1:
    fontFamily: Public Sans
    fontSize: 3rem
    fontWeight: 600
  body-md:
    fontFamily: Public Sans
    fontSize: 1rem
    fontWeight: 400
rounded:
  sm: 4px
  md: 8px
spacing:
  sm: 8px
  md: 16px
components:
  button-primary:
    backgroundColor: "{colors.tertiary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.sm}"
    padding: 12px
---

## Overview

One short paragraph: personality, density, emotional intent.

## Colors

- **Primary:** …
- **Tertiary:** sole interaction accent (or document otherwise)

## Typography

Headline vs body roles; avoid defaulting to Inter/Roboto/Arial unless the brand already uses them.

## Do's and Don'ts

- Do treat YAML tokens as source of truth
- Don't introduce one-off colors/fonts outside this file
```

Replace every example value with the consumer’s real brand. The skeleton above is illustrative only.

## Harness vs consumer

| Layer | Owns |
|-------|------|
| This package | Rule + playbook + skill (workflow) |
| Consumer `DESIGN.md` | Product tokens and rationale |
| Consumer CSS / theme | Implementation derived from DESIGN.md |

## Related

- Harness rule [DESIGN.md Visual Identity](/harness-rules/design-md.md)  
- Skill `authoring-design-md`  
- Spec: https://github.com/google-labs-code/design.md/blob/main/docs/spec.md
