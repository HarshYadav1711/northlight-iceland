# NorthLight Iceland

A static travel guide to Iceland — destination write-ups, activity notes, planning basics, a photo gallery, and a contact form. HTML and CSS only; no build step or JavaScript.

## Overview

The site covers five regions, five common activities, and practical topics (timing, transport, budget, safety, packing). Content pages share the same header, footer, and stylesheet. Photographs load from the Unsplash CDN at runtime.

## Features

### Destination Discovery

* Reykjavík
* The Golden Circle
* South Coast
* Akureyri
* Westfjords

Each destination page section includes drive times, suggested stay length, and links to related activities.

### Experiences

* Northern Lights viewing
* Glacier hiking
* Whale watching
* Geothermal hot springs
* Ice cave exploration

Seasonal availability is summarised in a comparison table on the Experiences page.

### Travel Planning Resources

* Best times to visit
* Transportation guidance
* Budget considerations
* Safety recommendations
* Packing suggestions

### Gallery

Ten photographs with captions, grouped on a single grid page.

### Feedback Form

The contact page collects name, email, destination interest, travel season, and message. Submitting redirects to `thank-you.html` — a demo flow with no server-side processing.

## Design Principles

### Clarity

Logical page sections, breadcrumbs on inner pages, and in-page jump links on longer guides (Destinations, Experiences, Travel Guide).

### Accessibility

Built to WCAG 2.1 AA where achievable without JavaScript:

* Skip link to main content
* Semantic landmarks (`header`, `nav`, `main`, `footer`, `aside`)
* One `<h1>` per page; tables use `<caption>` and `scope`
* Descriptive `alt` text on all images; visible `:focus-visible` rings
* Form fields paired with labels and hint text (`aria-describedby`)
* `aria-current="page"` on active navigation links
* CSS-only mobile menu (checkbox toggle) — see limitations below
* `prefers-reduced-motion` honoured for nav animation and form transitions

**Known limitation:** the mobile menu toggle does not update `aria-expanded` without JavaScript. Details in `docs/production-review.md`.

### Responsiveness

Single-column layout on small screens; two- and three-column grids from 600px and 900px breakpoints. Tables scroll horizontally inside `.table-wrap` on narrow viewports.

### Performance

No JavaScript and no CSS frameworks. Typography from Google Fonts (Montserrat, Poppins) via `css/tokens.css`. Styles split into layered CSS files imported through `css/styles.css`.

## Technology Stack

### Frontend

* HTML5
* CSS3

### Layout Techniques

* CSS Flexbox
* CSS Grid
* CSS custom properties (design tokens)
* Responsive media queries

## Project Structure

```text
northlight-iceland/
│
├── index.html              # Homepage
├── destinations.html       # Five destination guides
├── experiences.html        # Five activity guides + season table
├── travel-guide.html       # Timing, transport, budget, safety, packing
├── gallery.html            # Photo grid
├── contact.html            # Feedback form + image attributions
├── thank-you.html          # Form confirmation (demo redirect target)
├── template.html           # Page shell for copying new pages
│
├── css/
│   ├── styles.css          # Entry point — imports the layers below
│   ├── tokens.css          # Colours, spacing, fonts
│   ├── base.css            # Reset, typography, utilities
│   ├── layout.css          # Header, nav, footer, grids
│   └── components.css      # Cards, forms, gallery, tables
│
├── images/                 # Empty — photos served from Unsplash CDN
│
├── docs/                   # Maintainer documentation
│   ├── production-review.md
│   ├── image-attributions.md
│   ├── assets-audit.md
│   └── …
│
├── .github/workflows/
│   └── pages.yml           # GitHub Pages deployment
│
└── README.md
```

## Live Site

**https://harshyadav1711.github.io/northlight-iceland/**

## Local Setup

**Requirements:** a web browser. No Node, npm, or build tools.

1. Clone or download the repository.
2. Preview using either method below.

**Option A — open directly**

Open `index.html` in a browser. Relative links and CSS work. Images still require network access (Unsplash CDN).

**Option B — local HTTP server (recommended)**

From the repository root:

```powershell
python -m http.server 8080
```

Then open http://localhost:8080

Use any static file server if you prefer — `npx serve`, VS Code Live Server, etc. Serve from the repo root so paths like `css/styles.css` resolve correctly.

## Deployment

The site is static HTML/CSS deployed to GitHub Pages.

**Automated (this repository):** pushing to `main` triggers `.github/workflows/pages.yml`, which uploads the repository root as a Pages artifact. Enable Pages under repository Settings → Pages → Source: GitHub Actions.

**Manual / other hosts:** upload all HTML files and the `css/` directory to any static host (Netlify, Cloudflare Pages, S3, etc.). Keep file paths unchanged. No build command required.

The contact form will not send email on static hosting — `method="get"` redirects to `thank-you.html` for demonstration only.

## User Experience Goals

* Find a region or activity without hunting through unrelated pages
* Read planning basics (season, roads, costs) in one place
* Submit feedback through a labelled, keyboard-reachable form
* Use the site on a phone without horizontal scrolling on main content

## Future Enhancements

* Self-hosted images (remove Unsplash CDN dependency)
* Server-side or third-party form handling
* Favicon and custom 404 page
* Optional JavaScript for menu `aria-expanded` and form POST

## Credits

Photographs from [Unsplash](https://unsplash.com/) under the [Unsplash License](https://unsplash.com/license). Full credits on the [Contact page](https://harshyadav1711.github.io/northlight-iceland/contact.html#attributions) and in `docs/image-attributions.md`.

Travel information is for general planning only. NorthLight Iceland does not sell tours or packages.

## Author

Harsh Yadav
