# Documentation Consistency Audit

**Date:** 7 June 2026  
**Scope:** `README.md`, `docs/website-specification.md`, `docs/evaluation-report.md`, `docs/references.md`, `SUBMISSION-REVIEW.md` compared against the website source (HTML, CSS, GitHub Actions workflow).

**Method:** Read all five documents; inspected all eight HTML pages and the CSS layer files (`css/styles.css` and imports); ran `npx html-validate "*.html"` (0 errors); searched markup and stylesheets for breakpoints, accessibility attributes, external-link behaviour, and asset paths.

**Post-audit updates (same day):** Issues 1, 4, 5, and 6 below were remediated after this audit was written. Navigation accessibility attributes are now on all eight HTML pages; `clip: rect()` was removed from `css/base.css`; `images/.gitkeep` exists; `docs/evaluation-report.md` was restructured to v2.0; `docs/references.md` Unsplash URLs, `docs/website-specification.md` breakpoints, and `README.md` were aligned with the codebase. See `docs/submission-readiness-audit.md` for current submission status.

---

## Executive summary

Most high-level feature claims are implemented: six primary navigation pages plus `thank-you.html`, five destination guides, five experience guides with a seasonal table, travel-planning sections, a ten-image gallery, a GET-based contact form, layered CSS, Unsplash CDN images, and GitHub Pages deployment.

The largest gaps are **documentation that describes accessibility fixes not present in the code**, **conflicting responsive breakpoint values across documents**, **evaluation status that contradicts the submission review**, and **incorrect Unsplash URLs in the references bibliography**. Several smaller mismatches involve missing project directories, omitted form fields, and external-link behaviour.

---

## Issues

### 1. Navigation accessibility fixes documented but not implemented

| Field | Detail |
|-------|--------|
| **File** | `SUBMISSION-REVIEW.md`, `docs/evaluation-report.md` |
| **Claim** | Hidden navigation checkbox removed from tab order (`tabindex="-1"`, `aria-hidden="true"`). Visible toggle label receives keyboard focus (`tabindex="0"`) with `aria-controls="main-nav"`. Issue listed under “Improvements made” / “Navigation keyboard access”. |
| **Actual implementation** | All eight HTML pages use `<input type="checkbox" id="nav-toggle" class="nav-checkbox" aria-controls="main-nav">` with no `tabindex` or `aria-hidden`. The paired `<label for="nav-toggle">` has no `tabindex="0"` and no `aria-controls`. The visually hidden checkbox remains focusable on viewports below 900px. At ≥900px the checkbox is removed from layout via `display: none` in `css/layout.css`, not via `tabindex`. |
| **Recommended correction** | Either apply the documented HTML attributes to every page’s nav toggle, or revise both documents to state that the checkbox remains in the mobile tab order and describe the actual focus behaviour (label activates checkbox via `for` association). |

---

### 2. External links do not open in a new tab

| Field | Detail |
|-------|--------|
| **File** | `docs/evaluation-report.md` |
| **Claim** | Under browser-testing checks: “External links open in a new tab with `rel="noopener noreferrer`”. |
| **Actual implementation** | External links (`road.is`, `vedur.is`, `safetravel.is`, Unsplash, aurora forecast) include `rel="noopener noreferrer"` but **no** `target="_blank"` appears in any HTML file. Links navigate in the same tab. |
| **Recommended correction** | Remove the “open in a new tab” requirement from the evaluation checklist, or add `target="_blank"` to external links if that behaviour is intended. |

---

### 3. Responsive breakpoints conflict across documents

| Field | Detail |
|-------|--------|
| **File** | `docs/website-specification.md` (primary conflict); also `SUBMISSION-REVIEW.md` (partial) |
| **Claim** | `website-specification.md`: Mobile &lt;768px; Tablet 768px–959px with “horizontal navigation” and two-column grids; Desktop 960px+ with three-column card grids and 75rem max-width. `SUBMISSION-REVIEW.md`: “Form two-column rows activate” at tablet 768px (implies all two-column form behaviour starts there). |
| **Actual implementation** | CSS breakpoints in `css/layout.css` and `css/components.css`: **600px** — two-column card grids (`card-grid--2`), gallery grid, form field pairs (`form-row--2`); **768px** — footer three-column layout, feature rows, form aside + panel (`form-layout`), experience list layout; **900px** — horizontal primary navigation, three-column card grids (`card-grid--3`), wide gallery item span. Max-width `75rem` is set in `css/tokens.css` at all sizes. `README.md` correctly cites 600px and 900px. |
| **Recommended correction** | Align `website-specification.md` with the 600px / 768px / 900px breakpoints used in CSS, and note that horizontal navigation starts at 900px, not 768px. Update `SUBMISSION-REVIEW.md` to state form **field pairs** activate at 600px and the aside + form panel layout at 768px. |

---

### 4. Evaluation report status contradicts submission review

| Field | Detail |
|-------|--------|
| **File** | `docs/evaluation-report.md` vs `SUBMISSION-REVIEW.md` |
| **Claim** | `evaluation-report.md`: Browser, responsive, HTML, CSS, and WAVE testing tables are all **Pending** with “_To be recorded_” placeholders; evidence screenshots expected in `docs/evidence/`. `SUBMISSION-REVIEW.md`: HTML validation **Pass — 0 errors**; responsive layouts **Pass**; cross-browser **Pass** (Chromium tested). |
| **Actual implementation** | `npx html-validate "*.html"` exits 0 (no errors). No `docs/evidence/` directory exists. No recorded browser versions, WAVE counts, or W3C validator screenshots. Responsive behaviour is implemented in CSS but formal test results are not filed. |
| **Recommended correction** | Reconcile the two documents: either complete `evaluation-report.md` with recorded results and evidence files, or add a cross-reference in `evaluation-report.md` pointing to `SUBMISSION-REVIEW.md` for completed checks and mark overlapping sections as done. |

---

### 5. “Improvements made” lists resolved issues that remain in code

| Field | Detail |
|-------|--------|
| **File** | `docs/evaluation-report.md`, `SUBMISSION-REVIEW.md` |
| **Claim** | “Hidden checkbox remained in tab order” resolved via `tabindex="-1"` and `aria-hidden="true"` (see Issue 1). “Screen reader utility updated to `clip-path: inset(50%)` **instead of** deprecated `clip: rect()`”. |
| **Actual implementation** | `css/base.css` `.visually-hidden, .nav-checkbox` sets **both** `clip: rect(0, 0, 0, 0)` and `clip-path: inset(50%)`. Navigation checkbox tab-order fix is absent (Issue 1). |
| **Recommended correction** | In “Improvements made”, state that `clip-path` was **added alongside** `clip: rect()` for backward compatibility (if intentional), or remove `clip: rect()` from CSS and update the docs. Mark the navigation tab-order item as open if the HTML fix was never applied. |

---

### 6. `images/` directory listed in README but missing

| Field | Detail |
|-------|--------|
| **File** | `README.md` |
| **Claim** | Project structure includes `images/` — “Placeholder (.gitkeep); photos served from Unsplash CDN”. |
| **Actual implementation** | No `images/` directory exists in the repository. All photographs load from `images.unsplash.com` URLs in HTML. |
| **Recommended correction** | Remove `images/` from the structure diagram or create the directory with `.gitkeep` if it is meant to exist for future self-hosted assets (as noted in Future Enhancements). |

---

### 7. Homepage destination count inconsistent with site-wide claims

| Field | Detail |
|-------|--------|
| **File** | `README.md`, `docs/website-specification.md` (implicit via five-region scope) |
| **Claim** | README: “The site covers **five regions**”. `destinations.html`: “Five regions that shape most Iceland itineraries.” |
| **Actual implementation** | `index.html` featured-destinations section shows **four** destination cards (Reykjavík, Golden Circle, South Coast, Westfjords) and lead copy reads “**Four routes** that cover most first visits”. Akureyri is omitted from the homepage grid but fully documented on `destinations.html`. |
| **Recommended correction** | Either add an Akureyri card to the homepage and change the lead text to “five routes”, or clarify in README that the homepage highlights four featured regions while the Destinations page covers all five. |

---

### 8. Contact form consent field omitted from README

| Field | Detail |
|-------|--------|
| **File** | `README.md` |
| **Claim** | Feedback form collects “name, email, destination interest, travel season, and message”. |
| **Actual implementation** | `contact.html` includes a **required consent checkbox** (`id="consent"`, `name="consent"`) in addition to the five fields listed. `docs/website-specification.md` correctly documents the consent field. |
| **Recommended correction** | Add the consent checkbox to the README Features → Feedback Form list. |

---

### 9. Unsplash photo URLs in references use incorrect path format

| Field | Detail |
|-------|--------|
| **File** | `docs/references.md` |
| **Claim** | Image source entries link to Unsplash photographs, e.g. `<https://unsplash.com/photos/photo-1470074568702-e89b72010f00>`. |
| **Actual implementation** | HTML and `docs/image-attributions.md` use CDN paths with photo IDs such as `photo-1470074568702-e89b72010f00` under `images.unsplash.com`. Unsplash page URLs in the attributions doc use the format `unsplash.com/photos/{id}` **without** a duplicated `photo-` prefix in the slug (e.g. `https://unsplash.com/photos/1483347756197-71ef873115ba`). All twelve bibliography URLs in `references.md` insert an extra `photo-` segment that does not match working Unsplash page URLs. |
| **Recommended correction** | Update each image reference URL to match the format in `docs/image-attributions.md` (remove the redundant `photo-` prefix from the path segment after `/photos/`). |

---

### 10. Breadcrumbs not on every inner content page

| Field | Detail |
|-------|--------|
| **File** | `docs/website-specification.md` |
| **Claim** | “Every content page shares a persistent header … **breadcrumbs on inner pages**”. |
| **Actual implementation** | Breadcrumbs appear on `destinations.html`, `experiences.html`, `travel-guide.html`, `gallery.html`, and `contact.html`. `thank-you.html` has no breadcrumb or page hero. `index.html` (homepage) correctly omits breadcrumbs. |
| **Recommended correction** | Narrow the claim to “breadcrumbs on standard inner guide pages” and exclude `thank-you.html`, or add a minimal breadcrumb trail to `thank-you.html` (e.g. Home / Contact / Thank you). |

---

### 11. `aria-controls` placement differs from submission description

| Field | Detail |
|-------|--------|
| **File** | `SUBMISSION-REVIEW.md` |
| **Claim** | “Visible label receives keyboard focus … with `aria-controls="main-nav"`.” |
| **Actual implementation** | `aria-controls="main-nav"` is on the `<input type="checkbox">`, not on the visible `<label class="nav-toggle">`. The label exposes only visually hidden text “Toggle navigation menu” and decorative bars marked `aria-hidden="true"`. |
| **Recommended correction** | Revise the submission note to state that `aria-controls` is on the checkbox input, or move the attribute to the label if that matches the intended ARIA pattern. |

---

### 12. Evaluation scope page count differs between documents

| Field | Detail |
|-------|--------|
| **File** | `docs/evaluation-report.md` vs `SUBMISSION-REVIEW.md` |
| **Claim** | `evaluation-report.md`: “seven public HTML pages” (excludes `template.html`). `SUBMISSION-REVIEW.md`: “html-validate on all **8 pages**” including `template.html`. |
| **Actual implementation** | Eight `.html` files exist at the repository root. `template.html` is a development shell, not linked from public navigation. `html-validate` passes on all eight. |
| **Recommended correction** | Standardise terminology: e.g. “seven public pages plus one development template” across both documents. |

---

### 13. Experience naming inconsistency (minor)

| Field | Detail |
|-------|--------|
| **File** | `README.md` |
| **Claim** | Experiences list includes “**Geothermal hot springs**”. |
| **Actual implementation** | `experiences.html` section heading and nav link use “**Hot springs**” / “Hot springs &amp; geothermal pools” (`#hot-springs`). Seasonal table row label is “Hot springs”. |
| **Recommended correction** | Align README wording with the page title (“Hot springs & geothermal pools”) or rename the on-page heading to match README. |

---

### 14. GitHub Pages workflow triggers on `master` — not mentioned in docs

| Field | Detail |
|-------|--------|
| **File** | `README.md`, `docs/website-specification.md` |
| **Claim** | Deployment triggers on push to `main`. |
| **Actual implementation** | `.github/workflows/pages.yml` triggers on `push` to branches **`main` and `master`**, plus `workflow_dispatch`. |
| **Recommended correction** | Optional: note both branch names in deployment sections, or restrict the workflow to `main` only if `master` is unintentional. |

---

## Verified claims (no correction required)

The following documented claims match the codebase:

| Claim | Evidence |
|-------|----------|
| HTML and CSS only; no JavaScript | No `<script>` tags; nav toggle is CSS-only |
| Layered CSS via `css/styles.css` importing `tokens`, `base`, `layout`, `components` | `css/styles.css` import chain |
| Google Fonts Montserrat and Poppins | `@import` in `css/tokens.css` |
| Five destinations with drive times, stay length, activity links | `destinations.html` sections and comparison table |
| Five experiences with seasonal comparison table | `experiences.html` articles and `#seasons` table |
| Travel guide: timing, transport, budget, safety, packing | `travel-guide.html` sections with in-page nav |
| Gallery: ten photographs with captions | Ten `<figure class="gallery-item">` entries in `gallery.html` |
| Contact form GET → `thank-you.html` | `contact.html` form `action` and `method="get"` |
| Form validation constraints (2–80 name, 20–2000 message, required selects, consent) | HTML5 attributes on `contact.html` |
| Skip link, `lang="en"`, one `<h1>` per page, table `<caption>` and `scope` | Present on reviewed pages |
| `aria-current="page"` on active nav links | Set per page in primary navigation |
| `prefers-reduced-motion` for nav and form transitions | `css/layout.css`, `css/base.css`, `css/components.css` |
| `.table-wrap` horizontal scroll on narrow viewports | Used on all three data tables |
| Image attributions on Contact page | `contact.html#attributions` aside with twelve credits |
| `thank-you.html` uses `noindex` | `<meta name="robots" content="noindex">` |
| GitHub Pages deploy from repository root | `pages.yml` uploads `path: .` |
| `html-validate` zero errors | Confirmed via CLI run on 7 June 2026 |
| Live URL | Matches `https://harshyadav1711.github.io/northlight-iceland/` in all five documents |
| Twelve unique Unsplash photographs | Matches `docs/image-attributions.md` catalog and HTML `src` URLs |
| Contact page duplicate `<aside>` landmarks uniquely labelled | `aria-labelledby` on form aside and attributions aside |

---

## Cross-document consistency matrix

| Topic | README | website-spec | evaluation-report | references | SUBMISSION-REVIEW | Code |
|-------|--------|--------------|-------------------|------------|-------------------|------|
| Breakpoints | 600px / 900px | 768px / 960px | 375 / 768 / 1280 (test widths) | — | 375 / 768 / 1280 | 600 / 768 / 900px |
| Nav tab-order fix | Known `aria-expanded` limitation only | — | Documented as fixed | — | Documented as fixed | **Not applied** |
| HTML validation | — | — | Pending | — | Pass (0 errors) | Pass (verified) |
| External links new tab | — | — | Required | — | — | Same-tab only |
| Form consent field | Omitted | Documented | — | — | — | Implemented |
| `images/` directory | Listed | — | — | — | — | **Missing** |
| Evidence screenshots | — | — | Expected in `docs/evidence/` | — | — | **Directory absent** |

---

## Recommended priority order

1. **High** — Fix or rewrite navigation accessibility claims in `SUBMISSION-REVIEW.md` and `docs/evaluation-report.md` (Issue 1, 5, 11).
2. **High** — Reconcile evaluation pending status with submission pass results (Issue 4).
3. **Medium** — Correct `docs/website-specification.md` breakpoints and navigation behaviour (Issue 3).
4. **Medium** — Fix `docs/references.md` Unsplash URLs (Issue 9).
5. **Low** — README structure (`images/`), form consent field, homepage four-vs-five regions, experience naming, breadcrumb scope, workflow branch note (Issues 6–8, 10, 13, 14).

---

*This audit reports inconsistencies only. No code or documentation files were modified during the review.*
