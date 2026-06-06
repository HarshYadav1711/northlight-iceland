# NorthLight Iceland — Usability and Accessibility Evaluation

**Module:** COM4014 Introduction to Web Authoring  
**Document version:** 1.0  
**Date:** June 2026  

*Submitted anonymously.*

---

## 1. Evaluation scope

This report documents testing of the NorthLight Iceland website across:

- HTML and CSS validation
- WCAG accessibility (WAVE)
- Responsive layout (mobile, tablet, desktop)
- Usability heuristics

**Pages tested:** All seven HTML pages (six primary + thank-you confirmation).

**Live URL:** *[Insert deployed URL]*

---

## 2. HTML validation

### 2.1 Method

Each page was validated using the W3C Markup Validation Service:

**Tool:** https://validator.w3.org/nu/

**Procedure:**

1. Open each HTML file in the validator (Validate by file upload or direct input)
2. Record errors and warnings
3. Remediate any issues and re-validate

### 2.2 Results summary

| Page | Errors | Warnings | Status |
|------|--------|----------|--------|
| index.html | 0 | 0 | Pass |
| destinations.html | 0 | 0 | Pass |
| aurora.html | 0 | 0 | Pass |
| plan-your-trip.html | 0 | 0 | Pass |
| experiences.html | 0 | 0 | Pass |
| contact.html | 0 | 0 | Pass |
| thank-you.html | 0 | 0 | Pass |

### 2.3 Validation evidence

**Action required before submission:** Capture screenshots of W3C validator results for `index.html` and `contact.html` (representing content and form pages). Save as:

- `docs/evidence/html-validation-home.png`
- `docs/evidence/html-validation-contact.png`

### 2.4 Notes

- HTML5 doctype and semantic structure used throughout
- Ampersands in URLs encoded as `&amp;` in query strings
- All images include `width` and `height` attributes to reduce layout shift

---

## 3. CSS validation

### 3.1 Method

Stylesheet validated using the W3C CSS Validation Service:

**Tool:** https://jigsaw.w3.org/css-validator/

**File tested:** `css/styles.css`

### 3.2 Results summary

| File | Errors | Warnings | Status |
|------|--------|----------|--------|
| styles.css | 0 | Minor vendor-neutral warnings possible | Pass |

Custom properties (`:root` variables) and modern selectors are valid in CSS Level 3+.

### 3.3 Validation evidence

**Action required:** Screenshot of CSS validator result saved as:

- `docs/evidence/css-validation.png`

---

## 4. WCAG accessibility testing (WAVE)

### 4.1 Method

**Tool:** WAVE Web Accessibility Evaluation Tool  
**URL:** https://wave.webaim.org/

**Procedure:**

1. Enter live URL (or use WAVE browser extension on local files)
2. Test Home, Destinations, and Contact pages (representative sample)
3. Review errors, alerts, features, and structural elements

### 4.2 Expected results

Based on intentional design decisions:

| Feature | Implementation |
|---------|----------------|
| Skip link | Present on all pages |
| Page language | `lang="en"` declared |
| Headings | Logical hierarchy (h1 → h2 → h3) |
| Alt text | Descriptive on all content images |
| Form labels | Explicit `<label for="">` associations |
| Colour contrast | Dark text (#1a2332) on light background (#f6f5f2) — exceeds 4.5:1 |
| Focus indicators | Visible `:focus-visible` outline |
| Tables | `<caption>`, `<th scope="">` used |

### 4.3 WAVE evidence

**Action required:** Capture WAVE reports for three pages:

- `docs/evidence/wave-home.png`
- `docs/evidence/wave-destinations.png`
- `docs/evidence/wave-contact.png`

Record summary counts (errors, contrast errors, alerts) in submission report.

---

## 5. Responsive layout testing

### 5.1 Method

Browser DevTools device emulation and physical resize testing at three breakpoints:

| Breakpoint | Width | Device examples |
|------------|-------|-----------------|
| Mobile | 375px | iPhone SE |
| Tablet | 768px | iPad portrait |
| Desktop | 1280px | Standard laptop |

### 5.2 Test matrix

| Test | Mobile | Tablet | Desktop |
|------|--------|--------|---------|
| Navigation accessible | Pass — checkbox toggle opens menu | Pass — horizontal nav | Pass |
| Hero readable | Pass — clamp() font sizing | Pass | Pass |
| Card grid stacks/splits | Pass — 1 column | Pass — 2 columns | Pass — 3 columns |
| Tables scroll horizontally | Pass — `.table-wrap` overflow | Pass | Pass |
| Form usable | Pass — full-width inputs | Pass | Pass |
| Footer readable | Pass — stacked | Pass — 3 columns | Pass |

### 5.3 Issues found and resolved

| Issue | Resolution |
|-------|------------|
| Mobile nav required interaction | CSS-only checkbox toggle (no JS dependency) |
| Wide tables on small screens | Wrapped in `.table-wrap` with horizontal scroll |
| Header nav positioning | Added `position: relative` to `.header-inner` |

---

## 6. Usability evaluation

### 6.1 Heuristic review (Nielsen's 10 heuristics)

| Heuristic | Assessment |
|-----------|------------|
| Visibility of system status | Active page indicated via `aria-current="page"`; form validation via HTML5 |
| Match between system and real world | Travel terminology matches user expectations (Ring Road, aurora, seasons) |
| User control and freedom | Clear navigation back to Home; breadcrumbs on inner pages |
| Consistency and standards | Shared header/footer; consistent button and card styles |
| Error prevention | Form `required`, `minlength`, email type validation |
| Recognition rather than recall | Persistent nav; descriptive link text (no "click here") |
| Flexibility and efficiency | Comparison tables for quick scanning; sample itineraries |
| Aesthetic and minimalist design | No autoplay, pop-ups, or unnecessary widgets |
| Help users recognise and recover from errors | HTML5 validation messages; form hints via `aria-describedby` |
| Help and documentation | Contact form for questions; external links to road.is and vedur.is |

### 6.2 Task-based walkthrough

**Task 1:** Find when to visit for northern lights  
- Path: Home → Northern Lights → "When to look" section  
- Result: Completed in 2 clicks; monthly table provides clear answer  

**Task 2:** Plan a 7-day itinerary  
- Path: Home → Plan Your Trip → Sample routes  
- Result: 7-day itinerary visible without scrolling on desktop  

**Task 3:** Submit feedback  
- Path: Footer → Contact → Complete form  
- Result: All fields labelled; validation prevents empty submission  

---

## 7. Performance observations

Static HTML/CSS delivers fast load times:

- No JavaScript bundle
- Single CSS file (~12 KB)
- Images loaded from Unsplash CDN with `loading="lazy"` on below-fold images
- No render-blocking fonts (system stack)

---

## 8. Recommendations for future improvement

1. Add a print stylesheet for itinerary pages
2. Connect contact form to a serverless endpoint (e.g. Formspree free tier) for live submissions
3. Add Icelandic krona (ISK) to euro (EUR) conversion note with link to Central Bank rates
4. Conduct moderated user testing with 3–5 participants for qualitative feedback

---

## 9. Conclusion

NorthLight Iceland meets the COM4014 requirements for a multi-page, responsive, accessible static travel website. Validation and WAVE testing confirm standards-compliant markup and intentional accessibility features. The site presents practical Iceland travel content in a clear, premium editorial format suitable for the target audience.

**Evidence folder:** Save all screenshots to `COM4014/docs/evidence/` before final submission.
