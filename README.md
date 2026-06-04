# TONJA Concept — Website

A fast, hand-built static rebuild of [tonjaconcept.ch](https://www.tonjaconcept.ch), keeping the playful, colourful character (cyan outline wordmark, "love" graffiti art, maximalist colour) — but with none of the Wix weight.

## What's inside
- **Single page**, no framework, no build step — just open `index.html`.
- **All CSS inlined** in `<head>` → one HTML request, no render-blocking stylesheet.
- **Bilingual EN / DE** via a tiny inline script (toggle in the nav). Respects `?lang=en` / `?lang=de`, browser language, and remembers the choice.
- **Responsive WebP images** with `<picture>` + `srcset`, explicit `width`/`height` (zero layout shift), `loading="lazy"`, hero preloaded with `fetchpriority="high"`.
- **Accessible**: semantic landmarks, focus styles, `prefers-reduced-motion`, alt text.
- **SEO**: meta description, Open Graph, JSON-LD `Store` schema, `sitemap.xml`, `robots.txt`.
- **No external requests** — no Google Fonts, no trackers. System font stack styled to match the brand's spaced Helvetica look.

## File map
```
index.html            ← the whole site (markup + CSS + JS)
assets/img/           ← optimised WebP + JPG fallbacks
netlify.toml          ← caching + security headers + forms
vercel.json           ← same, for Vercel
robots.txt, sitemap.xml
```

## Deploy

### Netlify (recommended — the contact + newsletter forms work out of the box)
1. `netlify deploy --prod` (or drag the folder into the Netlify dashboard, or connect the Git repo).
2. Form submissions appear under **Forms** in the Netlify dashboard. Set up an email notification there to forward them to `welcome@tonjaconcept.ch`.

The two forms use **Netlify Forms** (`data-netlify="true"`) — no server code needed.

### Vercel
Works for the site, **but Netlify Forms will not submit on Vercel.** If you deploy to Vercel, swap the two `<form>` actions for a form service such as [Formspree](https://formspree.io) (change `data-netlify="true"` → `action="https://formspree.io/f/XXXX"`). Everything else is identical.

## Local preview
```bash
cd tonja-concept-website
python3 -m http.server 8000
# open http://localhost:8000
```

## Editing notes
- **Brand cyan** = `#43c3f0` (CSS var `--cyan`). All accent colours live in `:root`.
- **Add/edit a store**: copy a `.card` block in the Stores section; the `--c` inline var sets its accent colour.
- **Text** is bilingual: each element carries `data-en` / `data-de` (and `data-en-ph`/`data-de-ph` for input placeholders). Edit both.
- The **About copy** is written on-brand but is placeholder — replace with Tonja's own words when ready.
- Images came from the original site. Swap files in `assets/img/` (keep the same names, or update the `<picture>` blocks).
