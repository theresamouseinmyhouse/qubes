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
| `PRINT_AND_PLAY_PDF_URL` | Print-and-play rulebook PDF link |
| `CUBE_TEMPLATE_URL` | Cube template / dice-sticker guide link |
| `CONTACT_EMAIL` | Your email (appears twice: in `mailto:` and the visible text) |
| `SITE_URL` | Done: `https://theresamouseinmyhouse.github.io/qubes`. If the repo is renamed, update the `og:image` URL in `index.html`. |
| `[LOCATION / AVAILABILITY]` | Where and when in-person sessions happen |
| `[FREE / THANK-YOU GIFT]` | Whether it's free, or what testers get |
| `[YOUR NAME]` | Your name, for the footer |

When you replace a bracketed placeholder, you can also drop its `<span class="todo">` wrapper.

**Cubes photo:** add `assets/cubes.png` (about 1200px wide, compressed), then swap the dashed placeholder box in the "What is QUBES?" section for the `<img>` tag given in the TODO comment above it.

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
