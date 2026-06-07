# Submission readiness audit

**Date:** 7 June 2026  
**Scope:** HTML, CSS, documentation, `README.md`, GitHub Pages deployment workflow  
**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

**Method:** Inspected all eight HTML files and four CSS layers; ran `npx html-validate "*.html"` (0 errors); reviewed root and `docs/` documentation; checked `.github/workflows/pages.yml`; cross-checked against `SUBMISSION-REVIEW.md` and `docs/evaluation-report.md` (v2.0).

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

| Issue | Location | Detail |
|-------|----------|--------|
| Homepage destination count mismatch | `index.html` vs `destinations.html` / README | Homepage lead copy says “**Four routes**” and shows four destination cards (Akureyri omitted). Destinations page and README state **five** regions. |
| `template.html` publicly reachable | Deployed site | Not linked from navigation but available at `/template.html` with placeholder meta description. |

### Documentation accuracy

| Issue | Location | Detail |
|-------|----------|--------|
| Breakpoint values conflict | `docs/website-specification.md` vs CSS / README | Spec cites mobile &lt;768px, tablet 768–959px with horizontal nav, desktop 960px+. Implementation uses **600px**, **768px**, **900px**; horizontal nav starts at **900px**. README correctly cites 600px and 900px. |
| Form layout breakpoint wording | `SUBMISSION-REVIEW.md` vs `css/components.css` | Submission review states form two-column rows activate at tablet **768px**; `.form-row--2` activates at **600px** (aside + panel layout is at 768px). |
| README omits consent field | `README.md` § Feedback Form | Lists five fields; `contact.html` also requires a **consent checkbox** documented in `docs/website-specification.md`. |
| README project tree incomplete | `README.md` § Project Structure | Omits `docs/evidence/`, `docs/documentation-consistency-audit.md`, `docs/final-review.md`, and other files present in `docs/`. |
| Incorrect Unsplash URLs | `docs/references.md` | Twelve image bibliography entries use `/photos/photo-{id}` paths; working Unsplash page URLs and `docs/image-attributions.md` use `/photos/{id}` without the duplicated `photo-` prefix. |
| Stale consistency audit | `docs/documentation-consistency-audit.md` | Dated 7 June 2026; Issue 1 states navigation accessibility fixes are **not implemented**. They are now present on all eight HTML pages. |
| Stale final review note | `docs/final-review.md` § Testing evidence | States `docs/evidence/` “does not exist”; folder now exists with `README.md` but **no screenshots** yet. |
| Stale production-review note | `docs/production-review.md` § Remaining recommendations | Suggests adding `noindex` to `thank-you.html`; that meta tag is already in place. |
| Duplicate course folder | `COM4014/docs/` | Contains older copies of `evaluation-report.md`, `website-specification.md`, and `references.md`. Not linked from the site but deployed alongside the live project. |

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
3. **Fix `docs/references.md` image URLs** — Remove the erroneous `photo-` prefix from Unsplash bibliography links so they match `docs/image-attributions.md`.
4. **Align breakpoint documentation** — Update `docs/website-specification.md` (and the tablet form note in `SUBMISSION-REVIEW.md`) to match CSS breakpoints, or add an explicit note that the spec describes design intent and CSS uses 600/768/900px.
5. **Update `README.md`** — Add the consent checkbox to the form field list; extend the project structure to include `docs/evidence/` and other existing `docs/` files.
6. **Resolve homepage copy** — Either change “Four routes” to five and add Akureyri to the featured grid, or clarify in README that the homepage highlights four featured regions while the Destinations page covers all five.

### Submission hygiene (optional but reduces assessor confusion)

7. **Address `COM4014/` duplication** — Remove the folder, move it outside the repo, or exclude it from the Pages artifact if assessors should not see duplicate docs at `/COM4014/docs/`.
8. **Refresh stale audit documents** — Add a short “superseded” note to `docs/documentation-consistency-audit.md` or update Issue 1 to reflect current nav markup; correct the evidence-folder line in `docs/final-review.md`.
9. **Confirm GitHub Pages settings** — Repository Settings → Pages → Source: GitHub Actions; verify the live URL matches README and documentation.

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
| Documentation consistency | **Partial** | Breakpoints, references URLs, and two stale audit files need alignment |

**Overall:** Safe to submit as a complete static website project. Prioritise documentation fixes and optional evidence capture if the assessment rubric requires recorded browser or WAVE testing.

---

*This audit identifies actual issues and risks only. No website code was modified.*
