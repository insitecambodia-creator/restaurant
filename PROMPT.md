# Restaurant Landing Page — Reusable Design Prompt

A standard template + prompt for building a new restaurant landing page. Keeps
every site consistent in structure and quality, while letting each one look
distinct through its own brand colors, typography accent, and signature
design element.

This file is the reusable spec. `index.html` / `style.min.css` /
`main.min.js` in this repo are a **reference implementation** of it, built
with a fictional demo restaurant ("Ficus & Salt") so the template can be
previewed and duplicated. See `README.md` for how to adapt it to a real
restaurant.

---

## 1. Common data fields (research checklist)

Every restaurant site pulls from the same field set — fill what's confirmed,
mark the rest:

| Field | Notes |
|---|---|
| Restaurant name | |
| Cuisine / concept / positioning | 1-line tagline + 2-3 sentence description |
| Owner / chef / founder | Only if publicly confirmed |
| Full address | |
| Phone number | Click-to-call format |
| Email | |
| Website (if existing) | |
| Opening hours | Day-by-day, note if hours conflict across sources |
| Social handles | Instagram, Facebook, TripAdvisor, etc. |
| Reservation link | e.g. book.bistrochat.com or similar |
| Signature dishes / menu highlights | 4-6 items, no full menu needed |
| Price positioning | $ / $$ / $$$ if inferable |
| Delivery links | Nham24, foodpanda, etc. if applicable |
| Logo / brand colors | Extract if available; else neutral palette |
| Map link | Google Maps URL |

Anything not publicly confirmed is labeled **"Not publicly confirmed"**
on-site (subtly, e.g. in fine print or omitted from hero) and flagged
clearly in the README.

---

## 2. Page structure — hero-heavy, short page

Single page, in this order. Roughly 60% of first-viewport weight goes to the
hero; everything below is scannable in a few scrolls, no filler sections.

1. **Hero** (dense — does most of the work)
   - Restaurant name + tagline
   - One-line cuisine/concept descriptor
   - Key practical facts inline: neighborhood/city, price range, open/closed
     now indicator (optional), primary CTA button
   - Secondary CTA (call / reserve / directions) visible without scrolling
2. **About / Concept** — 2-4 sentences, no more
3. **Signature dishes** — 4-6 items as a compact grid or list, no
   descriptions longer than one line each
4. **Practical info bar** — hours, address, phone, map link, social icons,
   all in one compact block (not spread across sections)
5. **Final CTA band** — reservation/call/WhatsApp, repeated once at the
   bottom

No blog-style long-form sections, no image carousels, no multi-page nav. If
there's a multi-location brand, use tabs or anchor-jump within the same page
rather than separate pages, unless content genuinely exceeds single-page
scope.

---

## 3. Visual design system (neutral default)

**Default neutral palette** (used when no logo/brand colors are available):

- Background: warm off-white `#FAF7F2` or soft charcoal `#1C1B19` (pick per
  venue mood — bistro/day = light, wine bar/night = dark)
- Text: near-black `#22201D` / near-white `#F5F2ED`
- Accent: one muted terracotta, olive, or brass tone — never a saturated
  primary color
- Avoid pure black/white; avoid corporate blue

**When a logo/brand exists:** extract 1-2 dominant colors from it, keep
everything else neutral, and use the brand color only for accents (CTA
buttons, dividers, small details) — never as a full background wash unless
the brand itself is bold.

**Typography:**

- Display/headline: a serif with character (Fraunces, Playfair, or similar)
  for the name/hero
- Body: clean sans (Work Sans, Inter)
- Optional handwritten accent (Caveat) for a tagline or menu highlight, used
  sparingly

**Signature design element:** one recurring motif tied to the venue's
identity — a chalkboard texture, a butcher's stamp, a wine-label border, a
colonial-villa line detail — used once or twice, not repeated everywhere.

**Layout rules:**

- Mobile-first, fully responsive
- Generous whitespace, no dense text blocks
- Original SVG illustrations or CSS-only decorative blocks in place of
  photos when no rights-cleared images exist
- No stock-photo look-alikes, no hotlinked images

---

## 4. The reusable prompt (paste into Claude Code / Claude Design)

```
Build a single-page restaurant website using the research data provided below.

STRUCTURE (in this order, no more sections than this):
1. Hero — name, tagline, one-line concept, city/neighborhood, price range,
   primary CTA (reserve/call) and secondary CTA (directions), all visible
   without scrolling on desktop and mobile.
2. About/Concept — max 4 sentences.
3. Signature dishes — 4-6 items, one line each, no long descriptions.
4. Practical info bar — hours, address, phone, map link, social icons,
   all in one compact block.
5. Final CTA band — repeat reservation/call/WhatsApp CTA.

DESIGN:
- Neutral base palette (warm off-white or soft charcoal background,
  near-black/near-white text) unless brand/logo colors are provided —
  if provided, use 1-2 brand colors as accents only, never full backgrounds.
- Serif display font for name/headlines, clean sans for body, optional
  handwritten accent font for tagline only.
- One signature visual motif reflecting the venue's identity, used once
  or twice — not repeated as wallpaper.
- No stock photos, no hotlinked images. If no rights-cleared photos exist,
  use original SVG illustration(s) or CSS-only decorative blocks instead.
- Mobile-first, fully responsive, generous whitespace, no dense text blocks.

TECHNICAL REQUIREMENTS:
- Plain HTML, CSS, minimal JS only if needed — no frameworks.
- Flat file structure — ALL files in one directory, no subfolders
  (no assets/css/, assets/js/, assets/images/). Required files:
  index.html, style.min.css, main.min.js, [any SVGs], robots.txt,
  sitemap.xml, llms.txt, README.md.
- Minify HTML/CSS/JS for final delivery.
- Full SEO: title tag, meta description, canonical URL placeholder,
  Open Graph + Twitter Card tags, JSON-LD Restaurant schema (name,
  address, phone, hours, cuisine, social links, sameAs).
- robots.txt allowing normal crawling, referencing sitemap.xml.
- llms.txt summarizing the restaurant for AI systems: name, concept,
  cuisine, location, contact, social links, key URLs.
- README.md covering: what's in the folder, unconfirmed/missing info,
  sources used, and step-by-step publishing instructions (domain
  replacement, Cloudflare Pages upload, Search Console submission).
- Add lightweight event-tracking hooks on CTA buttons (phone,
  reservation, directions, WhatsApp, Instagram) as JS data attributes
  or simple function calls, ready to wire into Plausible/Umami later —
  do not add any tracking scripts by default.
- Test hero section styling against global heading color rules before
  delivery (known past bug: global CSS overriding hero-specific colors).

DATA TO USE:
[paste researched fields from the checklist above — mark anything
unconfirmed as "Not publicly confirmed"]
```

---

## 5. How to use this

1. Research a restaurant using the field checklist in Section 1.
2. Paste the prompt from Section 4 into Claude Code (or Claude Design for the
   visual pass), with the researched data filled in at the bottom.
3. Review the output against Section 2's structure and Section 3's palette
   rules before delivery — especially checking the hero renders correctly
   against the CSS reset.
4. Swap in brand colors from the logo if one exists; otherwise keep the
   neutral default.

This keeps every site feeling like part of the same "house style" (short,
hero-forward, clean, SEO-solid, flat-file) while still looking distinct per
venue.
