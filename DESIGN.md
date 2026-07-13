# Design System — Linear Design System

A reusable dark-first, near-black monochrome design system: shadcn/ui + Radix primitives, Poppins + IBM Plex Mono typography, restrained single-accent color, grid-disciplined layout. Originated from the Invios (invoicing SaaS) redesign, generalized here as a standalone base for future apps.

## Origin / Product Context
- **Where this came from:** Built for Invios, an invoicing/quotations SaaS for freelancers, consultants, and small agencies — positioned as "a serious tool, not a toy."
- **Reference sites:** https://runey.app (layout/hierarchy/component behavior/motion — not branding or copy), https://linear.app (dark monochrome visual register).
- **Intended use here:** A portable starting point for future apps/platform work — not tied to Invios specifically. Treat the tokens and rationale below as defaults to adapt per-product, not hardcoded law.

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
- **Honest tradeoff:** Poppins is a common "safe SaaS" choice (geometric-rounded, associated with no-code/template tools). The IBM Plex Mono tabular pairing is what keeps a Poppins-based UI from reading as templated once real data is on screen — lean on that pairing, don't drop it.

## Color
- **Approach:** Restrained — near-black neutrals + one accent reserved for the primary action only.
- **Accent:** `#eab308` (dark mode) / `#ca8a04` (light mode) — originally Invios' brand gold, brightened for legibility on near-black surfaces. **Swap this per-product** — the point of the system is restraint and one accent, not this specific hue.
- **Neutrals (dark):** background `#0d0d0d`, card `#171717`, elevated `#212121`, border `rgba(245,243,239,0.09)`, foreground `#f5f3ef`, muted `#a5a099`, muted-2 `#716c64`.
- **Neutrals (light):** background `#f7f6f4`, card `#ffffff`, elevated `#fbfaf8`, border `rgba(23,18,15,0.10)`, foreground `#17140f`, muted `#6f6a61`, muted-2 `#96908d`.
- **Semantic:** success `#3ddc73` dark / `#16803c` light, warning `#ff9142` dark / `#c2540c` light, destructive `#ff6455` dark / `#c0311a` light. Deliberately distinct hues from the accent — the accent must never double as a status color.
- **Dark mode:** Dark-first, default. Light mode is a full restrained-monochrome counterpart, not an afterthought — same relationships, same accent hue family, adjusted lightness/contrast per surface.

## Spacing
- **Base unit:** 4px.
- **Density:** Mixed by design — compact controls (buttons, pills, nav items) paired with generous card padding (1.5–2rem). Controls stay dense and efficient; containers stay breathable.
- **Scale:** 2xs(2) xs(4) sm(8) md(16) lg(24) xl(32) 2xl(48) 3xl(64).

## Layout
- **Approach:** Grid-disciplined — strict alignment, no editorial asymmetry outside deliberate exceptions (see ledger tables / hero metric below).
- **Grid:** Responsive 12-column dashboard grid; fixed 15rem left sidebar (icons + labels, bottom settings/profile) on desktop.
- **Mobile nav:** Not prescribed here — Invios kept its existing bottom tab bar + FAB rather than a drawer, justified by shipped usage data. Decide per-product; don't assume a drawer is required just because the desktop pattern is sidebar-based.
- **Max content width:** 1360px.
- **Border radius:** Base `0.875rem` (14px), cards/panels `1.25–1.5rem` (16–24px), pills/badges `999px` (full). **Exception: ledger-mode tables use `0` radius** — see Component Patterns.

## Motion
- **Approach:** Minimal-functional — only transitions that aid comprehension, nothing decorative.
- **Easing:** enter/hover(ease-out) exit(ease-in) move(ease-in-out).
- **Duration:** hover/control micro(150–200ms), sidebar/drawer slide(200–250ms), dialog/menu/toast fade+scale(150–200ms).
- **Reduced motion:** All transitions/animations respect `prefers-reduced-motion: reduce`.

## Component Patterns (the risks worth reusing)
- **Tabular-numeral pairing:** any real number (money, counts, dates-as-numbers) renders in the mono face with `font-variant-numeric: tabular-nums`. Non-negotiable wherever digits line up in columns.
- **Asymmetric hero metric:** for dashboards, consider one dominant number (2-3x the size of supporting KPIs) instead of N equal KPI cards — gives an instant "am I in trouble or fine" signal. **Caveat:** this was prototyped, not field-tested — picking the "one most important number" is a product decision that may not generalize across all user contexts. Validate per-product before treating it as default.
- **Ledger-mode data tables:** for data that represents money/transactions specifically, break from the soft rounded-card treatment used elsewhere — zero radius, hairline row dividers, mono tabular figures, no card chrome. Creates a deliberate "this is where the real records live" register shift. Don't apply this to every table — only where the content is genuinely ledger-like (invoices, transactions, audit logs).
- **Status as dot + word, never color alone:** every status badge pairs a small colored dot with a text label (Paid / Overdue / Draft), not color-only chips — accessibility and scannability both benefit.
- **Icons in nav:** kept for Invios (declined the icon-free-nav option) — Lucide, 16-18px, thin stroke, muted default/brighter on hover/active.

## Reference Preview
`preview.html` in this repo — self-contained, fonts embedded, light/dark toggle — renders the full system against a realistic dashboard mockup (sidebar nav, asymmetric hero metric, revenue chart, ledger-mode invoice table, mobile nav callout). Open it directly in a browser to see the system live before wiring it into any specific app's codebase.

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-07-13 | Dark-first near-black monochrome + Poppins + 0.875rem radius, modeled on Runey's dashboard hierarchy/spacing/motion (not its branding/copy) | Originated for Invios after ruling out platform rebuilds (Twenty CRM, Invoicerr, Base44, Lovable, Replit) as ways to get a "full client-workflow OS" — this repo generalizes the resulting visual system for reuse |
| 2026-07-13 | Pair Poppins with IBM Plex Mono (tabular figures) for every real number | Poppins is proportional and misaligns multi-digit totals in columns; serious fintech tools (Mercury, Ramp) pair a display face with a tabular-numeral face for this reason |
| 2026-07-13 | Asymmetric hero metric (one dominant number) instead of N equal KPI cards | Every competitor examined (Runey, Linear, Stripe, Ramp) treats KPIs as equal; a dominant figure gives instant signal, borrowed from trading-terminal hierarchy. Not field-tested — treat as a pattern to validate, not a default |
| 2026-07-13 | Ledger-mode data tables: zero border-radius, hairline rows, mono tabular figures, no card chrome | Deliberate register break for money/transaction data specifically — reinforces "serious tool, not a toy" exactly where it matters most |
| 2026-07-13 | Declined icon-free primary nav for Invios | Considered, explicitly not taken — icons stayed for scannability |
| 2026-07-13 | Extracted from the Invios repo into a standalone repo | Meant to be pointed at by future apps/platform work, not committed into any single product's codebase |
