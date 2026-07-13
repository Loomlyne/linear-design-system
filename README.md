# Linear Design System

A reusable dark-first, near-black monochrome design system — shadcn/ui + Radix primitives, Poppins + IBM Plex Mono typography, restrained single-accent color, grid-disciplined layout.

Originated from the Invios (invoicing SaaS) redesign, generalized here as a standalone base for future apps. Named for its closest visual reference (Linear's dashboard register), not affiliated with Linear.

## Contents

- **[`DESIGN.md`](./DESIGN.md)** — the full design system spec: typography, color, spacing, layout, motion, component patterns, and the rationale/decisions log behind each choice. Read this before wiring the system into any app.
- **[`preview.html`](./preview.html)** — self-contained reference preview (fonts embedded, no external dependencies). Open directly in a browser. Shows the full system applied to a realistic dashboard mockup: sidebar nav, asymmetric hero metric, revenue chart, ledger-mode invoice table, mobile nav callout, plus a type/color/component specimen. Has a light/dark toggle.
- **[`fonts/`](./fonts)** — raw woff2 files (Poppins 400/500/600/700, IBM Plex Mono 400/500, Latin subset only) already embedded as base64 in `preview.html`, kept here standalone so any app can self-host them without re-fetching from Google Fonts.

## Using this in a new app

1. Read `DESIGN.md` — treat color/type as defaults to adapt per-product (especially the accent hex, which is Invios' brand color, not a fixed system color).
2. Copy the `@font-face` blocks and CSS custom properties out of `preview.html`'s `<style>` block as your starting token layer.
3. Build shadcn/ui components against those tokens (Button, Card, Badge, Table, Sheet, Dialog, etc.) rather than hand-rolling new component styles.
4. Keep the two named "risk" patterns — tabular-numeral pairing for real numbers, ledger-mode tables for money/transaction data — wherever the new app has financial or otherwise ledger-like data. They're the load-bearing differentiators, not decoration.

## Origin

Built during a design consultation for [Invios](https://invios.online) (invoicing/quotations SaaS), referencing [Runey](https://runey.app)'s dashboard hierarchy/spacing/motion and [Linear](https://linear.app)'s dark monochrome register — branding and copy from neither were copied. See `DESIGN.md`'s Decisions Log for the full reasoning trail.
