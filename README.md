# Aetherist Market — Official Website

Official promotional / landing website for **Aetherist Market** — a premium digital products marketplace community hosted on Discord.

> Premium digital products. Instant delivery. 24/7 support.

## Official Links

| Destination | URL |
|---|---|
| 🛒 Shop | https://aetherist-market.mysellauth.com/ |
| 💬 Discord | https://discord.gg/s4m9avEfaC |
| ▶️ YouTube | https://www.youtube.com/@NiksScripts |

**Flagship product:** AetheristTTK — €7.00 — ∞ In Stock

This is a static advertising/landing experience. There is no checkout, cart, backend or payment logic — every CTA funnels visitors to the 3 official destinations above.

## Running the Site

**Open `index.html` directly in any browser.** It just works.

The site is also hosted-friendly (GitHub Pages, Netlify, any static host):

```
# optional local server
python3 -m http.server 8080
# → http://localhost:8080
```

> Live preview: open `index.html`, or deploy via GitHub Pages
> (Settings → Pages → Deploy from a branch → `main` / `/ (root)`).

### A note on JS modules
The site uses classic deferred scripts in namespaced IIFE modules (a `window.AE` namespace) instead of native ES modules. This is deliberate: native ES modules and `fetch()` are blocked on the `file://` protocol, and the site is required to work by double-clicking `index.html`. JSON data files are fetched live on http(s) and transparently fall back to identical embedded data on `file://`.

## File Structure

```
aetherist-market/
├── index.html                  # Main landing page (14 sections)
├── pages/
│   ├── terms.html              # Full Terms of Service + TOC + acceptance modal
│   ├── status.html             # Animated fake-live server status page
│   ├── reviews.html            # Full vouch wall with filters
│   ├── help.html               # Help center / purchase guide
│   └── 404.html                # Animated 404
├── assets/
│   ├── css/
│   │   ├── main.css            # Variables, reset, base styles
│   │   ├── animations.css      # All keyframes & animation utilities
│   │   ├── components.css      # Buttons, cards, nav, modals, badges
│   │   ├── sections.css        # Homepage + subpage section styles
│   │   └── responsive.css      # Mobile-first media queries
│   ├── js/
│   │   ├── app.js              # Main init & orchestrator (data renderers)
│   │   ├── particles.js        # Canvas particle + constellation system
│   │   ├── animations.js       # Reveals, counters, parallax, magnetic, timeline, preloader
│   │   ├── cursor.js           # Custom glowing cursor + trail
│   │   ├── tilt.js             # 3D tilt + glare for cards
│   │   ├── marquee.js          # Infinite ticker/marquee logic
│   │   ├── navbar.js           # Sticky nav, scroll-spy, mobile menu, progress bar
│   │   ├── modal.js            # ToS acceptance modal, product quick-view
│   │   ├── toast.js            # Toast notification system
│   │   ├── typewriter.js       # Typing + glitch text effects
│   │   ├── status.js           # Uptime bars, ping readouts, "last checked"
│   │   ├── faq.js              # Accordion + faq.json loader
│   │   └── theme.js            # Accent switcher (localStorage)
│   ├── data/
│   │   ├── products.json       # Product data (flagship + coming soon)
│   │   ├── faq.json            # FAQ entries (loaded dynamically)
│   │   ├── features.json       # Feature grid data
│   │   └── reviews.json        # Review / vouch wall data
│   └── img/
│       ├── logo.svg            # "A" monogram with animated gradient
│       ├── favicon.svg
│       └── og-image.svg
└── README.md
```

## Customization

### Change the 3 official links
They appear throughout the HTML/JS. Search-and-replace these exact strings:
- `https://aetherist-market.mysellauth.com/` (shop)
- `https://discord.gg/s4m9avEfaC` (discord)
- `https://www.youtube.com/@NiksScripts` (youtube)

`assets/js/app.js` also holds them once in the `LINKS` object (used by rendered cards).

### Change colors
All tokens live in `assets/css/main.css` under `:root` — accents, glows, gradients, radii. Accent presets (purple / cyan / violet) are the `[data-accent="..."]` blocks right below.

### Edit products → `assets/data/products.json`
- First object = the flagship card (name, price, stock, description, buyUrl). Bound to the hero product card + quick-view modal at runtime.
- Extra objects render as locked "coming soon" cards.
- On `file://`, identical fallback data inside `assets/js/app.js` is used — keep both in sync if you edit offline.

### Edit FAQs → `assets/data/faq.json`
Array of `{ "q": "...", "a": "..." }`. Loaded dynamically by `assets/js/faq.js` (with the same file:// fallback embedded in that file).

### Edit the vouch wall → `assets/data/reviews.json`
Array of `{ "user", "stars" (1-5), "verified" (bool), "date", "text" }`. Drives the homepage auto-scrolling wall and the filterable reviews page.

### Edit features → `assets/data/features.json`
Array of `{ "icon", "title", "text" }` (+ optional `"wide": true` and `"marquee": "..."` for a full-width card with a mini ticker). Icon names map to the `ICONS` map in `assets/js/app.js`.

### Toggle animations
All keyframes are in `assets/css/animations.css`. Heavy effects auto-disable for users with `prefers-reduced-motion: reduce` and on touch devices.

## Feature Checklist

- 28/28 animations implemented (preloader draw, custom cursor, particle constellations, aurora blobs, gradient shimmer, RGB-split glitch, typewriter, magnetic buttons, shine sweep, 3D tilt + glare, idle float, marquees, staggered reveals, parallax, counters, scroll progress, scroll-spy, pulse dots, SVG path drawing, accordion, toasts, modals, conic glow borders, uptime bars, neon flicker, back-to-top ring, mobile menu stagger, smooth anchors)
- Fully responsive: 360 / 768 / 1024 / 1440+ breakpoints
- Semantic HTML5, ARIA labels, keyboard focus styles
- `prefers-reduced-motion` respected
- All internal links relative (GitHub Pages ready)
- All external CTAs: `target="_blank" rel="noopener noreferrer"`

## Git & GitHub Pages

The repo ships with git initialized and an initial commit on `main`. Add your remote and push:

```bash
git remote add origin https://github.com/<user>/aetherist-market.git
git push -u origin main
```

Then enable Pages: **Settings → Pages → Build and deployment → Source: "Deploy from a branch" → Branch: `main`, Folder: `/ (root)` → Save.**
Site goes live at `https://<user>.github.io/aetherist-market/`.

---

© 2025 Aetherist Market — Not affiliated with Discord Inc.
