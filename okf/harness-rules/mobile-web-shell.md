---
type: Harness Rule
title: Mobile Web Shell
description: Fixed overlays, safe areas, and touch/input defaults for mobile web and PWAs
tags: [harness-rules, mobile, pwa, ios, ui]
status: stable
generated:
  by: agent/cursor
  at: 2026-08-12T05:45:00Z
sources:
  - id: kredit-tracker-mobile-ios-shell
    resource: /kredit-tracker/.cursor/rules/mobile-ios-shell.mdc
    title: iOS/Mobile Shell (generalized)
  - id: energy-tracker-agents-ios
    resource: /energy-tracker/AGENTS.md
    title: iOS / PWA notes (partial)
---

# Mobile Web Shell

For mobile web apps and Homescreen PWAs (especially iOS Safari).

## Fixed overlays

Render tab bars, sheet menus, and similar **fixed** overlays with a portal to `document.body` (e.g. `createPortal(..., document.body)`).

`position: fixed` inside ancestors with `backdrop-blur`, `filter`, or `transform` is positioned relative to that ancestor on iOS — UI state may toggle while the overlay stays invisible.

## Safe areas and layout

- Use `viewport-fit=cover` (or framework equivalent) when drawing edge-to-edge chrome
- Apply `env(safe-area-inset-*)` to sticky headers and bottom chrome
- Prefer a bottom tab bar on small screens when the product has primary destinations; keep a denser nav on desktop if needed

## Touch and forms

- Touch targets ≈ 44×44 CSS px
- Form control font-size ≥ 16px to avoid Safari auto-zoom
- Horizontal chip/filter rows should scroll, not wrap awkwardly

## PWA push testing (iOS)

Homescreen install via Safari; notifications often invisible while the app is foregrounded — document leave/lock for manual tests. Concrete APIs stay in project rules.
