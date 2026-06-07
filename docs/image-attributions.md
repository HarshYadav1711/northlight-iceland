# Image attributions

Audit of all photographs used on the NorthLight Iceland website. Generated from the HTML source — no local image files are bundled; every photograph is loaded from the Unsplash CDN at page render time.

**Summary:** 12 unique photographs · 29 `<img>` references across 5 content pages · 0 local image files

---

## Licensing notes

All photographs are sourced from [Unsplash](https://unsplash.com/) and used under the [Unsplash License](https://unsplash.com/license).

| Permission | Detail |
|------------|--------|
| **Use** | Free for commercial and non-commercial use |
| **Modification** | Allowed (crop, resize, colour adjustment, etc.) |
| **Distribution** | Allowed in websites, social media, and print |
| **Attribution** | Not legally required, but **recommended** — Unsplash asks that credit be given to the photographer and Unsplash when practical |
| **Selling unaltered copies** | Not permitted (e.g. selling the photo itself as a stock image or print without meaningful modification) |
| **Replicating Unsplash** | Not permitted (compiling photos to create a competing image service) |
| **Trademarks / people / private property** | If a photo contains a recognizable trademark, logo, or brand, separate permission may be required from the brand owner. The site does not use images primarily featuring identifiable people or branded products. |

**CDN delivery:** Images are requested from `images.unsplash.com` with crop and quality query parameters (`auto=format`, `fit=crop`, `w`, `q`). Resizing via the CDN does not change licensing terms.

**Local migration:** If photographs are downloaded and self-hosted later, the Unsplash License still applies. Photographer credit should be retained (see `docs/assets-audit.md` for migration guidance).

---

## Attribution requirements

### What the Unsplash License requires

- No mandatory on-page credit.
- No mandatory link back to Unsplash or the photographer.

### What this project provides (recommended practice)

| Location | Content |
|----------|---------|
| `contact.html` — `#attributions` aside | Full photographer list with Unsplash and licence links |
| `gallery.html` — bottom of gallery section | Summary statement linking to Unsplash, the licence, and the Contact page |
| Every page footer | Link to `contact.html#attributions` labelled “Image attributions” |
| `docs/references.md` | Harvard-style bibliography entries for each photograph |
| This document | Complete inventory for maintainers and academic submission |

### Recommended credit format

When adding or updating attributions elsewhere (e.g. README, submission documents), use:

> *[Description]* by [Photographer name] on [Unsplash](https://unsplash.com/)

Example:

> *Northern lights over lake* by Vincent Guth on [Unsplash](https://unsplash.com/photos/1483347756197-71ef873115ba)

---

## Master image catalog

Each row is one unique Unsplash photo. The **Photo ID** matches the filename segment in CDN URLs (`photo-{id}`).

| Photo ID | Description | Photographer | Unsplash source | Pages used |
|----------|-------------|--------------|-----------------|------------|
| `1483347756197-71ef873115ba` | Aurora borealis over lake | Vincent Guth | [unsplash.com/photos/1483347756197-71ef873115ba](https://unsplash.com/photos/1483347756197-71ef873115ba) | `index.html`, `gallery.html` |
| `1529963183539-53a91a228095` | Reykjavík harbour | Jonas Johansson | [unsplash.com/photos/1529963183539-53a91a228095](https://unsplash.com/photos/1529963183539-53a91a228095) | `index.html`, `destinations.html`, `gallery.html` |
| `1476610182048-b716bfb6815a` | Geothermal steam | Erik Odiin | [unsplash.com/photos/1476610182048-b716bfb6815a](https://unsplash.com/photos/1476610182048-b716bfb6815a) | `index.html`, `destinations.html`, `gallery.html` |
| `1520769945061-fa875b7745b9` | Seljalandsfoss waterfall | Kym Ellis | [unsplash.com/photos/1520769945061-fa875b7745b9](https://unsplash.com/photos/1520769945061-fa875b7745b9) | `index.html`, `destinations.html`, `gallery.html` |
| `1504829857797-ddff29c27927` | Iceland highland / fjord landscape | Kym Ellis | [unsplash.com/photos/1504829857797-ddff29c27927](https://unsplash.com/photos/1504829857797-ddff29c27927) | `index.html`, `destinations.html`, `gallery.html` |
| `1531366936337-7c912a4589a7` | Aurora over snow | Markus Spiske | [unsplash.com/photos/1531366936337-7c912a4589a7](https://unsplash.com/photos/1531366936337-7c912a4589a7) | `index.html`, `experiences.html`, `gallery.html` |
| `1439066615861-d1af74d74005` | Glacier hiking | Anders Jildén | [unsplash.com/photos/1439066615861-d1af74d74005](https://unsplash.com/photos/1439066615861-d1af74d74005) | `index.html`, `experiences.html`, `gallery.html` |
| `1478131143088-5e561ea45f65` | Geothermal pool | Silversea Cruises | [unsplash.com/photos/1478131143088-5e561ea45f65](https://unsplash.com/photos/1478131143088-5e561ea45f65) | `index.html`, `experiences.html` |
| `1521295121783-8a263d6dba82` | Mountain reflection | Marc-Olivier Jodoin | [unsplash.com/photos/1521295121783-8a263d6dba82](https://unsplash.com/photos/1521295121783-8a263d6dba82) | `destinations.html`, `gallery.html` |
| `1470074568702-e89b72010f00` | Ring Road landscape | Luca Bravo | [unsplash.com/photos/1470074568702-e89b72010f00](https://unsplash.com/photos/1470074568702-e89b72010f00) | `travel-guide.html` |
| `1483664852095-d662b550591b` | Ice cave interior | Pascal Debrunner | [unsplash.com/photos/1483664852095-d662b550591b](https://unsplash.com/photos/1483664852095-d662b550591b) | `experiences.html`, `gallery.html` |
| `1559827292-581593893654` | Whale tail | NOAA | [unsplash.com/photos/1559827292-581593893654](https://unsplash.com/photos/1559827292-581593893654) | `experiences.html`, `gallery.html` |

**Note:** The Contact page lists “Iceland landscape / fjords — Kym Ellis” as a single credit line; that corresponds to photo `1504829857797-ddff29c27927` (also used for Seljalandsfoss and highland imagery under Kym Ellis’s two separate uploads).

---

## Page-by-page inventory

### `index.html` (8 images)

| Section | Context | Photo ID | Photographer | CDN width |
|---------|---------|----------|--------------|-----------|
| Hero | Full-width banner above main heading | `1483347756197-71ef873115ba` | Vincent Guth | 1800 |
| Featured destinations — Reykjavík card | Destination card image | `1529963183539-53a91a228095` | Jonas Johansson | 800 |
| Featured destinations — Golden Circle card | Destination card image | `1476610182048-b716bfb6815a` | Erik Odiin | 800 |
| Featured destinations — South Coast card | Destination card image | `1520769945061-fa875b7745b9` | Kym Ellis | 800 |
| Featured destinations — Westfjords card | Destination card image | `1504829857797-ddff29c27927` | Kym Ellis | 800 |
| Featured experiences — Northern Lights card | Experience card image | `1531366936337-7c912a4589a7` | Markus Spiske | 800 |
| Featured experiences — Glacier hiking card | Experience card image | `1439066615861-d1af74d74005` | Anders Jildén | 800 |
| Featured experiences — Geothermal pools card | Experience card image | `1478131143088-5e561ea45f65` | Silversea Cruises | 800 |

The hero image is the only above-the-fold photograph on this page (no `loading="lazy"`). All card images use `loading="lazy"`.

---

### `destinations.html` (5 images)

| Section | Anchor | Photo ID | Photographer | CDN width |
|---------|--------|----------|--------------|-----------|
| Reykjavík | `#reykjavik` | `1529963183539-53a91a228095` | Jonas Johansson | 900 |
| Golden Circle | `#golden-circle` | `1476610182048-b716bfb6815a` | Erik Odiin | 900 |
| South Coast | `#south-coast` | `1520769945061-fa875b7745b9` | Kym Ellis | 900 |
| Akureyri | `#akureyri` | `1521295121783-8a263d6dba82` | Marc-Olivier Jodoin | 900 |
| Westfjords | `#westfjords` | `1504829857797-ddff29c27927` | Kym Ellis | 900 |

All images sit in feature-row `<figure class="feature-media">` blocks beside destination prose. All use `loading="lazy"`.

---

### `experiences.html` (5 images)

| Section | Anchor | Photo ID | Photographer | CDN width |
|---------|--------|----------|--------------|-----------|
| Northern Lights | `#northern-lights` | `1531366936337-7c912a4589a7` | Markus Spiske | 800 |
| Glacier hiking | `#glacier-hiking` | `1439066615861-d1af74d74005` | Anders Jildén | 800 |
| Hot springs & geothermal pools | `#hot-springs` | `1478131143088-5e561ea45f65` | Silversea Cruises | 800 |
| Whale watching | `#whale-watching` | `1559827292-581593893654` | NOAA | 800 |
| Ice caves | `#ice-caves` | `1483664852095-d662b550591b` | Pascal Debrunner | 800 |

All images sit in `<figure class="experience-media">` blocks. All use `loading="lazy"`.

---

### `travel-guide.html` (1 image)

| Section | Anchor | Photo ID | Photographer | CDN width |
|---------|--------|----------|--------------|-----------|
| Transport | `#transport` | `1470074568702-e89b72010f00` | Luca Bravo | 900 |

Single feature-row image beside the “Getting around” transport copy. Uses `loading="lazy"`.

---

### `gallery.html` (10 images)

| Figcaption title | Photo ID | Photographer | CDN width |
|------------------|----------|--------------|-----------|
| Northern lights over Þingvallavatn (wide layout) | `1483347756197-71ef873115ba` | Vincent Guth | 1400 |
| Seljalandsfoss | `1520769945061-fa875b7745b9` | Kym Ellis | 800 |
| Reykjavík harbour | `1529963183539-53a91a228095` | Jonas Johansson | 800 |
| Geothermal field | `1476610182048-b716bfb6815a` | Erik Odiin | 800 |
| Glacier outlet | `1439066615861-d1af74d74005` | Anders Jildén | 800 |
| North Iceland | `1521295121783-8a263d6dba82` | Marc-Olivier Jodoin | 800 |
| Westfjords coastline | `1504829857797-ddff29c27927` | Kym Ellis | 800 |
| Ice cave | `1483664852095-d662b550591b` | Pascal Debrunner | 800 |
| Winter aurora | `1531366936337-7c912a4589a7` | Markus Spiske | 800 |
| Whale watching | `1559827292-581593893654` | NOAA | 800 |

Each item is a `<figure class="gallery-item">` with `<figcaption>`. All use `loading="lazy"`. An on-page attribution paragraph links to Unsplash and `contact.html#attributions`.

---

### Pages with no photographs

| Page | Notes |
|------|-------|
| `contact.html` | No `<img>` elements; hosts the `#attributions` credit list |
| `thank-you.html` | No images (form confirmation page) |
| `template.html` | Development shell only; no images in template body |

---

## On-site attribution locations

| File | Element | Purpose |
|------|---------|---------|
| `contact.html` | `<aside id="attributions">` | Primary credit list — photographer names grouped by subject |
| `gallery.html` | `<p class="attribution">` | Inline licence statement with link to full credits |
| All content pages | Footer link `contact.html#attributions` | Persistent path to attributions from every page |

---

## Related documentation

- `docs/references.md` — Harvard-style bibliography for academic submission
- `docs/assets-audit.md` — CDN dependency audit and local migration plan
- `README.md` — Brief licence summary with link to Contact page attributions

---

*Last reviewed: 7 June 2026 — matches HTML source in repository at time of audit.*
