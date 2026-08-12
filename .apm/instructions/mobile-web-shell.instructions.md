---
applyTo: "**/*.{tsx,jsx,css,scss},**/layout.*,**/shell*,**/nav*,**/header*,**/tabbar*,**/tab-bar*"
description: "Harness Rule: Mobile web/PWA shell — portals for fixed overlays, safe areas, touch/input defaults"
harnessRule: mobile-web-shell
source: okf/harness-rules/mobile-web-shell.md
---

# Harness Rule: Mobile Web Shell

Portal fixed overlays to `document.body`. Avoid `position: fixed` under `backdrop-blur`/`filter`/`transform` on iOS. Safe-area insets; ~44px touch targets; inputs ≥16px font.

Source: `okf/harness-rules/mobile-web-shell.md`
