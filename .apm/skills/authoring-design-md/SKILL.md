---
name: authoring-design-md
description: >-
  Create or update a consumer repo root DESIGN.md per the Google Labs design.md
  format (YAML tokens + markdown rationale). Use when adding visual identity for
  agents, capturing an existing UI brand, or changing colors/typography/components.
---

# Authoring DESIGN.md

Follow playbook [Applying DESIGN.md](/okf/guides/design-md-application.md). Spec: https://github.com/google-labs-code/design.md

## When

- Repo has UI but no root `DESIGN.md`
- User asks to capture / refresh visual identity for agents
- A PR changes brand colors, type, spacing, or shared component look

## Do

1. Read existing `DESIGN.md` if present; otherwise scan CSS variables, theme files, and key screens  
2. Write or update **repo-root** `DESIGN.md`:
   - YAML front matter: `name`, `colors` (include `primary`), `typography`; add `rounded`, `spacing`, `components` when known  
   - Body sections in spec order; omit only via `omitted:` with reasons when intentional  
3. Tokens are normative; prose explains application  
4. Lint when possible: `npx @google/design.md lint DESIGN.md` (on Windows shells prefer `npx -p @google/design.md designmd lint DESIGN.md`)  
5. Keep product tokens in the consumer repo — never publish them into `development-harness`  

## Do not

- Invent a conflicting palette when a clear brand already exists in code  
- Skip Overview/Colors/Typography on first create without documenting why under `omitted`  
- Duplicate DESIGN.md content into always-on Cursor rules; point agents at the file instead  

## Related

- Harness rule `design-md`  
- Playbook `okf/guides/design-md-application.md`
