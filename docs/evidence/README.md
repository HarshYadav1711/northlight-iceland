# Test evidence — NorthLight Iceland

This folder holds **screenshots captured during manual testing**. It is intentionally empty until real evidence is recorded. Do not commit placeholder or fabricated images.

Evidence supports the manual verification checklists in [`docs/evaluation-report.md`](../evaluation-report.md) (Part B). Screenshots are **optional** for submission if results are documented elsewhere, but filenames below match the evaluation report so assessors can find evidence quickly.

---

## What belongs here

Only genuine captures from browsers, DevTools, or online validators. Use **PNG** format and the exact filenames in the tables below unless you add a clearly named supplement (e.g. `browser-chrome-home-2026-06-07.png` is acceptable if the base name is preserved).

### Browser testing (3 files)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `browser-chrome-home.png` | Homepage (`index.html`) full viewport in Google Chrome at **1280px** width | `evaluation-report.md` § B.1 |
| `browser-firefox-nav.png` | Primary navigation and **open mobile menu** in Mozilla Firefox at **375px** width | `evaluation-report.md` § B.1 |
| `browser-edge-form.png` | Contact form (`contact.html`) showing **browser validation** for invalid or empty required fields in Microsoft Edge | `evaluation-report.md` § B.1 |

### Responsive layout (3 files)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `responsive-mobile-375.png` | Homepage at **375px** width (single column, hamburger visible) | `evaluation-report.md` § B.2 |
| `responsive-tablet-768.png` | Destinations page (`destinations.html`) at **768px** width (two-column cards or feature layout) | `evaluation-report.md` § B.2 |
| `responsive-desktop-1280.png` | Travel Guide page (`travel-guide.html`) at **1280px** width (full horizontal nav, multi-column content) | `evaluation-report.md` § B.2 |

### W3C HTML validation — supplementary (2 files)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `html-validation-home.png` | [W3C Nu Validator](https://validator.w3.org/nu/) results screen for `index.html` (show errors/warnings summary) | `evaluation-report.md` § B.3 |
| `html-validation-contact.png` | W3C Nu Validator results screen for `contact.html` | `evaluation-report.md` § B.3 |

**Note:** Automated `html-validate` (0 errors) is documented in `evaluation-report.md` § A.1 and `SUBMISSION-REVIEW.md`. W3C screenshots are an optional supplementary check.

### W3C CSS validation (1 file)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `css-validation.png` | [W3C CSS Validator](https://jigsaw.w3.org/css-validator/) results for `css/styles.css` by direct input or file upload | `evaluation-report.md` § B.4 |

### WAVE accessibility evaluation (3 files)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `wave-home.png` | [WAVE](https://wave.webaim.org/) summary panel for homepage (live URL or local file) | `evaluation-report.md` § B.5 |
| `wave-destinations.png` | WAVE summary for `destinations.html` | `evaluation-report.md` § B.5 |
| `wave-contact.png` | WAVE summary for `contact.html` | `evaluation-report.md` § B.5 |

### Optional — asset migration (not in evaluation report)

| Filename | What to capture | Referenced in |
|----------|-----------------|---------------|
| `before-cdn-migration.png` | Representative page before self-hosting images | `docs/assets-audit.md` |
| `after-cdn-migration.png` | Same view after local images are in place | `docs/assets-audit.md` |

Add these only if you perform the CDN-to-local migration described in the assets audit.

---

## How to capture evidence

### General guidelines

1. **Use real sessions** — capture from the live site (`https://harshyadav1711.github.io/northlight-iceland/`) or from a local server (`python -m http.server 8080` at the repo root). Network access is required for Unsplash images and Google Fonts.
2. **Record context in the image** — include the browser chrome or DevTools device bar where helpful so viewport width and browser name are visible.
3. **One concern per screenshot** — avoid cropping out the area that proves the check (e.g. validation message, WAVE error count, menu open state).
4. **No editing beyond crop** — do not alter results to show a pass or fail that did not occur.
5. **Update the evaluation report** — after capture, tick the relevant checklist in `docs/evaluation-report.md` Part B and note browser versions or validator counts in the tables there.

### Browser and responsive screenshots

| Step | Action |
|------|--------|
| 1 | Open the target page and set viewport (DevTools → Toggle device toolbar, or resize window to exact width). |
| 2 | For mobile menu shots: use **375px** width, tab to or click the menu toggle, capture with menu **open**. |
| 3 | For form validation: submit the contact form with required fields empty or invalid; capture the **native browser** validation UI. |
| 4 | Save with the filename from the table above into this directory (`docs/evidence/`). |

**Suggested tools:** Built-in OS screenshot, browser DevTools screenshot, or Firefox/Chrome full-page capture where appropriate.

### Validator and WAVE screenshots

| Tool | URL | Input |
|------|-----|-------|
| W3C Nu HTML Validator | https://validator.w3.org/nu/ | Upload HTML file or paste markup |
| W3C CSS Validator | https://jigsaw.w3.org/css-validator/ | Validate by URI (`css/styles.css` on live site) or file upload |
| WAVE | https://wave.webaim.org/ | Enter page URL, or use the WAVE browser extension on local files |

Capture the **summary panel** showing error, warning, contrast, and alert counts. If a page fails unexpectedly, file the screenshot anyway and record the issue in `evaluation-report.md`.

---

## Where this folder is referenced

| Document | How it uses `docs/evidence/` |
|----------|------------------------------|
| [`docs/evaluation-report.md`](../evaluation-report.md) | Part B manual verification checklists; optional evidence tables (§ B.1–B.6); evidence capture summary |
| [`SUBMISSION-REVIEW.md`](../../SUBMISSION-REVIEW.md) | Submission sign-off; points to evaluation report for detailed testing |
| [`docs/production-review.md`](../production-review.md) | Recommends capturing evidence before academic submission |
| [`docs/final-review.md`](../final-review.md) | Notes evidence folder status in pre-submission review |
| [`docs/assets-audit.md`](../assets-audit.md) | Suggests before/after screenshots if images are self-hosted |
| [`docs/documentation-consistency-audit.md`](../documentation-consistency-audit.md) | Records whether evidence exists vs documentation claims |
| [`docs/submission-readiness-audit.md`](../submission-readiness-audit.md) | Pre-submission readiness assessment and evidence status |

This README is the **canonical filename list** for evaluation evidence. If you add screenshots, keep names aligned with `evaluation-report.md` or update both documents together.

---

## Folder status

| Item | Status |
|------|--------|
| Expected files (evaluation report) | 12 PNG screenshots |
| Files currently present | None — capture during manual verification |
| Placeholder images | Not used — do not add fake or generated screenshots |

When all intended captures are complete, optionally add a one-line note to `evaluation-report.md` § B.6 stating the capture date and which files are present.
