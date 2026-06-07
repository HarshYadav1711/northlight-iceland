# NorthLight Iceland — Evaluation Report

**Document version:** 2.0 (final submission)  
**Date:** June 2026  
**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

---

## Status at submission

| Category | Status |
|----------|--------|
| Development review (markup, accessibility intent, remediations) | **Completed** — see [Part A](#part-a--completed-findings) |
| Automated HTML lint (`html-validate`) | **Completed** — 0 errors on all 8 HTML files |
| Cross-browser manual testing | Pending manual verification |
| Responsive layout manual testing (all breakpoints × browsers) | Pending manual verification |
| W3C Markup Validation Service | Pending manual verification |
| W3C CSS Validation Service | Pending manual verification |
| WAVE accessibility evaluation | Pending manual verification |
| Evidence screenshots | Pending manual verification |

This report separates **completed findings** (verified during development and automated review) from **manual verification checklists** (standard final steps before or after submission). Items marked “Pending manual verification” are not failures — they await hands-on testing and optional supplementary tooling.

---

## Evaluation scope

**Public pages (7):** `index.html`, `destinations.html`, `experiences.html`, `travel-guide.html`, `gallery.html`, `contact.html`, `thank-you.html`

**Development shell (1):** `template.html`

**Shared stylesheet:** `css/styles.css` (imports `tokens.css`, `base.css`, `layout.css`, `components.css`)

Cross-reference: detailed submission sign-off is recorded in `SUBMISSION-REVIEW.md`.

---

## Part A — Completed findings

### A.1 Automated markup review

| Check | Tool | Scope | Result |
|-------|------|-------|--------|
| HTML structure and validity rules | [`html-validate`](https://html-validate.org/) CLI | All 8 `.html` files at repository root | **Pass — 0 errors** |

Re-run locally from the repository root:

```bash
npx html-validate "*.html"
```

### A.2 CSS structure review

| Check | Result |
|-------|--------|
| Layered imports via `css/styles.css` | **Pass** — `tokens`, `base`, `layout`, `components` resolve in order |
| Invalid properties in stylesheets | **Pass** — no stray HTML attributes or invalid declarations identified during review |
| Responsive breakpoints in use | **Pass** — 600px, 768px, and 900px media queries drive grids, navigation, forms, and tables |

### A.3 Implemented accessibility features

The following features are present in the current codebase (design intent — not a substitute for WAVE or assistive-technology testing):

| Feature | Implementation |
|---------|----------------|
| Skip link | Present on all pages |
| Page language | `lang="en"` on `<html>` |
| Headings | One `<h1>` per page; logical `h2` / `h3` hierarchy |
| Alt text | Descriptive `alt` on all content images |
| Form labels | Explicit `<label>` associations; hints via `aria-describedby` |
| Colour contrast | Dark text on light surfaces; breadcrumb and footer link opacity raised during review |
| Focus indicators | Visible `:focus-visible` outline on interactive elements |
| Tables | `<caption>` and `th scope` on all data tables |
| Motion | `prefers-reduced-motion` respected for navigation animation and form transitions |
| Navigation toggle | Hidden checkbox (`tabindex="-1"`, `aria-hidden="true"`); visible label (`tabindex="0"`, `aria-controls="main-nav"`) |
| Screen reader utility | `.visually-hidden` and `.nav-checkbox` use `clip-path: inset(50%)` |

### A.4 Development review — issues identified and resolved

Issues below were found during development and pre-submission review (`SUBMISSION-REVIEW.md`). All except the known `aria-expanded` limitation were remediated in the repository.

| Issue | Area | Severity | Resolution |
|-------|------|----------|------------|
| Duplicate complementary landmarks without unique labels | `contact.html` | Medium | **Resolved** — both `<aside>` elements named with `aria-labelledby` |
| Redundant `for` on nested consent checkbox label | `contact.html` | Low | **Resolved** — redundant `for` removed |
| Hidden checkbox in tab order | Navigation (all pages) | Medium | **Resolved** — `tabindex="-1"` and `aria-hidden="true"` on checkbox; label receives focus |
| Deprecated `clip: rect()` in visually-hidden utility | `css/base.css` | Low | **Resolved** — `clip-path: inset(50%)` only |
| Redundant `aria-required` alongside native `required` | `contact.html` | Low | **Resolved** — redundant attribute removed |
| Low-contrast breadcrumb links on page hero | Inner pages | Medium | **Resolved** — opacity increased to 88% |
| Low-contrast footer links | All pages | Medium | **Resolved** — high-contrast white link colours |
| Wide tables on small screens | Table pages | Medium | **Resolved** — `.table-wrap` with horizontal scroll |
| Mobile menu `aria-expanded` not updated without JavaScript | Navigation (all pages) | Low | **Known limitation** — acceptable without JavaScript |

### A.5 Known limitations (accepted for submission)

- Contact form uses `method="get"` and redirects to `thank-you.html`; no server-side processing.
- Photographs load from the Unsplash CDN; offline viewing shows `alt` text until images load.
- CSS-only mobile menu does not update `aria-expanded` when toggled.
- Cross-browser layout was reviewed in a Chromium-based browser during development; Firefox and Edge hands-on runs are listed under manual verification below.

---

## Part B — Manual verification checklists

Complete these checks in a browser or online tool. Record results and optional screenshots in `docs/evidence/` when finished. Until then, each section remains **Pending manual verification**.

### B.1 Cross-browser testing

**Method:** Manual testing at desktop viewport (1280px) and mobile viewport (375px). Verify navigation, link targets, form interaction, image loading, and typographic rendering.

**Browsers to test:**

| Browser | Version tested | Layout & navigation | Form interaction | Fonts load | Status |
|---------|----------------|---------------------|------------------|------------|--------|
| Google Chrome | — | [ ] | [ ] | [ ] | Pending manual verification |
| Mozilla Firefox | — | [ ] | [ ] | [ ] | Pending manual verification |
| Microsoft Edge | — | [ ] | [ ] | [ ] | Pending manual verification |

**Checklist:**

- [ ] Primary navigation links reach the correct pages
- [ ] Mobile menu toggle opens and closes at 375px width
- [ ] Contact form shows browser validation for invalid input
- [ ] External links include `rel="noopener noreferrer"` (verify intended same-tab or new-tab behaviour)
- [ ] Google Fonts (Montserrat, Poppins) render when network is available

**Optional evidence (save to `docs/evidence/` when captured):**

| File | Description |
|------|-------------|
| `browser-chrome-home.png` | Homepage layout in Chrome at 1280px |
| `browser-firefox-nav.png` | Navigation and mobile menu in Firefox |
| `browser-edge-form.png` | Contact form validation in Edge |

---

### B.2 Responsive layout testing

**Method:** Browser DevTools device emulation or window resize at three widths.

| Breakpoint | Width | Example device |
|------------|-------|----------------|
| Mobile | 375px | iPhone SE |
| Tablet | 768px | iPad portrait |
| Desktop | 1280px | Standard laptop |

**Checklist — mark each cell when verified:**

| Test | Mobile (375px) | Tablet (768px) | Desktop (1280px) |
|------|----------------|----------------|------------------|
| Navigation usable | [ ] | [ ] | [ ] |
| Hero / page hero readable | [ ] | [ ] | [ ] |
| Card grids layout correctly | [ ] | [ ] | [ ] |
| Tables scroll horizontally inside `.table-wrap` | [ ] | [ ] | [ ] |
| Contact form usable | [ ] | [ ] | [ ] |
| Footer readable | [ ] | [ ] | [ ] |

**Section status:** Pending manual verification

**Optional evidence (save to `docs/evidence/` when captured):**

| File | Description |
|------|-------------|
| `responsive-mobile-375.png` | Homepage at 375px width |
| `responsive-tablet-768.png` | Destinations page at 768px width |
| `responsive-desktop-1280.png` | Travel Guide page at 1280px width |

---

### B.3 W3C HTML validation (supplementary)

**Note:** Automated `html-validate` already reports 0 errors (see [A.1](#a1-automated-markup-review)). The W3C Nu Validator is an optional supplementary check.

**Tool:** https://validator.w3.org/nu/

**Procedure:**

1. Upload each HTML file or validate by direct input
2. Record errors and warnings per page
3. Remediate any unintended issues and re-validate

**Checklist:**

| Page | Errors | Warnings | Verified | Status |
|------|--------|----------|----------|--------|
| `index.html` | — | — | [ ] | Pending manual verification |
| `destinations.html` | — | — | [ ] | Pending manual verification |
| `experiences.html` | — | — | [ ] | Pending manual verification |
| `travel-guide.html` | — | — | [ ] | Pending manual verification |
| `gallery.html` | — | — | [ ] | Pending manual verification |
| `contact.html` | — | — | [ ] | Pending manual verification |
| `thank-you.html` | — | — | [ ] | Pending manual verification |
| `template.html` | — | — | [ ] | Pending manual verification |

**Optional evidence (save to `docs/evidence/` when captured):**

| File | Description |
|------|-------------|
| `html-validation-home.png` | W3C Nu Validator result for `index.html` |
| `html-validation-contact.png` | W3C Nu Validator result for `contact.html` |

---

### B.4 W3C CSS validation

**Tool:** https://jigsaw.w3.org/css-validator/

**File to validate:** `css/styles.css` (validator follows `@import` chain)

**Checklist:**

| File | Errors | Warnings | Verified | Status |
|------|--------|----------|----------|--------|
| `css/styles.css` | — | — | [ ] | Pending manual verification |

**Optional evidence (save to `docs/evidence/` when captured):**

| File | Description |
|------|-------------|
| `css-validation.png` | W3C CSS Validator result for `css/styles.css` |

---

### B.5 WAVE accessibility evaluation

**Tool:** https://wave.webaim.org/ (or WAVE browser extension on local files)

**Pages to evaluate:** Home (`index.html`), Destinations (`destinations.html`), Contact (`contact.html`)

**Procedure:**

1. Enter the live URL or evaluate local files
2. Review errors, contrast errors, alerts, and structural features
3. Record summary counts; remediate any unintended issues

**Checklist:**

| Page | Errors | Contrast errors | Alerts | Verified | Status |
|------|--------|-----------------|--------|----------|--------|
| `index.html` | — | — | — | [ ] | Pending manual verification |
| `destinations.html` | — | — | — | [ ] | Pending manual verification |
| `contact.html` | — | — | — | [ ] | Pending manual verification |

**Optional evidence (save to `docs/evidence/` when captured):**

| File | Description |
|------|-------------|
| `wave-home.png` | WAVE report for homepage |
| `wave-destinations.png` | WAVE report for destinations page |
| `wave-contact.png` | WAVE report for contact page |

---

### B.6 Evidence capture summary

Create `docs/evidence/` when screenshots are ready. None are required for submission if manual checks are recorded elsewhere, but the filenames above provide a consistent naming scheme.

| Evidence set | Files expected | Status |
|--------------|----------------|--------|
| Browser testing | 3 screenshots | Pending manual verification |
| Responsive testing | 3 screenshots | Pending manual verification |
| W3C HTML validation | 2 screenshots | Pending manual verification |
| W3C CSS validation | 1 screenshot | Pending manual verification |
| WAVE evaluation | 3 screenshots | Pending manual verification |

---

## Conclusion

NorthLight Iceland is a multi-page, responsive, static HTML/CSS travel website. **Development and automated review are complete:** markup passes `html-validate` with zero errors, accessibility features are implemented as documented in Part A, and identified markup issues have been remediated except for the documented CSS-only menu limitation.

**Manual verification** (Part B) covers cross-browser runs, responsive spot-checks, optional W3C validator passes, WAVE evaluation, and evidence capture. These items are clearly scoped checklists — not open defects — and can be completed and recorded when time and tooling allow.

For submission sign-off details, see `SUBMISSION-REVIEW.md`.
