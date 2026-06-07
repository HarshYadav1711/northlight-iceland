# NorthLight Iceland — Asset Audit and Migration Plan

**Audit date:** 7 June 2026  
**Scope:** Non-destructive review of runtime assets and third-party dependencies in the website codebase (HTML, CSS, deployment workflow). No files were modified during this audit.

**Local asset status:** The `images/` directory exists but contains no files. All photographs are loaded from the Unsplash CDN at page render time.

---

## Summary

| Category | Count | Runtime dependency? |
|----------|-------|---------------------|
| Unique external images (Unsplash) | 12 | Yes |
| Total `<img>` references to Unsplash | 29 | Yes |
| External font families (Google Fonts) | 2 | Yes |
| Font weight variants requested | 6 | Yes |
| JavaScript libraries | 0 | — |
| CSS frameworks | 0 | — |
| Outbound content links (external sites) | 6 domains | No (hyperlinks only) |
| GitHub Actions (deployment) | 3 actions | No (build/deploy only) |

The site has no npm packages, no bundled JavaScript, and no CSS framework. Runtime third-party dependencies are limited to **Unsplash** (images) and **Google Fonts** (typography).

---

## Externally hosted images

**Provider:** Unsplash CDN (`images.unsplash.com`)  
**Licence:** [Unsplash License](https://unsplash.com/license) — attribution maintained on `contact.html` and `gallery.html`.

### Inventory

| Photo ID | Subject (alt text summary) | Photographer | Pages used | Approx. requests per page load |
|----------|---------------------------|--------------|------------|--------------------------------|
| `photo-1483347756197-71ef873115ba` | Northern lights over lake | Vincent Guth | `index.html` (hero), `gallery.html` | 1–2 |
| `photo-1529963183539-53a91a228095` | Reykjavík harbour | Jonas Johansson | `index.html`, `destinations.html`, `gallery.html` | 1–3 |
| `photo-1476610182048-b716bfb6815a` | Geothermal steam | Erik Odiin | `index.html`, `destinations.html`, `gallery.html` | 1–3 |
| `photo-1520769945061-fa875b7745b9` | Seljalandsfoss waterfall | Kym Ellis | `index.html`, `destinations.html`, `gallery.html` | 1–3 |
| `photo-1504829857797-ddff29c27927` | Iceland highland landscape | Kym Ellis | `index.html`, `destinations.html`, `gallery.html` | 1–3 |
| `photo-1531366936337-7c912a4589a7` | Aurora over snow | Markus Spiske | `index.html`, `experiences.html`, `gallery.html` | 1–3 |
| `photo-1439066615861-d1af74d74005` | Glacier hiking | Anders Jildén | `index.html`, `experiences.html`, `gallery.html` | 1–3 |
| `photo-1478131143088-5e561ea45f65` | Geothermal pool | Silversea Cruises | `index.html`, `experiences.html` | 1–2 |
| `photo-1521295121783-8a263d6dba82` | Mountain reflection | Marc-Olivier Jodoin | `destinations.html`, `gallery.html` | 1–2 |
| `photo-1470074568702-e89b72010f00` | Ring Road landscape | Luca Bravo | `travel-guide.html` | 1 |
| `photo-1483664852095-d662b550591b` | Ice cave interior | Pascal Debrunner | `experiences.html`, `gallery.html` | 1–2 |
| `photo-1559827292-581593893654` | Whale tail | NOAA | `experiences.html`, `gallery.html` | 1–2 |

### Image usage by page

| Page | External images | Notes |
|------|-----------------|-------|
| `index.html` | 8 | Includes above-the-fold hero (1800px width param) |
| `destinations.html` | 5 | Card images at 900px width param |
| `experiences.html` | 5 | Card images at 800px width param |
| `travel-guide.html` | 1 | Single illustrative image |
| `gallery.html` | 10 | Largest single-page image load; hero item at 1400px |
| `contact.html` | 0 | Attribution links only |
| `thank-you.html` | 0 | — |
| `template.html` | 0 | — |

### Image migration entries

| Current dependency | Where used | Risk | Recommended local replacement |
|--------------------|------------|------|--------------------------------|
| `https://images.unsplash.com/photo-1483347756197-71ef873115ba` | `index.html`, `gallery.html` | **High** — hero image; largest layout impact if CDN fails | `images/hero/aurora-lake.webp` (1800×1013) + `images/gallery/aurora-lake-800.webp` |
| `https://images.unsplash.com/photo-1529963183539-53a91a228095` | `index.html`, `destinations.html`, `gallery.html` | **Medium** — repeated across three pages | `images/destinations/reykjavik-harbour.webp` |
| `https://images.unsplash.com/photo-1476610182048-b716bfb6815a` | `index.html`, `destinations.html`, `gallery.html` | **Medium** | `images/destinations/geothermal-steam.webp` |
| `https://images.unsplash.com/photo-1520769945061-fa875b7745b9` | `index.html`, `destinations.html`, `gallery.html` | **Medium** | `images/destinations/seljalandsfoss.webp` |
| `https://images.unsplash.com/photo-1504829857797-ddff29c27927` | `index.html`, `destinations.html`, `gallery.html` | **Medium** | `images/destinations/highland-landscape.webp` |
| `https://images.unsplash.com/photo-1531366936337-7c912a4589a7` | `index.html`, `experiences.html`, `gallery.html` | **Medium** | `images/experiences/aurora-snow.webp` |
| `https://images.unsplash.com/photo-1439066615861-d1af74d74005` | `index.html`, `experiences.html`, `gallery.html` | **Medium** | `images/experiences/glacier-hiking.webp` |
| `https://images.unsplash.com/photo-1478131143088-5e561ea45f65` | `index.html`, `experiences.html` | **Low–Medium** | `images/experiences/geothermal-pool.webp` |
| `https://images.unsplash.com/photo-1521295121783-8a263d6dba82` | `destinations.html`, `gallery.html` | **Low–Medium** | `images/destinations/mountain-reflection.webp` |
| `https://images.unsplash.com/photo-1470074568702-e89b72010f00` | `travel-guide.html` | **Low** — single use | `images/travel-guide/ring-road.webp` |
| `https://images.unsplash.com/photo-1483664852095-d662b550591b` | `experiences.html`, `gallery.html` | **Low–Medium** | `images/experiences/ice-cave.webp` |
| `https://images.unsplash.com/photo-1559827292-581593893654` | `experiences.html`, `gallery.html` | **Low–Medium** | `images/experiences/whale-tail.webp` |

**Risk rationale (images):**

- **High:** Hero image on `index.html` is above the fold; CDN outage or blocking breaks first impression and Largest Contentful Paint.
- **Medium:** Shared card images used on multiple pages; failure affects several sections simultaneously.
- **Low–Medium:** Used on one or two pages only; degraded experience is localised.

**Additional image risks (all entries):**

- Offline or local preview shows alt text only until CDN responds
- Query parameters (`w`, `q`, `fit`) tie layout to Unsplash URL contract
- Privacy: browser sends Referer header to Unsplash on each request
- No version pinning — CDN content is stable but not guaranteed immutable

---

## Externally hosted fonts

| Current dependency | Where used | Risk | Recommended local replacement |
|--------------------|------------|------|--------------------------------|
| Google Fonts CSS: `Montserrat` weights 500, 600, 700 | `css/tokens.css` → `--font-display`; headings, logo, buttons site-wide | **Medium** | Self-host WOFF2 files in `fonts/montserrat/`; add `@font-face` rules in `css/fonts.css` |
| Google Fonts CSS: `Poppins` weights 400, 500, 600 | `css/tokens.css` → `--font-body`; body copy site-wide | **Medium** | Self-host WOFF2 files in `fonts/poppins/`; add `@font-face` rules in `css/fonts.css` |
| Runtime font files from `fonts.gstatic.com` | Loaded indirectly when `tokens.css` `@import` resolves | **Medium** | Eliminated once local `@font-face` replaces Google Fonts `@import` |

**Implementation detail:** The `@import` in `css/tokens.css` (line 3) is the single entry point:

```css
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@500;600;700&family=Poppins:wght@400;500;600&display=swap");
```

All eight HTML pages link to `css/styles.css`, which imports `tokens.css`. Every page therefore triggers a request to Google Fonts on first visit.

**Risk rationale (fonts):**

- Third-party network request on every cold load (stylesheet + WOFF2 files from `gstatic.com`)
- Flash of unstyled or fallback text if Google CDN is slow or blocked
- Privacy and compliance considerations for EU visitors (Google as sub-processor)
- **Mitigating factor:** `system-ui` is already in the font stack as fallback; site remains readable without Google Fonts

**Alternative (zero-asset):** Remove custom fonts and rely on the existing system stack (`system-ui, sans-serif`) — lowest maintenance, no download cost, slight visual change.

---

## Third-party dependencies

### Runtime dependencies (affect live site)

| Current dependency | Where used | Risk | Recommended local replacement |
|--------------------|------------|------|--------------------------------|
| Unsplash CDN (`images.unsplash.com`) | 29 `<img src>` across 5 HTML pages | **High** | Migrate all 12 unique photos to `images/` (see image table above) |
| Google Fonts (`fonts.googleapis.com`) | `css/tokens.css` | **Medium** | Self-hosted fonts in `fonts/` or system font stack only |
| Google Fonts static files (`fonts.gstatic.com`) | Runtime (browser fetch after CSS parse) | **Medium** | Removed by self-hosting |

### Outbound hyperlinks (not asset dependencies)

These are intentional external references, not loaded assets. No migration required unless policy mandates otherwise.

| Domain | Where used | Risk | Notes |
|--------|------------|------|-------|
| `road.is` | `destinations.html`, `travel-guide.html`, `contact.html` | **Low** | Official road conditions — keep as external link |
| `vedur.is` | `travel-guide.html`, `contact.html`, `experiences.html` | **Low** | Official weather — keep as external link |
| `safetravel.is` | `index.html`, `travel-guide.html` | **Low** | Safety resource — keep as external link |
| `unsplash.com` | `contact.html`, `gallery.html` | **Low** | Licence attribution — keep after local image migration |
| `unsplash.com/license` | `contact.html` | **Low** | Licence reference |

### Deployment dependencies (GitHub Actions only)

| Current dependency | Where used | Risk | Recommended action |
|--------------------|------------|------|---------------------|
| `actions/checkout@v4` | `.github/workflows/pages.yml` | **Low** | Pin to commit SHA for reproducibility (optional hardening) |
| `actions/upload-pages-artifact@v3` | `.github/workflows/pages.yml` | **Low** | Pin to commit SHA (optional) |
| `actions/deploy-pages@v4` | `.github/workflows/pages.yml` | **Low** | Pin to commit SHA (optional) |

These actions do not affect site runtime for visitors. They are not part of the front-end asset migration.

### Dependencies not present

| Expected in many web projects | Status in NorthLight Iceland |
|------------------------------|------------------------------|
| npm / package.json | Not used |
| JavaScript bundles | Not used |
| CSS frameworks (Bootstrap, Tailwind, etc.) | Not used |
| Icon fonts / SVG sprites (external) | Not used |
| Analytics scripts | Not used |
| Map embeds (Google Maps, etc.) | Not used |

---

## Migration plan

This plan describes recommended steps only. **No assets have been replaced as part of this audit.**

### Phase 1 — Prepare local asset structure

1. Create subdirectories under `images/`:

   ```text
   images/
   ├── hero/
   ├── destinations/
   ├── experiences/
   ├── travel-guide/
   └── gallery/          # optional if reusing canonical files via relative paths
   ```

2. Create `fonts/montserrat/` and `fonts/poppins/` for WOFF2 files.

3. Add `css/fonts.css` for `@font-face` declarations (new file; import from `styles.css` when ready).

4. Add `docs/evidence/` screenshots before and after migration for visual regression checks.

### Phase 2 — Download and optimise images

1. Download each of the 12 unique Unsplash photos at source quality (per Unsplash License).

2. Export WebP (primary) and JPEG (fallback if needed) at these target widths to match current usage:

   | Use case | Target width | Example path |
   |----------|--------------|--------------|
   | Homepage hero | 1800px | `images/hero/aurora-lake.webp` |
   | Gallery feature | 1400px | Reuse hero asset or dedicated crop |
   | Destination cards | 900px | `images/destinations/*.webp` |
   | Experience / index cards | 800px | `images/experiences/*.webp` |
   | Travel guide inline | 900px | `images/travel-guide/ring-road.webp` |

3. Preserve existing `width` and `height` attributes in HTML when updating `src` paths to prevent layout shift.

4. Keep photographer attributions on `contact.html` unchanged.

### Phase 3 — Self-host fonts

1. Download Montserrat (500, 600, 700) and Poppins (400, 500, 600) WOFF2 files from [Google Fonts](https://fonts.google.com/) or [google-webfonts-helper](https://gwfh.mranftl.com/fonts).

2. Add `@font-face` rules in `css/fonts.css` with `font-display: swap`.

3. Replace the Google Fonts `@import` in `css/tokens.css` with `@import url("fonts.css")` (or merge into tokens).

4. Verify `--font-body` and `--font-display` token values remain unchanged.

### Phase 4 — Update HTML references

1. Replace each `https://images.unsplash.com/...` `src` with the corresponding local path (29 replacements across 5 files).

2. Run HTML validation and visual checks at 375px, 768px, and 1280px.

3. Confirm `gallery.html` and `index.html` still meet performance expectations without CDN latency.

### Phase 5 — Verification

| Check | Tool / method |
|-------|---------------|
| No remaining Unsplash image URLs in HTML | Repository search for `images.unsplash.com` |
| No Google Fonts `@import` | Repository search for `fonts.googleapis.com` |
| Offline preview | Local server with network disabled — images and fonts still render |
| HTML validation | W3C Nu Validator |
| Accessibility | WAVE — alt text unchanged |
| File size budget | Total `images/` + `fonts/` size documented in commit message |

### Rollback strategy

Keep a branch or tag with CDN URLs intact until local assets are verified on GitHub Pages. Reverting HTML `src` values and restoring the Google Fonts `@import` restores the current behaviour without data loss.

---

## Risk summary matrix

| Dependency | Availability risk | Privacy risk | Performance impact | Migration effort |
|------------|-------------------|--------------|--------------------|------------------|
| Unsplash images | Medium–High | Low–Medium (Referer) | High (LCP, 29 requests) | Medium (12 files, 29 HTML edits) |
| Google Fonts | Low | Medium (third-party) | Medium (render-blocking CSS) | Low–Medium (6 font files, 1 CSS edit) |
| External travel links | N/A (links only) | None | None | None required |
| GitHub Actions | Low | None | None (deploy time only) | Optional pinning only |

---

## Post-migration target state

After migration, the site should have:

- **Zero** runtime requests to `images.unsplash.com`
- **Zero** runtime requests to `fonts.googleapis.com` or `fonts.gstatic.com`
- All photographs served from `images/` on the same origin as GitHub Pages
- All typography served from `fonts/` or system fallbacks
- Unchanged visual design, alt text, and attribution content
- Improved offline local preview and reduced third-party dependency footprint

---

## Document history

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 7 June 2026 | Initial non-destructive audit and migration plan |
