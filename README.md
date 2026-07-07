# La Ferme de Bassac — Landing Page

A flat-file, single-page landing site for La Ferme de Bassac (French farm
butcher shop, charcuterie and bistro/steakhouse, Phnom Penh &amp; Siem Reap),
built from `PROMPT.md`, the reusable restaurant-landing-page spec in this
repo. Plain HTML/CSS/JS, no frameworks, no build step.

**This is an independent build, not the restaurant's official site.** Their
real, live website is **https://lafermedebassac.com/** — treat this repo as
an alternative/redesign landing page, and update the canonical/OG URLs
(currently a placeholder `lafermedebassac.example` domain) to wherever it
actually gets deployed before publishing.

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The page: hero, concept, signature dishes, a 3-location tab panel (Bistro & Butcher / Steak House / Butcher Depot), follow block, final CTA. Kept human-readable for editability; run an HTML minifier at publish time for a byte-minimal artifact. |
| `style.min.css` | All styles, minified. Warm off-white background, oxblood/rust accent, `--accent`/`--accent-dark` CSS vars for easy re-theming. |
| `main.min.js` | Per-location open/closed status (computed against Cambodia time, `Asia/Bangkok`, not the visitor's device clock) + CTA click-tracking hooks. |
| `motif-butcher-stamp.svg` | Signature visual motif: an original circular butcher/quality-stamp mark, used once in the hero. **Not the restaurant's real logo** — no official logo file was publicly available. |
| `favicon.svg` | Site icon, matches the stamp motif. |
| `robots.txt` / `sitemap.xml` | Crawl config. |
| `llms.txt` | Plain-language business summary for AI/LLM crawlers. |
| `PROMPT.md` | The reusable design brief/checklist — unchanged, for building the next restaurant site. |

## Data sources & confirmation status

Confirmed by direct research request:
- Concept, founding year, EU-standard/no-hormone farming, ~45 min farm distance, all three addresses, phone numbers, and hours — as provided.
- Founder/chef Ludovic Moulin, formerly personal chef to the French Ambassador to Cambodia, founded 2011 — cross-checked against `lafermedebassac.com/histoire.html` and third-party coverage (Phnom Penh Post).
- 4.9/5 rating from 82 Google reviews — as published on the restaurant's own website; **not independently re-verified against live Google review data**, and displayed with that caveat in the page's fine print.

Found via web search, used with lower confidence:
- Official website: `https://lafermedebassac.com/index-en.html`.
- Facebook, Phnom Penh: `https://www.facebook.com/fermedebassac/` (high confidence — consistently referenced as the main page).
- Facebook, Siem Reap: `https://www.facebook.com/p/The-Butchers-Choice-by-La-Ferme-De-Bassac-61559890532848/` — could not confirm whether this maps to the Steak House, the Butcher Depot, or covers both; the page currently links it once and flags the ambiguity in the fine print rather than guessing.

**Not publicly confirmed** (per the original research, and not fabricated here):
- Email address — omitted from the page entirely rather than guessed.
- Exact menu prices — the site shows dish names only, no price positioning ($/$$/$$$) is claimed.
- Online reservation or delivery links — the page directs every CTA to phone calls instead.
- Official logo file — `motif-butcher-stamp.svg` is an original mark inspired by the "butcher's stamp" motif suggested in `PROMPT.md`, not the restaurant's real branding.

## Editing

- Location data lives in `index.html` inside each `.tab-panel` (address, phone, map link) and its `data-hours` JSON attribute (used by `main.min.js` for the live open/closed dot) — keep both in sync if hours change.
- JSON-LD in `<head>` mirrors the same three locations as a `@graph` of `Restaurant`/`Store` entries.
- Re-theme via the CSS custom properties at the top of `style.min.css` (`--accent`, `--accent-dark`, `--bg`, etc.) if a real logo/brand palette becomes available later, per `PROMPT.md` §3.

## Publishing (Cloudflare Pages)

1. Decide on and swap in the real deployment domain across `index.html` (canonical, OG, Twitter, JSON-LD `url` fields), `robots.txt`, `sitemap.xml`, and `llms.txt`.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Upload assets**, and upload every file in this folder (flat, no subfolders).
3. Attach the custom domain under **Custom domains** and update DNS as prompted.
4. Submit `sitemap.xml` in **Google Search Console** and request indexing for the homepage.
5. Validate Open Graph output with a link-preview debugger and the JSON-LD with Google's Rich Results Test before announcing the site.
6. Resolve the Siem Reap Facebook page ambiguity above (confirm which physical location "The Butcher's Choice by La Ferme De Bassac" page belongs to, and whether a distinct third page exists) before treating the follow links as final.
