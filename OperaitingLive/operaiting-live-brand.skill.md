---
name: operaiting-live-brand
description: "Brand & design system for OPER(AI)TING LIVE — the live AI masterclass by John Brewton (Operating & 6AEP) and Wessal Khader (Unfazed Founder). Use for any landing page, registration, thank-you, email, slide, or social asset for OPER(AI)TING LIVE. A cinematic, dark, premium system: warm espresso-taupe ground, electric Signal-Yellow gold accent, liquid-glass surfaces, Playfair Display + Inter. Aligned with (and a sibling to) the John Brewton personal brand — same typefaces, warm dark surfaces, never black, never green. Triggers: 'Oper(AI)ting Live', 'OperAIting brand', 'masterclass landing page', 'liquid glass', 'Signal Yellow', 'espresso-taupe', 'thank-you page'."
---

# OPER(AI)TING LIVE — Brand & Design System

A cinematic, dark-mode-first design language for OPER(AI)TING LIVE, a complimentary one-time live masterclass. It evolves the John Brewton personal brand (warm surfaces, electric yellow, Playfair + Inter) into a premium, screen-lit "operator" aesthetic: a warm espresso-taupe ground, an emissive gold accent, and liquid-glass surfaces.

Read every section before producing output. The system holds together because color, type, spacing, and decoration follow strict rules.

## Quick Reference — The Rules

1. **Two typefaces only.** Playfair Display (display/headlines/numerals) + Inter (body, labels, UI, eyebrows). No third face.
2. **Never pure black. Never green.** The dark ground is a warm espresso-taupe (`#221A13`), nudged toward the personal-brand Deep Taupe family. Avoid `#000` surfaces and any forest/emerald greens.
3. **One accent: Signal-Yellow gold (`#F4ED5B`).** It is the operator's signal — CTAs, eyebrows, numerals, rule accents, glows. Used as a gradient to gold-deep (`#D8C73F`) for emissive moments.
4. **Liquid glass is the signature surface.** Translucent fill + 1px luminous stroke + inner top highlight + a slow specular sheen. Rounded corners and soft shadows are allowed (this system is cinematic, not the flat editorial register).
5. **Whole-line emphasis only.** When highlighting a headline, color the entire line (gold gradient), never partial words.
6. **Generous, intentional space.** 8px base unit. Big sections breathe; conversion moments (thank-you steps) tighten.
7. **Mobile-first.** Every effect is scroll/tap-driven, not hover-dependent, and respects `prefers-reduced-motion`.
8. **Single-file, production-clean.** One HTML file (Kajabi-ready), CSS in `<style>`, minimal inline JS, CDN fonts only. No build step. No comments left in production output.

---

## Color System

```
/* Dark ground (warm espresso-taupe — never black, never green) */
--ink:        #221A13   /* page ground */
--ink-2:      #2D2218   /* raised panels, stat tiles */
--ink-3:      #36291E   /* cards */
--espresso:   #2B231F   /* mid surface */
--warmsmoke:  #3A302A   /* warm divider ground */

/* Light family (text on dark) */
--bone:       #F4EFE6   /* primary text */
--bone-soft:  #E9E2D5
--linen:      #D9D0BF   /* secondary text */
--taupe:      #A99C8C   /* tertiary / labels */
--stone:      #8A7E70   /* captions, metadata, legal ONLY */

/* Accent + metals + sparks */
--gold:       #F4ED5B   /* primary accent (Signal Yellow), CTAs, numerals, glow */
--gold-deep:  #D8C73F   /* gradient stop / pressed */
--champagne:  #E8D9A8   /* fine metallic lines, tag text */
--cinder:     #C25A26   /* warm spark — data-viz line art only */
--ash:        #6E92B8   /* cool spark — data-viz line art only */
```

**Usage rules**
- Gold is the only accent. Never introduce a second hue as an accent.
- Cinder and ash appear only in background SVG line art (spark lines, contour rings), never as text or fills behind copy.
- `--stone` is for captions, metadata, and the legal/disclaimer block only — never primary paragraph text.
- Body text on dark uses `--linen`; primary headings/important text use `--bone`.

**Gradients & ambient**
```
--grad-gold: linear-gradient(135deg, #F4ED5B 0%, #D8C73F 100%);
--halo-gold: radial-gradient(60% 60% at 50% 30%, rgba(244,237,91,.16) 0%, rgba(244,237,91,0) 60%);
```

**Contrast (targets: WCAG AA+; AAA where possible)**
- Bone on ink ≈ 13:1 · Linen on ink ≈ 10:1 · Gold on ink ≈ 12:1 · Ink (`#1A1604`) on gold buttons ≈ 12:1.

---

## Typography

Two faces. Loaded from Google Fonts.

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;0,800;0,900;1,400;1,600&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

- **Playfair Display** — display headlines (h1–h3), pull quotes, and all numeric figures (prices, dates, stat counters, the odometer, the "01/02/03" step/card numbers). Weight 600 for headings; 700 for numerals.
- **Inter** — body copy, leads, labels, eyebrows, buttons, tags, captions, the legal block. Eyebrows/labels are uppercase with wide tracking.

**Fluid scale (clamped, mobile-first)**
```
--fs-h1:    clamp(2.1rem, 7vw, 4.6rem)
--fs-h2:    clamp(1.7rem, 5.2vw, 3.1rem)
--fs-h3:    clamp(1.25rem, 3.2vw, 1.85rem)
--fs-lead:  clamp(1.05rem, 2.3vw, 1.28rem)
--fs-body:  clamp(1rem, 1.6vw, 1.0625rem)
--fs-label: 0.6875rem            /* eyebrow */
```

**Type rules**
- Headlines: `font-weight:600; line-height:1.06; letter-spacing:-.02em`.
- Eyebrows: Inter 600, `letter-spacing:.22em`, uppercase, gold, with a 22px gold rule before the text.
- Headline titles avoid trailing periods unless restoring verbatim legal/marketing copy.
- Highlight whole lines with `--grad-gold` via `background-clip:text` (`.hl-line`), never partial words.

---

## Spacing, Radii, Motion

```
/* 8px base */
--sp-4:16  --sp-5:24  --sp-6:32  --sp-7:48  --sp-8:64  --sp-9:96  --sp-10:128
--r-sm:10  --r-md:16  --r-lg:22  --r-xl:30  --r-pill:999
--ease-cine: cubic-bezier(.16,1,.3,1)   /* one signature curve for everything */
--t-fast:.25s  --t-med:.45s  --t-slow:.7s
--wrap:1180px  --gutter:clamp(20px,5vw,40px)
```
- Editorial sections use `--sp-9` block padding; conversion-critical sections (thank-you action steps) tighten to `--sp-7`/`--sp-6` so the action sits near the fold.
- One easing curve (`--ease-cine`) governs all transitions.

---

## Liquid Glass (signature surface)

```css
.glass{
  position:relative; background:rgba(244,239,230,.045);
  backdrop-filter:blur(18px) saturate(140%); -webkit-backdrop-filter:blur(18px) saturate(140%);
  border:1px solid rgba(244,239,230,.12); border-radius:var(--r-lg);
  box-shadow:inset 0 1px 0 rgba(255,255,255,.10), 0 24px 60px -28px rgba(0,0,0,.7); overflow:hidden;
}
/* slow specular sheen — the "liquid" tell */
.glass::after{
  content:""; position:absolute; inset:0; pointer-events:none; border-radius:inherit; z-index:1;
  background:linear-gradient(115deg,transparent 30%,rgba(255,255,255,.06) 45%,transparent 60%);
  transform:translateX(-30%); animation:glassSheen 7s var(--ease-cine) infinite;
}
@keyframes glassSheen{0%{transform:translateX(-60%)}55%,100%{transform:translateX(60%)}}
.glass--bright{border-color:rgba(244,237,91,.30); background:rgba(244,239,230,.07)} /* active / featured */
```
Tiers: base glass (panels, cards), bright glass (featured/selected), and emissive glass (the single primary CTA moment — add a gold radial bleed behind it).

---

## Motion Language

- **Scroll reveal:** content rises 28–30px and fades in on entry. Implemented with CSS scroll-driven animation (`@supports (animation-timeline: view())`) so it needs no JS and degrades to visible.
- **Liquid sheen:** the slow specular streak above.
- **Cursor glow (desktop only):** a soft gold radial follows the pointer (`@media (hover:hover)`).
- **Magnetic CTAs (desktop):** primary buttons drift toward the cursor and snap back.
- **Spotlight cards:** a gold radial glow tracks the pointer across each card; a top-illumination glow on speaker cards.
- **Odometer:** numeric stats roll into place on scroll-in (measure digit height with `getBoundingClientRect()` to avoid sub-pixel drift).
- **Sticky card stack:** asymmetric two-column block where cards pin and fan out at ±12°.
- **Kinetic marquee:** a slow credential/value strip; pauses on hover.
- All motion is wrapped in `@media (prefers-reduced-motion:no-preference)` or guarded in JS; everything has a static fallback.

---

## Components

- **Sticky nav** — pinned to the top of the hero; transparent over the hero, solidifies on scroll. Logo `Oper(AI)ting` + small `LIVE` pill. On secondary pages (thank-you), the logo is centered and there is no CTA.
- **Hero** — CSS mesh-gradient blobs + gold halo + SVG spark lines behind a centered stack: gold eyebrow/badge, Playfair h1 (concise, whole-line gold highlight), Inter lead, and a **date/time card** (Date · Time `ET | PT` · Length).
- **Date/time card (`.when-card`)** — glass pill split into cells; date spelled out ("June 16"); times combined with a faint pipe.
- **Value cards / sticky stack** — number lives in an enlarged gold icon box; titles in Playfair; on desktop a 2-column asymmetric sticky stack with ±12° tilt.
- **Comparison** — two-column "hard way vs OPER(AI)TING LIVE" rows with ✕ (cinder) / ✓ (gold).
- **Speaker cards** — glass cards with real photos, name (Playfair), role (gold, uppercase, one line), bio, compact stat pills (don't stretch full width on desktop), and small champagne tag pills. Top-illumination glow on hover.
- **Bonuses (bento)** — asymmetric grid of varied-width glass cards; label + name + description + value; a gold "total value" tile.
- **Offer card** — emissive bright-glass with `$0` price, struck value, checklist, and the primary CTA.
- **FAQ** — native `<details>/<summary>`, gold number + Playfair question + rotating `+` toggle. Mirror into FAQPage JSON-LD for AEO.
- **Footer** — Playfair wordmark `Oper(AI)ting Live`, an Inter people line (`John Brewton · Operating & 6AEP · Wessal Khader · Unfazed Founder™`), a tiny (8px) legal/disclaimer box, and a 10px centered copyright line.
- **CTAs** — pill buttons; primary = gold gradient with dark text (`#1A1604`) and gold glow; ghost = glass.

---

## Voice & Naming

- **Brand name:** always **Oper(AI)ting Live** (stylized with the `(AI)`), uppercase `OPER(AI)TING LIVE` in wordmarks/titles. Never "Operaite" or plain "Operating Live".
- **Companies:** combine as **"Operating & 6AEP"** (John) and **"Unfazed Founder™"** (Wessal). Add ™ to Unfazed Founder; 6AEP carries no ™.
- **Tone:** declarative, operator-grade, economical, no hype. The bonus product name "The Oper(AI)tor's Audit" keeps its `(AI)`.
- **Speakers:** John Brewton (Founder · Operating & 6AEP) and Wessal Khader (Founder and CEO · Unfazed Founder™).

---

## Production & SEO Standards

- **One self-contained HTML file** per page (Kajabi drop-in). CSS in `<style>`, minimal inline JS, fonts via CDN, images inline as data URIs where practical. No external `.js`/`.css`.
- **No comments in production** — strip all HTML and CSS/JS comments before shipping.
- **Indexable pages** (landing): set `<link rel="canonical">`, `<meta name="robots" content="index, follow, max-image-preview:large">`, full Open Graph + Twitter Card, `theme-color: #221A13`, and JSON-LD (`Event` + `FAQPage`) for search and answer engines.
- **Transactional pages** (thank-you): `<meta name="robots" content="noindex, follow">`, still ship Open Graph for shared links.
- **Accessibility:** semantic headings (one h1), `aria-hidden` on decorative layers, focus-visible gold outlines, and reduced-motion fallbacks.

---

## Anti-Patterns (Never Do)

Pure-black surfaces. Forest/emerald greens. A second accent color. Partial-word highlights. A third typeface. Cinder/ash as text or content backgrounds. `--stone` for body copy. Hover-only interactions with no touch/scroll fallback. Multiple competing glows on one element. Comments left in shipped HTML. The "Operaite" or plain "Operating Live" rendering of the brand name.
