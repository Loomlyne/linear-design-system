---
name: "Linear Design System"
category: Product
surface: web
status: published
source: "https://github.com/Loomlyne/linear-design-system"
local: "/Users/koss/Developer/linear-design-system"
colors:
  background: "#0d0d0d"
  card: "#171717"
  elevated: "#212121"
  foreground: "#f5f3ef"
  muted: "#a5a099"
  muted-2: "#716c64"
  border: "rgba(245,243,239,0.09)"
  accent: "#eab308"
  accent-light: "#ca8a04"
  success: "#3ddc73"
  warning: "#ff9142"
  destructive: "#ff6455"
  light-background: "#f7f6f4"
  light-card: "#ffffff"
  light-elevated: "#fbfaf8"
  light-foreground: "#17140f"
  light-muted: "#6f6a61"
  light-muted-2: "#96908d"
  light-border: "rgba(23,18,15,0.10)"
  light-success: "#16803c"
  light-warning: "#c2540c"
  light-destructive: "#c0311a"
typography:
  display:
    fontFamily: Poppins
    fontWeight: 600
  body:
    fontFamily: Poppins
    fontWeight: 400
  ui:
    fontFamily: Poppins
    fontWeight: 500
  data:
    fontFamily: "IBM Plex Mono"
    fontWeight: 400
rounded:
  base: 0.875rem
  card: 1.25rem
  pill: 999px
  ledger: 0
spacing:
  base: 4px
---

# Design System — Linear Design System

A reusable dark-first, near-black monochrome design system: shadcn/ui + Radix primitives, Poppins + IBM Plex Mono typography, restrained single-accent color, grid-disciplined layout. Originated from the Invios (invoicing SaaS) redesign, generalized here as a standalone base for future apps.

> **Open Design default.** This file is the live source of truth. It is symlinked into Open Design as `user:linear-design-system`. Edit this repo, not the Wise onboarding system. Never fall back to generic purple SaaS, Inter-only stacks, or equal KPI cards when this system is active.

## Origin / Product Context
- **Where this came from:** Built for Invios, an invoicing/quotations SaaS for freelancers, consultants, and small agencies — positioned as "a serious tool, not a toy."
- **Reference sites:** https://runey.app (layout/hierarchy/component behavior/motion — not branding or copy), https://linear.app (dark monochrome visual register).
- **Intended use here:** Portable base for Invios and future apps. Tokens are defaults to adapt per-product (especially accent hue), not sacred law — **patterns** (mono tabular nums, ledger tables, single accent, dark-first) are non-negotiable.

## Aesthetic Direction
- **Direction:** Industrial/Utilitarian — minimal decoration, typography and spacing carry all visual weight.
- **Decoration level:** Minimal.
- **Mood:** Near-black, dense, precise. Reads as a serious instrument, not a friendly template.

## Typography
- **Display/Hero:** Poppins, weight 600.
- **Body:** Poppins, weight 400.
- **UI/Labels:** Poppins, weight 500.
- **Data/Tables:** IBM Plex Mono, tabular figures — every real number (amounts, KPI values, table columns) uses this so multi-digit totals actually align in columns. Poppins alone is proportional and will visibly misalign.
- **Code:** IBM Plex Mono (same face as data, no separate code font needed).
- **Loading:** Self-hosted — both families embedded as `@font-face` (Latin subset), avoiding a Google Fonts CDN runtime dependency. Weights: Poppins 400/500/600/700, IBM Plex Mono 400/500. Font files + base64 payloads live in `fonts/`.
- **Scale:** Hero/page-title 1.35–2.25rem (600), section heading 1.5rem (600), body 0.875–1rem (400), label/caption 0.75rem (500, uppercase, 0.06em tracking), hero metric figure 3rem (500, mono).
- **Honest tradeoff:** Poppins is a common "safe SaaS" choice. The IBM Plex Mono tabular pairing is what keeps a Poppins-based UI from reading as templated once real data is on screen — lean on that pairing, don't drop it.

## Color
- **Approach:** Restrained — near-black neutrals + one accent reserved for the primary action only.
- **Accent:** `#eab308` (dark mode) / `#ca8a04` (light mode) — Invios brand gold, brightened for near-black. Swap per-product if needed; keep single-accent discipline.
- **Neutrals (dark):** background `#0d0d0d`, card `#171717`, elevated `#212121`, border `rgba(245,243,239,0.09)`, foreground `#f5f3ef`, muted `#a5a099`, muted-2 `#716c64`.
- **Neutrals (light):** background `#f7f6f4`, card `#ffffff`, elevated `#fbfaf8`, border `rgba(23,18,15,0.10)`, foreground `#17140f`, muted `#6f6a61`, muted-2 `#96908d`.
- **Semantic:** success `#3ddc73` dark / `#16803c` light, warning `#ff9142` dark / `#c2540c` light, destructive `#ff6455` dark / `#c0311a` light. Accent never doubles as status.
- **Dark mode:** Dark-first, default. Light mode is a full restrained-monochrome counterpart, not an afterthought.

## Spacing
- **Base unit:** 4px.
- **Density:** Mixed — compact controls (buttons, pills, nav) + generous card padding (1.5–2rem).
- **Scale:** 2xs(2) xs(4) sm(8) md(16) lg(24) xl(32) 2xl(48) 3xl(64).

## Layout
- **Approach:** Grid-disciplined — strict alignment, no editorial asymmetry outside deliberate exceptions (ledger tables / hero metric).
- **Grid:** Responsive 12-column dashboard grid; fixed **15rem** left sidebar (icons + labels, settings/profile at bottom) on desktop.
- **Mobile nav:** Per-product. Invios uses bottom tab bar + center FAB (not a drawer). Don't assume drawer just because desktop is sidebar.
- **Max content width:** 1360px.
- **Border radius:** Base `0.875rem` (14px), cards/panels `1.25–1.5rem`, pills/badges `999px`. **Ledger-mode tables: `0` radius.**

## Motion
- **Approach:** Minimal-functional — only transitions that aid comprehension.
- **Easing:** enter/hover(ease-out) exit(ease-in) move(ease-in-out).
- **Duration:** hover/control 150–200ms, sidebar/drawer 200–250ms, dialog/menu/toast 150–200ms.
- **Reduced motion:** Respect `prefers-reduced-motion: reduce`.

## Component Patterns (load-bearing)
- **Tabular-numeral pairing:** any real number (money, counts, numeric dates) in mono + `font-variant-numeric: tabular-nums`. Non-negotiable for column alignment.
- **Asymmetric hero metric:** one dominant number (2–3× supporting KPIs) for dashboards when product validates it — not equal KPI soup by default.
- **Ledger-mode data tables:** money/transactions only — 0 radius, hairline row dividers, mono tabular figures, no card chrome. Not for every table.
- **Status as dot + word, never color alone.**
- **Icons in nav:** Lucide 16–18px, thin stroke, muted default / brighter active.
- **shadcn/ui + Radix** primitives — don't invent parallel component styles.

## Agent Rules (Open Design / Claude Design / Hermes)
1. Always load this DESIGN.md before generating UI. Prefer `user:linear-design-system` over stock/default/Wise.
2. Dark mode is the default frame unless the user asks for light. Deliver light as a full counterpart when requested.
3. **One accent action per screen.** Secondary actions are neutral/ghost. Never paint charts or status with the accent.
4. Money, dates-as-numbers, and KPI figures → **IBM Plex Mono tabular**. Labels/headings → Poppins.
5. Status badges = colored **dot + word**. Never color-only chips or full-row status tints.
6. Ledger tables only for invoices/transactions/audit logs. Client rosters and CRM lists may use soft card chrome.
7. Desktop shell: 15rem sidebar + max content 1360px + 12-col grid. Mobile: bottom nav + FAB for Invios-class apps unless told otherwise.
8. Empty states: serious copy, one primary CTA, no decorative illustration kits. Tone: "a serious tool, not a toy."
9. Loading: section skeletons matching layout — no spinners as primary pattern.
10. Do **not** use: Inter-only stacks, purple/indigo SaaS gradients, glassmorphism, equal four-KPI hero rows, Google Fonts CDN, emoji as UI chrome, fake Lorem for product demos when a content bible exists.
11. For Invios multi-screen work, follow `PROMPTS.md` content bible (clients, team, numbers, dates) for consistency.
12. Preview ground truth: open `preview.html` in this repo before inventing new visual register.

## Do's and Don'ts

### Do
- Self-host Poppins + IBM Plex Mono from `fonts/`
- Reserve accent for primary buttons / active brand moments only
- Pair every status color with a text label
- Keep financial tables in ledger mode
- Match Runey-like hierarchy/spacing without copying Runey branding

### Don't
- Use accent as chart series or status color
- Drop mono tabular nums on money columns
- Invent a second accent
- Apply 0-radius ledger treatment to every table
- Fall back to Wise / generic default systems while this one is active
- Paste Claude Design marketing chrome into product screens

## Reference Preview
`preview.html` — self-contained, fonts embedded, light/dark toggle — full dashboard mockup (sidebar, asymmetric hero, revenue chart, ledger invoice table, mobile nav callout). Open it before wiring into an app.

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-07-13 | Dark-first near-black monochrome + Poppins + 0.875rem radius, modeled on Runey's hierarchy/spacing/motion (not branding/copy) | Invios visual system after rejecting platform rebuilds; generalized for reuse |
| 2026-07-13 | Pair Poppins with IBM Plex Mono tabular figures for every real number | Column alignment; fintech-grade density |
| 2026-07-13 | Asymmetric hero metric pattern (validate per product) | Instant signal vs equal KPI cards |
| 2026-07-13 | Ledger-mode tables for money data | Register break for "serious tool, not a toy" |
| 2026-07-13 | Icons kept in primary nav | Scannability over icon-free trend |
| 2026-07-13 | Standalone repo extract | Point future apps here instead of forking tokens per product |
| 2026-07-17 | Wired as Open Design live default (`user:linear-design-system` symlink) | Replace Wise onboarding; Hermes/Claude/OD share one source of truth |
