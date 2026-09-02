# Modulo — Design System

**Modulo** is a Filipino everyday-carry (EDC) wallet brand engineering functional, secure carry solutions — Silo Standard, Silo Femme, and Silo Core — for Metro Manila's daily commuters. The brand is not a fashion label; it is a utilitarian, systems-driven product company. Visual language is drawn directly from public transit signage (LRT/MRT wayfinding, MetroCard/farecard graphics) and is deliberately bold, high-contrast, and legible — the opposite of a soft, decorative lifestyle-accessory look.

Tagline: **"Organize your way, make your move."**

This file is the single source of truth for Modulo's visual identity. Tokens below are extracted directly from the coded reference site (`reference/modulo-landing-page-v2.html`) — not approximated from screenshots — so treat these values as exact.

---

## 1. Brand Personality

- **Utilitarian, not decorative.** Every visual choice should read as functional — like signage, not styling.
- **Confident and direct.** Bold weights, tight tracking on headlines, no hedging copy.
- **Systematic order.** Modularity is the core concept (see logo). Grids, consistent radii, and repeatable component patterns matter more than one-off flourishes.
- **Commuter-anchored.** Color and iconography reference the transit network (LRT/MRT lines) the target customer lives in every day.
- **Locally made, precision-built.** Craftsmanship and mechanical precision (RFID blocking, coin rails, tracker hardware) are part of the aesthetic — not just marketing copy.

---

## 2. Color

### Core palette (from `:root` CSS variables)

| Token | Hex | Usage |
|---|---|---|
| `--asphalt` | `#0D0D0D` | Primary text, dark surfaces (footer, ticker), near-black — not pure black |
| `--page` | `#E8E8E8` | Page/background base |
| `--card` | `#FAFAFA` | Card and hero surface (off-white, slightly warmer than page) |
| `--white` | `#FFFFFF` | Pure white — product cards, panels |
| `--line` | `#DEDEDE` | Hairline borders, input outlines |
| `--gray-600` | `#5F5F5F` | Secondary/body text on light surfaces |
| `--gray-400` | `#A9A9A9` | Muted/tertiary text, captions |

### Accent palette (transit-line colors)

| Token | Hex | Usage |
|---|---|---|
| `--blue` | `#1C74E2` | Primary CTA buttons, links, focus states |
| `--red` | `#FA3C2E` | Secondary CTA, cart badge, alert/urgency accents |
| `--orange` | `#FE6A00` | Feature-split backgrounds, warm accent |
| `--yellow` | `#FBD916` | Ticker dot, star ratings, highlight accent |
| `--green` | `#58DF55` | Feature-split backgrounds, positive/active state accent |

**Rule:** Accent colors map to Metro Manila's LRT/MRT line colors and should be used the way transit systems use color — as a wayfinding/identification device (e.g., one accent per product variant, per campaign, or per state), not as decorative gradient washes. Do not blend or gradient the accent colors together except for the specific brass/plate texture noted below.

**Exception:** one gradient exists in the reference site — a bronze/brass "engraved plate" effect (`linear-gradient(160deg,#7C4F2C,#4E3019)`) used once for a tactile, metal-plate visual moment. This is a special-case texture, not a general pattern — do not reuse it for buttons or backgrounds.

---

## 3. Typography

**Primary typeface:** `Neue Haas Grotesk Display Pro` (licensed trial files in `/fonts`)
**Fallback stack:** `'Helvetica Neue', 'Inter Tight', Helvetica, Arial, sans-serif`

Available weights (from `/fonts`): Thin (15X) → Black (95X), including italics at every weight. Production usage skews heavy:

| Weight | Use |
|---|---|
| 800 (Black-ish/ExtraBold) | H1, H2 headlines, price, hero numbers |
| 700 (Bold) | Buttons, nav links, labels, review text |
| 600 (SemiBold) | Body copy, descriptions |

### Type scale (fluid, `clamp()`-based)

| Role | Size | Notes |
|---|---|---|
| H1 | `clamp(34px, 4.6vw, 54px)` | weight 800, letter-spacing `-.035em`, line-height `1.06` |
| H2 | `clamp(26px, 3.2vw, 38px)` | weight 800, same tracking/leading as H1 |
| H3 | `clamp(18px, 1.9vw, 22px)` | weight 800, letter-spacing `-.028em` |
| Big readout number (stat callouts) | `clamp(38px, 5vw, 58px)` | weight 800, letter-spacing `-.045em` |
| Body | 16px base, 14–14.5px in cards | weight 600, line-height 1.5–1.6 |
| Button/label | 14–14.5px | weight 700, letter-spacing `-.01em` |
| Eyebrow / uppercase micro-label | 9–11.5px | weight 700–800, letter-spacing `.10–.15em`, uppercase |

**Rule on tracking:** headline sizes get *tight, negative* tracking (compressed, confident); small uppercase labels get *wide, loose* tracking (signage-style spacing). Never apply loose tracking to large text or tight tracking to tiny labels — the contrast between the two is intentional and load-bearing for the transit-signage feel.

---

## 4. Shape & Elevation

| Token | Value | Usage |
|---|---|---|
| `--r` (base radius) | `16px` | Cards, hero panel, product cards, split-feature panels |
| Small component radius | `8–10px` | Buttons, ticker, inputs |
| Pill radius | `999px` | Tags, pagination dots (active state), pill badges |
| Circular | `50%` | Avatar/icon buttons, swatches, social icons |

**Shadow:** one soft, low-opacity shadow is used across the system: `0 8px 26px rgba(0,0,0,.07)` (resting), escalating to `0 20px 40px rgba(0,0,0,.09)` on hover for product cards. Do not introduce heavier or colored shadows — the system relies on a single, consistent soft-elevation language.

---

## 5. Iconography

- Style: **line icons only**, never filled/solid.
- `viewBox="0 0 24 24"`, `stroke="currentColor"`, `stroke-width: 2` (occasionally `2.6` for emphasis, e.g. a single hero icon).
- `fill="none"` — icons are outlines, consistent with the "systematic, engineered" feel rather than soft filled glyphs.
- Icon buttons are circular (`border-radius: 50%`), 32×32px touch target, with a subtle `rgba(0,0,0,.07)` hover fill.

---

## 6. Components (patterns observed in production)

### Buttons
- Base: `padding: 11px 19px`, `border-radius: 8px`, `font-size: 14px`, `font-weight: 700`, `letter-spacing: -.01em`
- Variants: `--blue`, `--red`, `--black` (asphalt) backgrounds, white text
- Hover: lift `translateY(-2px)` + `filter: brightness(1.06)`; icon (if present) slides right `translateX(3px)`
- Icons inside buttons: 14×14px, animate on hover

### Product cards (`.pcard`)
- White background, base radius, padding 26px stage area + 22px body
- Hover: lift `translateY(-5px)`, escalate shadow, product image scales `1.07` and rotates `-2deg`
- Structure: image stage → description (max 30ch, gray-600) → color swatches → variant name (uppercase, tracked) → price (800 weight) → "view" link (blue, arrow icon)

### Feature-split panels (`.split`)
- Two-column: text left, colored art panel right (or flipped)
- Art panel background is a single flat accent color (orange/blue/yellow) — not a gradient
- Product shot floats within the panel with a drop-shadow, not a hard edge

### Tags/pills (`.tag`)
- Light gray `#F1F1F1` background, `999px` radius, small colored dot indicator + label, `11.5px` bold text

### Navigation
- Sticky, translucent/blurred background (`backdrop-filter: blur(12px)`)
- Underline-on-hover link style (animated width, not color change)
- Circular icon buttons for search/account/cart; cart carries a small red count badge

### Footer
- Full asphalt (`#0D0D0D`) background, white/gray text
- Uppercase, wide-tracked section headers (`11.5px`, `.15em` tracking)

---

## 7. Layout

- Max content width: `1180px`, centered, fluid side padding via `clamp(16px, 3.5vw, 34px)`
- Grid-first: hero, product lineup, and feature splits all use CSS grid with 1fr/1fr or 3-column layouts
- Single-column stacking below 900px; touch targets and type scale adjust down, animations are disabled or simplified at that breakpoint
- Motion is subtle and purposeful: gentle drift/float on hero art, animated line-draw on the store-locator section, marquee-style auto-scroll on the review row — never gratuitous or decorative-only

---

## 8. Photography & Product Imagery

Product shots (see `/products`) are high-resolution (3840×2160 source), shot on clean neutral backgrounds, categorized by use-case per variant: Beep-card tap, Card fan-out, Cash slot, Coin organizer, Held-in-hand, Solo/hero shot. Silo Core additionally includes Tracker-feature shots. A "silo-line" set exists for full-lineup/catalogue compositions showing all three variants together.

When placed in layout, product shots are typically:
- Isolated on white or a single flat accent-color background (never busy/textured backgrounds)
- Given a soft drop-shadow when floated over color panels
- Scaled proportionally per variant to read as visually consistent sizes across the lineup (documented in code as per-shot width overrides)

**Fixed-ratio staging (v2 convention):** product and hero imagery sits inside a fixed `aspect-ratio` container (a "stage"), not positioned directly against the viewport. This locks crop and scale so a shot reads identically on desktop, tablet, and phone — the image is sized against its stage, never against the screen. When generating or placing new product imagery, always wrap it in a fixed-ratio stage rather than using raw percentage offsets against the parent section.

---

## 9. Voice (for copy accompanying design work)

Short, direct, benefit-first. Headlines state a function or resolve a friction point (e.g., "Organize your way, make your move") rather than using abstract lifestyle language. Avoid soft/aspirational fashion-brand copy; favor commuter-specific, concrete details (coins, cards, beep cards, RFID, tracking) over generic wallet-brand claims.

---

## 10. Source Files

| Asset | Location |
|---|---|
| Brand guide (full) | `/brand-guide/Modulo - Brand Guide.pdf` |
| Fonts (Neue Haas Grotesk Display, all weights) | `/fonts/` |
| Logo marks (black/white, with/without wordmark) | `/logos/` |
| Product photography | `/products/silo-standard/`, `/silo-femme/`, `/silo-core/`, `/silo-line/` |
| Coded reference (live token source) | `/reference/modulo-landing-page-v2.html` |

This DESIGN.md should be treated as authoritative over the brand guide PDF wherever the two differ, since it reflects the most recently coded and approved implementation.
