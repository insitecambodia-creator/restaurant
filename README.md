# Restaurant Landing Page Template

A flat-file, single-page restaurant website template: plain HTML/CSS/JS, no
frameworks, no build step. This repo doubles as:

1. **The reusable spec** — `PROMPT.md` — the design brief to paste into
   Claude Code / Claude Design for any new restaurant.
2. **A reference implementation** of that spec, built for a fictional demo
   restaurant, **Ficus & Salt**, so the template can be previewed and
   duplicated as a starting point.

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The page (hero, about, dishes, info bar, final CTA). Kept human-readable for editability; minify it with any HTML minifier at publish time if you want a byte-minimal artifact. |
| `style.min.css` | All styles, minified. |
| `main.min.js` | Open/closed indicator + CTA click-tracking hooks, minified. |
| `motif-olive-branch.svg` | The signature visual motif (an olive-branch line drawing, used once in the hero). |
| `favicon.svg` | Site icon. |
| `robots.txt` | Allows crawling, points at `sitemap.xml`. |
| `sitemap.xml` | Single-URL sitemap. |
| `llms.txt` | Plain-language summary of the business for AI/LLM crawlers. |
| `PROMPT.md` | The reusable design brief/checklist for building the next restaurant site from scratch. |

## Demo data — not a real restaurant

"Ficus & Salt," its address, phone number, email, hours, and social handles
are **fictional placeholder data** invented to demonstrate the template
(domain uses the reserved `.example` TLD on purpose). Nothing here should be
published as-is. Chef/ownership identity and delivery-platform availability
are marked "not publicly confirmed" in the footer and `llms.txt`, mirroring
how a real project should flag unverified research.

## Using this as a template for a real restaurant

1. Research the target restaurant using the checklist in `PROMPT.md` §1.
2. Replace every piece of demo data: JSON-LD block, hero copy, dish list,
   hours object in `main.min.js` (`HOURS`), info-bar contacts, `llms.txt`,
   `sitemap.xml`/`robots.txt` domain, and the `og:`/`twitter:`/canonical
   URLs in `<head>`.
3. If the restaurant has a logo/brand colors, swap the CSS custom properties
   in `style.min.css` (`--bg`, `--olive`, `--olive-dark`, etc.) — keep brand
   color as an accent only, per `PROMPT.md` §3. Otherwise keep the neutral
   palette as-is.
4. Swap the motif SVG for one that fits the new venue's identity if the
   olive branch doesn't suit it (chalkboard texture, wine-label border,
   butcher's stamp, etc. — see `PROMPT.md` §3).
5. Re-check the hero heading color renders correctly (`.hero h1` in
   `style.min.css` is deliberately set with `!important` and a comment
   explaining why — a past bug let a later global heading-color rule
   silently override it).
6. Wire `window.trackEvent` in `main.min.js` to Plausible/Umami if desired
   (it's a no-op console log by default).

## Publishing (Cloudflare Pages)

1. Replace all `ficusandsalt.example` references with the real domain
   across `index.html`, `robots.txt`, `sitemap.xml`, and `llms.txt`.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Upload
   assets**, and upload every file in this folder (flat, no subfolders).
3. Attach the custom domain under **Custom domains** once the project is
   created, and update DNS (Cloudflare will prompt for a CNAME/A record if
   the domain isn't already on Cloudflare).
4. Submit the live sitemap in **Google Search Console** (Search Console →
   Sitemaps → add `sitemap.xml`) and request indexing for the homepage URL.
5. Verify Open Graph output with a link-preview debugger and confirm the
   JSON-LD block validates (e.g. Google's Rich Results Test) before
   announcing the site.

## Sources

None — this reference build uses invented demo data, not research on an
actual business. When this template is filled in for a real restaurant,
list the sources used for each data field here (official website, Google
Business Profile, Instagram bio, etc.) per `PROMPT.md` §1.
