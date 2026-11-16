# QUBES playtest site

A one-page static site that recruits playtesters for **QUBES**, a kids-first tabletop storytelling game. It's plain HTML and CSS: no build step, no JavaScript, no trackers.

```
index.html        the page
style.css         all styles (colours are tokens at the top)
assets/           logo, symbols, favicon, link-preview image, fonts
assets/fonts/     Fredoka + Nunito (SIL Open Font License, see OFL-*.txt)
```

## Filling in the placeholders

Open `index.html` and search for each token below. The full list is also in a comment at the top of the file. Until you replace them, unfilled links show a yellow **TODO** tag on the page and bracketed text shows in a dashed yellow box.

| Token | Replace with |
|---|---|
| `SIGNUP_FORM_URL` | Done: `https://forms.gle/jYykqNi9DFmof7pL7` |
| `FEEDBACK_FORM_URL` | Post-session feedback form link |
| `PRINT_AND_PLAY_PDF_URL` | Done: `downloads/qubes-print-and-play-{letter,a4}.pdf`, built from `rules/` (see below). |
| `CUBE_TEMPLATE_URL` | Done: `downloads/qubes-spinners-{letter,a4}.pdf` (the last two rulebook pages). |
| `CONTACT_EMAIL` | Done: `hello@qubesgame.com`, forwarded by Cloudflare Email Routing. |
| `SITE_URL` | Done: `https://qubesgame.com` (custom domain, set by the `CNAME` file; DNS in Cloudflare). |
| `[LOCATION / AVAILABILITY]` | Where and when in-person sessions happen |
| `[FREE / THANK-YOU GIFT]` | Whether it's free, or what testers get |
| `[YOUR NAME]` | Your name, for the footer |

When you replace a bracketed placeholder, you can also drop its `<span class="todo">` wrapper.

**Cubes photo:** `assets/cubes.jpg` (1200px wide, metadata stripped). Replace the file to change it, and keep the `width`/`height` in `index.html` matching.

## Print & Play rulebook (`rules/`)

Three editions, all built from the same text: `rules/compact.html` (8 pages plus a spinner sheet, the main download), `rules/index.html` (full size, 22 pages), and `rules/index.html?2up` (the full pages two per landscape sheet, without the spinner pages).

`rules/index.html` is a print-friendly copy of the rulebook for remote playtesters, rewritten for paper spinners instead of cubes and stickers. **The Figma file is the master copy.** When the Figma rules change, update `rules/index.html` and `rules/compact.html` to match. `rules/SPINNER-CHANGES.md` lists every place the spinner edition differs from Figma.

Each `<section class="page">` is one printed page, sized to fit both Letter and A4. After editing, rebuild the PDFs in `downloads/` (compact, 2-up, full and spinners-only, each in Letter and A4) by printing `rules/` from Chrome, or with any headless-Chrome PDF script. Check that every page still fits on one sheet.

The page is `noindex` and is linked only from the "Playing remotely?" section, so the home page stays spoiler-free.

## Previewing locally

```
python -m http.server 8000
```
Then open http://localhost:8000.

## Publishing on GitHub Pages

1. Create an empty repository on GitHub.
2. `git remote add origin https://github.com/<user>/<repo>.git` then `git push -u origin main`.
3. On GitHub: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save**.
4. After a minute the site is live at `https://<user>.github.io/<repo>/`. Put that address in place of `SITE_URL`.
