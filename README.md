# Overheal — Website

The marketing + support site for **Overheal**, a gamified nutrition app for iPhone.
Served via GitHub Pages at https://vishnuumanikandan.github.io/HealthbarSupportWebsite/

## Structure

Static, no build step. All pages are at the repo root (GitHub Pages serves root) and
share one stylesheet. Every internal link is relative so it works under the Pages subpath.

| File | Purpose |
|------|---------|
| `index.html` | Landing page — hero, features, ranks ladder, FAQ, download CTA |
| `support.html` | Help & FAQ + contact (`support@overheal.app`) |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service (template — see note below) |
| `styles.css` | Shared theme (dark default, light toggle) |
| `app-icon.png` | The Overheal app icon (favicon, nav mark, OG image) |
| `docs/website-design.md` | Design spec for this site |

The rank emblems on the landing page are the **real in-app rank plaques** (Stone → Zenith),
defined once as SVG `<symbol>`s in `index.html` and reused via `<use>`.

## Before launch — TODO

- **App Store link:** the download buttons point at `href="#"` (search `TODO` in `index.html`).
  Swap in the real App Store URL once the app is live.
- **Terms of Service:** `terms.html` is a template flagged for legal review — have an
  attorney tailor it to your jurisdiction before relying on it.
- **Custom domain (optional):** the site currently lives on github.io. `overheal.app` is used
  only as the support email domain; add a `CNAME` file + update the canonical/OG URLs if you
  point a custom domain here later.

## Local preview

Open `index.html` in a browser, or run a static server from the repo root:

```
python3 -m http.server 8000
```
