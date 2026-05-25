# Arch Masonry — Website Redesign

**Live site:** [archmasonry.co.uk](https://www.archmasonry.co.uk)

---

## Overview

Full website redesign for Arch Masonry, a Bristol-based stonemasons company. The project started as a standalone HTML file and was later converted into a custom WordPress theme to replace the client's existing Nicepage/SeedProd-built site.

---

## Phase 1 — HTML Prototype

The initial version was built as a single self-contained `archmasonry.html` file, prototyped and previewed via GitHub Pages.

**What was built:**

- Dark luxury aesthetic — near-black background, gold (`#c8a84b`) accents, Cormorant Garamond + Inter typefaces
- Full-screen hero section with parallax-style background image and animated entrance
- Services section with hover cards (Stone Walling, Stone Cleaning, Restoration, Repointing)
- Before/After gallery with interactive slider — drag to reveal before/after photos for each project
- Testimonials section
- Contact section with form (name, email, phone, message)
- Sticky navigation with smooth scroll and active section highlighting
- Scroll-reveal animations using IntersectionObserver
- Cookie consent banner
- Footer with Privacy Policy and Cookie Policy links
- Fully responsive layout

**Images** were hosted on GitHub (`raw.githubusercontent.com`) for the prototype phase.

---

## Phase 2 — WordPress Conversion

The HTML prototype was converted into a custom WordPress theme to deploy on the client's existing hosting at `archmasonry.co.uk`.

**Theme structure:**

```
archmasonry-theme/
├── style.css          # Theme metadata (required by WordPress)
├── functions.php      # Removes conflicting WP default styles, adds theme support
├── front-page.php     # Main page template — the full redesign
├── index.php          # Fallback template
└── page.php           # Template for subpages (Privacy Policy, Cookie Policy)
```

**What changed during conversion:**

- All images migrated from GitHub to WordPress Media Library (`/wp-content/uploads/2026/05/`)
- `wp_head()` added to `<head>` so WordPress can inject favicon, plugins, and metadata
- `front-page.php` added as dedicated homepage template (takes priority over `index.php` in WP hierarchy)
- `page.php` created for subpages — same dark/gold styling, with logo nav and "Back to Home" link
- Copyright year updated to 2026

**Contact form:** integrated with [Formspree](https://formspree.io) — async fetch submission, loading state on button, error handling, no page redirect on success.

**Pages created in WordPress:**
- `Home New` — assigned as static front page in Settings → Reading
- `Cookie Policy` — slug: `cookie-policy`
- `Privacy Policy` — slug: `privacy-policy`

**Plugins on the site (pre-existing):**
- Nicepage + SeedProd — used for the old site, bypassed by the new theme
- Wordfence + Sucuri — security plugins, no conflicts
- UpdraftPlus — backups

---

## Notes

- The old homepage ("Bristol Stone Masonry") was built in both Nicepage and SeedProd, which overrode any custom theme for that page — solved by creating a new clean page as the front page
- `front-page.php` is required separately from `index.php` because WordPress uses `page.php` for any page set as static front page when only `index.php` exists
- Favicon is pulled from WordPress Site Identity (Appearance → Customize → Site Identity → Site Icon)
