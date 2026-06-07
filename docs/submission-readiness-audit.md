# Submission readiness audit

**Date:** 7 June 2026  
**Scope:** HTML, CSS, documentation, `README.md`, GitHub Pages deployment workflow  
**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

**Method:** Inspected all eight HTML files and four CSS layers; ran `npx html-validate "*.html"` (0 errors); reviewed root and `docs/` documentation; checked `.github/workflows/pages.yml`; cross-checked against `SUBMISSION-REVIEW.md` and `docs/evaluation-report.md` (v2.0).

**Repository polish (same day):** Documentation alignment items below (breakpoints, references URLs, README structure, form field list, homepage copy, stale audit notes, `COM4014/` removal) were applied after this audit was written.

**Verdict:** The website and core documentation are **submission-ready** as a static HTML/CSS academic project. No blocking code defects were found. Remaining gaps are documentation accuracy, optional manual test evidence, and operational dependencies (CDN, demo form) that are already disclosed.

---

## Strengths

### Website (HTML and CSS)

| Area | Finding |
|------|---------|
| Markup validity | `html-validate` reports **0 errors** on all 8 HTML files (`index.html` through `template.html`). |
| Page completeness | Seven public pages plus `thank-you.html` and `template.html`; primary and footer navigation are consistent across pages. |
| Internal linking | All internal page links and cross-page hash anchors (`destinations.html#akureyri`, `experiences.html#northern-lights`, etc.) target existing IDs. |
| Images | 29 `<img>` elements across five content pages; each has descriptive `alt`, `width`, and `height`. Twelve unique Unsplash photos documented in `docs/image-attributions.md`. |
| Forms | Contact form has visible labels, `aria-describedby` hints, HTML5 validation attributes, and a required consent checkbox. |
| Tables | Three data tables use `<caption>`, `th scope`, and `.table-wrap` for horizontal scroll. |
| Accessibility (implemented) | Skip link, `lang="en"`, one `<h1>` per page, `:focus-visible`, `prefers-reduced-motion`, labelled landmarks, nav toggle pattern (`tabindex="-1"` / `aria-hidden` on checkbox; `tabindex="0"` / `aria-controls` on label). |
| CSS architecture | Single entry point (`css/styles.css`) importing `tokens`, `base`, `layout`, `components`; breakpoints at 600px, 768px, and 900px. |
| Screen reader utility | `.visually-hidden` and `.nav-checkbox` use `clip-path: inset(50%)` without deprecated `clip: rect()`. |
| Confirmation page | `thank-you.html` includes `<meta name="robots" content="noindex">`. |

### Documentation

| Area | Finding |
|------|---------|
| Submission sign-off | `SUBMISSION-REVIEW.md` records completed pre-submission checklist items and known limitations. |
| Evaluation report (v2.0) | `docs/evaluation-report.md` clearly separates **completed findings** (Part A) from **manual verification checklists** (Part B) without fabricated test results. |
| Evidence guide | `docs/evidence/README.md` defines expected screenshot filenames and capture procedures. |
| Specification and references | `docs/website-specification.md`, `docs/references.md`, `docs/image-attributions.md`, and `docs/production-review.md` provide academic and maintainer context. |
| Attribution | Photographer credits on `contact.html#attributions`, gallery footer note, and Harvard-style bibliography in `docs/references.md`. |

### Deployment

| Area | Finding |
|------|---------|
| Workflow | `.github/workflows/pages.yml` deploys on push to `main` or `master` via GitHub Actions (`upload-pages-artifact` + `deploy-pages`). |
| Static suitability | No build step required; repository root contains all assets needed for the live site (`*.html`, `css/`). |
| README | Live URL, local setup, deployment instructions, and technology stack are documented. |

---

## Risks

Risks below are **disclosed or acceptable** for a demo static site unless assessors require live form handling or offline assets.

| Risk | Detail | Severity |
|------|--------|----------|
| External CDN dependency | All photographs load from `images.unsplash.com`; fonts from `fonts.googleapis.com` / `fonts.gstatic.com`. Blocked or offline networks show `alt` text and system font fallbacks. | Medium — operational |
| Demo form (`method="get"`) | `contact.html` submits via GET to `thank-you.html`; field values appear in the URL and browser history. Documented in README, evaluation report, and submission review. | Low for demo; **high if used with real user data** |
| CSS-only menu state | `aria-expanded` is not updated when the mobile menu opens or closes. Documented as a known limitation. | Low — accepted |
| No favicon or custom 404 | No `<link rel="icon">`, `404.html`, or `robots.txt`. Browsers show a generic tab icon; unknown paths use default GitHub Pages behaviour. | Low — cosmetic / SEO |
| Full-repository deploy | Workflow uploads `path: .` — the entire repository root, including `docs/`, `COM4014/`, and `template.html`, is published under the Pages URL. Not a runtime defect but exposes internal documentation paths publicly. | Low–medium — assessor confusion |
| Manual test evidence not captured | Part B of `docs/evaluation-report.md` (cross-browser, WAVE, W3C validators, screenshots) remains **Pending manual verification**. No fabricated results are filed. | Medium — documentation completeness for assessors who require evidence |
| Third-party availability | Live site depends on GitHub Pages, Unsplash, and Google Fonts remaining reachable. | Low |

---

## Remaining issues

Only **actual** inconsistencies and gaps identified in this audit. None block static site function.

### Code and content

| Issue | Location | Detail | Status |
|-------|----------|--------|--------|
| Homepage destination count mismatch | `index.html` vs `destinations.html` / README | Homepage shows four featured cards (Akureyri omitted); five regions on Destinations page. | **Resolved** — lead copy and README clarify four featured regions vs five on Destinations page. |
| `template.html` publicly reachable | Deployed site | Not linked from navigation but available at `/template.html` with placeholder meta description. | Open — acceptable for development shell. |

### Documentation accuracy

| Issue | Location | Detail | Status |
|-------|----------|--------|--------|
| Breakpoint values conflict | `docs/website-specification.md` vs CSS | Spec previously cited 768px / 960px breakpoints. | **Resolved** — spec aligned to 600px / 768px / 900px. |
| Form layout breakpoint wording | `SUBMISSION-REVIEW.md` vs CSS | Form field pairs vs aside layout breakpoints conflated. | **Resolved** — submission review distinguishes 600px field pairs and 768px aside layout. |
| README form and structure gaps | `README.md` | Consent field and docs inventory omitted. | **Resolved** — README updated. |
| Incorrect Unsplash URLs | `docs/references.md` | Bibliography URLs used duplicated `photo-` prefix. | **Resolved** — URLs match `docs/image-attributions.md`. |
| Stale audit documents | `documentation-consistency-audit.md`, `final-review.md`, `production-review.md` | Outdated nav, evidence, and noindex notes. | **Resolved** — post-audit notes and corrections applied. |
| Duplicate course folder | `COM4014/docs/` | Superseded copies of root `docs/` files. | **Resolved** — duplicate files removed. |

### Verification status (not defects)

| Item | Status |
|------|--------|
| Cross-browser manual testing (Firefox, Edge) | Pending manual verification — per `docs/evaluation-report.md` § B.1 |
| WAVE evaluation | Pending manual verification — § B.5 |
| W3C Nu HTML / CSS validators | Pending manual verification — § B.3–B.4 (supplementary to `html-validate`) |
| Evidence screenshots (12 files) | Pending manual verification — `docs/evidence/` contains guide only |

---

## Recommended final actions

Actions are limited to **documentation alignment**, **evidence capture**, and **submission hygiene**. No redesigns or new features.

### Before submission (recommended)

1. **Complete manual verification** — Work through `docs/evaluation-report.md` Part B; record browser versions and tick checklists when done.
2. **Capture evidence screenshots** — Follow `docs/evidence/README.md`; save PNGs with the documented filenames (optional if results are recorded elsewhere).
3. **Confirm GitHub Pages settings** — Repository Settings → Pages → Source: GitHub Actions; verify the live URL matches README and documentation.

### Already acceptable without action

- Demo GET form and CDN-hosted images/fonts (documented limitations).
- Missing favicon, `404.html`, and `robots.txt` (noted in reviews; not required for static coursework submission).
- `aria-expanded` not updated without JavaScript (documented known limitation).
- `html-validate` pass — no remediation required unless W3C Nu Validator finds supplementary issues during manual verification.

---

## Summary table

| Category | Submission-ready? | Notes |
|----------|-------------------|-------|
| HTML / CSS codebase | **Yes** | 0 `html-validate` errors; features implemented as documented |
| Accessibility (implemented) | **Yes** | Known CSS-only menu limitation disclosed |
| Deployment workflow | **Yes** | Functional; publishes full repository root |
| Core documentation | **Yes** | `SUBMISSION-REVIEW.md` + `evaluation-report.md` v2.0 are coherent |
| Supplementary evidence | **Partial** | Checklists defined; screenshots and multi-browser runs pending |
| Documentation consistency | **Yes** | Breakpoints, references, README, and audit cross-references aligned in repository polish pass |

**Overall:** Safe to submit as a complete static website project. Prioritise documentation fixes and optional evidence capture if the assessment rubric requires recorded browser or WAVE testing.

---

*This audit identifies actual issues and risks only. No website code was modified.*
