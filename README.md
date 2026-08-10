# Moodli

Handmade keychain brand website — 5-page static site (Home, About, Products, Community, Contact).

Moodli ("Mood Little") sells handcrafted keychains inspired by emotions and moments. This site is a static HTML/CSS/JS build with no framework or build step required.

## File structure

```
moodli/
├── index.html        Home — hero, stats counter, brand intro, featured carousel
├── about.html         About — mission/vision/values, team, journey CTA
├── products.html       Products — filterable collection grid, commission banner
├── community.html      Community — testimonials, collabs, Discord, photo gallery, guidelines
├── contact.html         Contact — contact form (Formspree) + social links
├── site.js            Shared JS: nav menu, scroll animations, counter, carousel, filters
└── README.md
```

All five pages load `site.js` — keep it in the same folder as the HTML files or the menu, animations, and filters won't work.

## Tech

- Plain HTML/CSS/JS, no build tools or dependencies to install
- [GSAP](https://gsap.com/) + ScrollTrigger, loaded from cdnjs, power the scroll-reveal animations
- Fonts: Inter (falls back to system sans-serif if not otherwise loaded)
- Images hosted externally on Imgur / Postimg
- Contact form submits via [Formspree](https://formspree.io/)

## Running locally

No server or install needed — just open `index.html` in a browser. Because `site.js` is loaded via `<script src="site.js">`, keep it next to the HTML files (don't rename or move it on its own).

If you want live-reload while editing, any static server works, e.g.:
```
npx serve .
```
or the VS Code "Live Server" extension.

## Deploying

Upload all six files (five `.html` + `site.js`) to the same directory on your host — GitHub Pages, Netlify, a shared host, wherever. No environment variables or config needed.

## Editing common things

- **Colors / branding** — CSS custom properties at the top of each `<style>` block (`--forest-green`, `--pale-cream`, etc.). Each page repeats them, so update all five files if you change a color.
- **Nav links / logo** — in the `<header>` markup, duplicated at the top of every page.
- **Product images** — swap the Imgur URLs in `products.html` (grid) and `index.html` (carousel). Each product card needs a `data-category` of `animals`, `limited`, or `sets` to work with the filter buttons.
- **Stats counter** (Home) — change the `data-target` numbers on the `.counter` elements in `index.html`.
- **Testimonials / gallery / team** — plain HTML blocks in `community.html` and `about.html`; copy an existing card/item and edit the content.
- **Contact form endpoint** — the `action="https://formspree.io/f/..."` attribute on the `<form>` in `contact.html`.
- **Animations** — controlled in `site.js` under the GSAP section. Reveal direction is set per-element via class (`reveal-up`, `reveal-left`, `reveal-right`, `reveal-scale`) in the HTML; grids that should stagger use `data-stagger-group` on the parent.

## Notes

- Site respects `prefers-reduced-motion` — animations are skipped for users with that OS setting enabled.
- Mobile breakpoint is `850px` (nav collapses to hamburger menu below that width).
- No analytics, tracking, or cookies are included by default.
