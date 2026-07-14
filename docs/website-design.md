# Overheal Website — Design Spec

**Date:** 2026-07-13
**Repo (deploy target):** `github.com/vishnuumanikandan/HealthbarSupportWebsite`
**Local clone:** `/Users/vishnumanikandan/Desktop/repos/HealthBar_Support_Website` (branch `main`)
**Live URL:** https://vishnuumanikandan.github.io/HealthbarSupportWebsite/ (GitHub Pages, legacy build, source = `main` root, no custom domain)

## Goal
Turn the provided single-file landing page into a real, multi-page Overheal website that
(a) features the **real app icon**, (b) uses the **real in-app rank plaques**, and
(c) absorbs the existing HealthBar support site (FAQ, Privacy, Contact), rebranded to Overheal.

## Source assets (ground truth)
- **App icon:** `HealthBar_Support_Website/download.png` (1024×1024) → copied to `app-icon.png`.
- **Rank plaques:** `HealthBar/design/erewhon/rank-plaques.html` — exact SVGs for all 9 ranks
  (Stone, Copper, Iron, Gold, Platinum, Diamond, Sentinel, Prismatic, Zenith). These are the
  ground truth the SwiftUI `RankPlaque` is traced from. The "live accent" `#4882FF` in those
  SVGs is used as a fixed blue, which matches the site theme.
- **Support content:** current live support site (FAQ, Privacy Policy, Contact) — rebranded +
  modernized to the real app behavior.

## File layout (all at repo root — Pages serves root; every link is RELATIVE)
| File | Purpose |
|------|---------|
| `index.html` | Landing page (provided HTML), upgraded per below |
| `privacy.html` | Privacy Policy — real disclosures, rebranded to Overheal |
| `support.html` | FAQ + Contact — modernized to the real app |
| `terms.html` | Terms of Service — standard template, **flagged for legal review** |
| `styles.css` | Shared theme, extracted once from the inline `<style>`; linked by all pages |
| `app-icon.png` | The real icon (copy of `download.png`) |
| `README.md` | Short note on structure + how to deploy |
| `download.png` | (existing untracked file) removed/renamed to `app-icon.png` |

Shared nav + footer markup is duplicated verbatim across the 4 pages (static site, no build step),
all pointing at the shared `styles.css`.

## Changes to `index.html`
1. **Rank icons:** replace every generic `#gem` / `#ph` gem usage with the real plaque SVGs:
   - Ranks ladder (all 9) → real plaques with correct per-rank hexagon fill/rim/emblem.
   - Hero phone `.plaque` "Gold III" → real Gold plaque.
   - Hero floating `.f-rank` chip → real Gold plaque (small).
   - "How it works" step 3 → a real plaque (Zenith, the aspirational apex).
2. **App icon:** favicon → `app-icon.png`; nav brand mark + footer brand mark + founder
   avatar → the icon; OG/Twitter image → `app-icon.png`.
3. **Branding/SEO:** canonical + `og:url` → the github.io URL; `og:image`/`twitter:image`
   → `app-icon.png` (1024×1024, dims updated); keep `overheal.app` only as the email domain
   and a future-domain reference. Contact email everywhere → `support@overheal.app`.
4. **App Store buttons:** point at a clearly-commented placeholder `#` (easy one-line swap
   when the app is live). No fake store URL.
5. **Nav:** add links to Support / Privacy pages (FAQ + How-it-works stay as on-page anchors).

## `support.html` (FAQ + Contact)
FAQ rewritten to match the **real** app (not the stale "Initiate/Warrior/Champion" copy):
- Logging: photo / describe / barcode (AI fills calories + macros).
- XP & levels vs. **RR-driven 9-rank ladder** (Stone→Zenith) — kept accurate to the app
  (XP drives level; rank derives from ranked rating, not XP).
- Purity Score (daily eating quality, 0–100).
- Calorie goals via Mifflin–St Jeor + activity factor.
- Edit/delete meals; Streak + weekly Streak Shield; guest mode; duels & guilds; offline sync.
- Contact block: `support@overheal.app`, ~1 business day response.

## `privacy.html`
Your real, accurate disclosures, rebranded to Overheal — kept faithful:
- Data collected (email via Firebase Auth, food logs, health profile, anonymized diagnostics).
- Third parties: Firebase (Google), Anthropic Claude API (anonymized nutrition summaries only,
  no PII), Open Food Facts (anonymous barcode lookups).
- TLS in transit + encryption at rest; retention + 30-day deletion; 13+; contact.
- `Last updated: 2026-07-13`.

## `terms.html`
Standard, readable Terms of Service template (eligibility 13+, license, acceptable use,
health-disclaimer "not medical advice", accounts, IP, disclaimers/liability, changes, contact).
**Explicitly flagged in-page and to the user as a template to review, not legal advice.**

## Deployment
Work in the local clone; commit on a branch; push; open a PR (per close-out convention —
do NOT merge without explicit go-ahead). Merging `main` auto-publishes via Pages.

## Out of scope / flagged
- Real App Store URL (placeholder until launch).
- Custom domain / `overheal.app` DNS (email domain only for now).
- Terms of Service legal review (template only).
- A bespoke 1200×630 OG share image (using the square icon for now).
