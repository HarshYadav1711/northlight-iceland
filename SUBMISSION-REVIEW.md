# NorthLight Iceland — Final Submission Review

Review completed: June 2026

## Validation summary

| Check | Result |
|-------|--------|
| HTML (`html-validate` on all 8 pages) | Pass — 0 errors |
| CSS structure | Pass — layered imports, no invalid properties |
| Responsive layouts (375px / 768px / 1280px) | Pass — verified in browser |
| Cross-browser | Layout uses standard CSS (flexbox, grid, custom properties); tested in Chromium-based browser. Firefox and Edge support the same features used. |

## Pages included

- `index.html` — Homepage
- `destinations.html` — Five destination guides
- `experiences.html` — Five experience guides
- `travel-guide.html` — Practical planning sections
- `gallery.html` — Image grid with captions
- `contact.html` — Feedback form
- `thank-you.html` — Form confirmation
- `template.html` — Reusable page shell

---

## Improvements made in this review

### HTML validation fixes (`contact.html`)

- Named both `<aside>` landmarks with `aria-labelledby` so complementary regions are unique (fixes `unique-landmark` rule).
- Removed redundant `for` attribute on the consent checkbox label where the input is nested inside the label.
- Added `id="attributions-heading"` for the attributions section heading.

### Accessibility (WAVE-oriented)

- **Navigation menu:** Hidden checkbox removed from tab order (`tabindex="-1"`, `aria-hidden="true"`). Visible label receives keyboard focus (`tabindex="0"`) with `aria-controls="main-nav"`. Decorative bars marked `aria-hidden="true"`.
- **Screen reader utility class:** Updated `.visually-hidden` and `.nav-checkbox` hiding to modern `clip-path: inset(50%)` instead of deprecated `clip: rect()`.
- **Form:** Removed redundant `aria-required` where native `required` is present. Placeholder `<option>` elements use `disabled selected hidden` for clearer validation. Removed textarea placeholder to avoid duplicate labelling and low-contrast placeholder text.
- **Landmarks:** Contact page asides uniquely named; all pages retain skip link, `<main>`, labelled navigation, and one `<h1>` per page.
- **Contrast:** Breadcrumb links on page hero increased from 75% to 88% opacity. Footer links use high-contrast white (`rgba(255,255,255,0.88–0.9)`) instead of light cyan on dark blue.
- **Focus:** Global `:focus-visible` outline retained; form fields, buttons, logo, nav links, and card links have visible focus rings.
- **Motion:** `prefers-reduced-motion` respected for nav animation and form transitions.

### CSS correctness

- Removed invalid `tabindex` property accidentally considered for CSS (focus handled in HTML instead).
- Footer link selectors clarified to avoid contrast regressions between footer nav and footer bottom links.

### Visual / responsive verification

- **Mobile (~375px):** Single-column stacks, hamburger menu, readable form fields, hero and page hero scale correctly.
- **Tablet (768px):** Form two-column rows activate; destination cards use 2-column grid.
- **Desktop (1280px):** Full navigation bar, form aside + form panel side-by-side, 3-column card grids where defined.

---

## Known limitations (acceptable for submission)

- **Form processing:** Contact form uses `method="get"` and redirects to `thank-you.html` for demonstration; no server-side handling.
- **External images:** Photographs load from Unsplash CDN; offline viewing shows alt text until images load.
- **Mobile menu state:** CSS-only toggle; `aria-expanded` is not updated without JavaScript (label text remains “Toggle navigation menu”).
- **Browser testing:** Automated visual review run in Chromium; Firefox and Edge were not blocked by any vendor-specific CSS in this project.

---

## Pre-submission checklist

- [x] All pages share header, footer, and stylesheet
- [x] Every form field has a visible label
- [x] Images include descriptive `alt` text
- [x] Tables include `<caption>` and `scope` attributes
- [x] External links use `rel="noopener noreferrer"`
- [x] Image attributions listed on Contact page
- [x] No HTML validation errors
