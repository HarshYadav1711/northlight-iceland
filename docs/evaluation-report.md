# NorthLight Iceland — Evaluation Report

**Document version:** 1.0  
**Date:** June 2026  
**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

---

## Evaluation scope

This report documents planned and completed quality checks for the NorthLight Iceland website. Pages under review include all seven public HTML pages (`index.html`, `destinations.html`, `experiences.html`, `travel-guide.html`, `gallery.html`, `contact.html`, and `thank-you.html`), plus the shared stylesheet at `css/styles.css`.

Evidence screenshots should be captured during testing and saved to `docs/evidence/` before final submission.

---

## Browser testing

### Method

Manual testing across major browsers at desktop viewport (1280px). Verify navigation, link targets, form interaction, image loading, and typographic rendering.

| Browser | Version (record when tested) | Status |
|---------|------------------------------|--------|
| Google Chrome | _To be recorded_ | Pending |
| Mozilla Firefox | _To be recorded_ | Pending |
| Microsoft Edge | _To be recorded_ | Pending |

### Checks

- Primary navigation links reach the correct pages
- Mobile menu toggle opens and closes on small viewports
- Contact form validation messages appear for invalid input
- External links open in a new tab with `rel="noopener noreferrer"`
- Google Fonts (Montserrat, Poppins) load correctly

### Evidence placeholders

| Screenshot | Description |
|------------|-------------|
| `docs/evidence/browser-chrome-home.png` | Homepage layout in Chrome at 1280px |
| `docs/evidence/browser-firefox-nav.png` | Navigation and mobile menu in Firefox |
| `docs/evidence/browser-edge-form.png` | Contact form validation in Edge |

---

## Responsive testing

### Method

Browser DevTools device emulation and window resize at three breakpoints:

| Breakpoint | Width | Device examples |
|------------|-------|-----------------|
| Mobile | 375px | iPhone SE |
| Tablet | 768px | iPad portrait |
| Desktop | 1280px | Standard laptop |

### Test matrix

| Test | Mobile | Tablet | Desktop |
|------|--------|--------|---------|
| Navigation accessible | _Pending_ | _Pending_ | _Pending_ |
| Hero readable | _Pending_ | _Pending_ | _Pending_ |
| Card grid layout | _Pending_ | _Pending_ | _Pending_ |
| Tables scroll horizontally | _Pending_ | _Pending_ | _Pending_ |
| Form usable | _Pending_ | _Pending_ | _Pending_ |
| Footer readable | _Pending_ | _Pending_ | _Pending_ |

### Evidence placeholders

| Screenshot | Description |
|------------|-------------|
| `docs/evidence/responsive-mobile-375.png` | Homepage at 375px width |
| `docs/evidence/responsive-tablet-768.png` | Destinations page at 768px width |
| `docs/evidence/responsive-desktop-1280.png` | Travel Guide page at 1280px width |

---

## HTML validation

### Method

Validate each HTML page using the W3C Markup Validation Service:

**Tool:** https://validator.w3.org/nu/

**Procedure:**

1. Upload each HTML file or validate by direct input
2. Record errors and warnings per page
3. Remediate any issues and re-validate

### Results

| Page | Errors | Warnings | Status |
|------|--------|----------|--------|
| index.html | _To be recorded_ | _To be recorded_ | Pending |
| destinations.html | _To be recorded_ | _To be recorded_ | Pending |
| experiences.html | _To be recorded_ | _To be recorded_ | Pending |
| travel-guide.html | _To be recorded_ | _To be recorded_ | Pending |
| gallery.html | _To be recorded_ | _To be recorded_ | Pending |
| contact.html | _To be recorded_ | _To be recorded_ | Pending |
| thank-you.html | _To be recorded_ | _To be recorded_ | Pending |

### Evidence placeholders

| Screenshot | Description |
|------------|-------------|
| `docs/evidence/html-validation-home.png` | W3C validator result for `index.html` |
| `docs/evidence/html-validation-contact.png` | W3C validator result for `contact.html` |

---

## CSS validation

### Method

Validate the main stylesheet using the W3C CSS Validation Service:

**Tool:** https://jigsaw.w3.org/css-validator/

**File tested:** `css/styles.css` (including imported layers)

### Results

| File | Errors | Warnings | Status |
|------|--------|----------|--------|
| styles.css | _To be recorded_ | _To be recorded_ | Pending |

### Evidence placeholders

| Screenshot | Description |
|------------|-------------|
| `docs/evidence/css-validation.png` | W3C CSS validator result for `css/styles.css` |

---

## Accessibility testing

### Method

Evaluate representative pages using the WAVE Web Accessibility Evaluation Tool:

**Tool:** https://wave.webaim.org/

**Pages to test:** Home (`index.html`), Destinations (`destinations.html`), Contact (`contact.html`)

**Procedure:**

1. Enter the live URL or use the WAVE browser extension on local files
2. Review errors, contrast errors, alerts, and structural features
3. Record summary counts and remediate any unintended issues

### Design intent

| Feature | Implementation |
|---------|----------------|
| Skip link | Present on all pages |
| Page language | `lang="en"` declared |
| Headings | Logical hierarchy (h1 → h2 → h3) |
| Alt text | Descriptive on all content images |
| Form labels | Explicit `<label>` associations; hints via `aria-describedby` |
| Colour contrast | Dark text on light background targeting WCAG 2.1 AA |
| Focus indicators | Visible `:focus-visible` outline on interactive elements |
| Tables | `<caption>` and `<th scope="">` used |
| Motion | `prefers-reduced-motion` respected |

### Results

| Page | Errors | Contrast errors | Alerts | Status |
|------|--------|-----------------|--------|--------|
| index.html | _To be recorded_ | _To be recorded_ | _To be recorded_ | Pending |
| destinations.html | _To be recorded_ | _To be recorded_ | _To be recorded_ | Pending |
| contact.html | _To be recorded_ | _To be recorded_ | _To be recorded_ | Pending |

### Evidence placeholders

| Screenshot | Description |
|------------|-------------|
| `docs/evidence/wave-home.png` | WAVE report for homepage |
| `docs/evidence/wave-destinations.png` | WAVE report for destinations page |
| `docs/evidence/wave-contact.png` | WAVE report for contact page |

---

## Issues found

The following issues were identified during development and pre-submission review (`SUBMISSION-REVIEW.md`):

| Issue | Page / area | Severity |
|-------|-------------|----------|
| Duplicate complementary landmarks without unique labels | `contact.html` | Medium |
| Redundant `for` attribute on nested consent checkbox label | `contact.html` | Low |
| Hidden checkbox remained in tab order | All pages (navigation) | Medium |
| Deprecated `clip: rect()` in visually-hidden utility | CSS (`base.css`) | Low |
| Redundant `aria-required` alongside native `required` | `contact.html` | Low |
| Low-contrast breadcrumb links on page hero | Inner pages | Medium |
| Low-contrast footer links on dark background | All pages | Medium |
| Mobile menu `aria-expanded` not updated without JavaScript | All pages (navigation) | Low — known limitation |

---

## Improvements made

| Issue | Resolution |
|-------|------------|
| Duplicate complementary landmarks | Named both `<aside>` elements with `aria-labelledby` on the contact page |
| Consent label redundancy | Removed redundant `for` attribute where input is nested inside label |
| Navigation keyboard access | Checkbox removed from tab order (`tabindex="-1"`, `aria-hidden="true"`); visible label receives focus with `aria-controls="main-nav"` |
| Screen reader utility | Updated `.visually-hidden` and `.nav-checkbox` to use `clip-path: inset(50%)`; removed deprecated `clip: rect()` |
| Form validation clarity | Placeholder `<option>` elements use `disabled selected hidden`; removed redundant `aria-required` |
| Breadcrumb contrast | Opacity increased from 75% to 88% on page hero breadcrumbs |
| Footer link contrast | Links use high-contrast white (`rgba(255,255,255,0.88–0.9)`) |
| Wide tables on small screens | Tables wrapped in `.table-wrap` with horizontal scroll |
| Motion sensitivity | `prefers-reduced-motion` applied to navigation animation and form transitions |

---

## Known limitations

- Contact form uses GET and redirects to `thank-you.html`; no server-side processing
- Photographs load from the Unsplash CDN; offline viewing shows alt text until images load
- CSS-only mobile menu toggle does not update `aria-expanded` dynamically

---

## Conclusion

NorthLight Iceland is structured as a multi-page, responsive, accessible static travel website. Formal validation and accessibility evidence should be captured using the placeholders above before final sign-off. Development review confirms intentional accessibility features and remediated markup issues documented in this report.
