# NorthLight Iceland — Website Specification

**Module:** COM4014 Introduction to Web Authoring  
**Project:** NorthLight Iceland destination website  
**Document version:** 1.0  
**Date:** June 2026  

*This document is submitted anonymously in accordance with assessment requirements.*

---

## 1. Executive summary

NorthLight Iceland is a static travel website that helps independent visitors plan trips to Iceland. The site prioritises clear route guidance, season-aware advice, and accessible presentation over booking functionality or promotional content.

The website comprises six HTML pages (five content pages plus one contact form page), one shared CSS stylesheet, and royalty-free photography with full attribution.

**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

---

## 2. Site objective and target audience

### 2.1 Objective

To provide trustworthy, actionable travel information for Iceland that:

- Helps visitors choose routes matched to trip length and season
- Explains northern lights viewing with realistic expectations
- Supports informed planning (driving, budget, packing)
- Meets web accessibility and responsive design standards

### 2.2 Target audience

| Segment | Characteristics | Primary needs |
|---------|-----------------|---------------|
| First-time visitors | 1–2 week trips, likely renting a car | Route suggestions, season comparison, driving safety |
| Returning travellers | Focus on specific regions or aurora | Deeper regional content, seasonal activity tables |
| Accessibility-conscious users | Screen reader, keyboard, or mobile users | Semantic markup, contrast, skip links, form labels |

**Tone:** Natural, concise, confident — editorial travel brand, not promotional brochure.

---

## 3. Provisional site structure

```
NorthLight Iceland
├── Home (index.html)
│   ├── Hero + value proposition
│   ├── Featured regions
│   └── Season overview CTA
├── Destinations (destinations.html)
│   ├── Reykjavík
│   ├── Golden Circle
│   ├── South Coast
│   ├── Snæfellsnes
│   └── North Iceland + comparison table
├── Northern Lights (aurora.html)
│   ├── Aurora science (brief)
│   ├── Timing and conditions
│   └── Clothing and expectations
├── Plan Your Trip (plan-your-trip.html)
│   ├── Seasons
│   ├── Driving
│   ├── Budget table
│   └── Sample itineraries
├── Experiences (experiences.html)
│   ├── Guided activities
│   ├── Seasonal availability table
│   └── Free/low-cost options
└── Contact (contact.html)
    ├── Accessible feedback form
    └── Image attributions
```

### 3.1 Navigation model

- Persistent header with primary navigation on all pages
- Breadcrumbs on inner pages
- Footer navigation duplicate for wayfinding
- Skip link to main content on every page

---

## 4. Functional specification

### 4.1 Technical requirements

| Requirement | Implementation |
|-------------|----------------|
| Markup | HTML5 semantic elements (`header`, `nav`, `main`, `section`, `article`, `footer`, `form`) |
| Styling | Single external CSS file (`css/styles.css`), mobile-first media queries |
| Scripting | None — CSS-only mobile navigation toggle |
| Frameworks | None |
| Hosting | Static hosting (GitHub Pages) |

### 4.2 Responsive breakpoints

| Viewport | Layout behaviour |
|----------|------------------|
| Mobile (&lt; 768px) | Single column, hamburger-style nav (checkbox toggle), stacked cards |
| Tablet (768px – 959px) | Two-column grids, horizontal navigation |
| Desktop (960px+) | Three-column card grids, max-width container (72rem) |

### 4.3 Contact form specification

| Field | Type | Validation |
|-------|------|------------|
| Full name | Text | Required, 2–80 characters |
| Email | Email | Required, valid email format |
| Enquiry type | Radio group | Required selection |
| Travel month | Select | Optional |
| Message | Textarea | Required, 20–2000 characters |
| Consent | Checkbox | Required |

Form submits via GET to `thank-you.html` for demonstration. Production deployment would use POST to a server endpoint or form service.

### 4.4 Accessibility features

- Skip navigation link
- `lang="en"` on `<html>`
- Descriptive page titles and meta descriptions
- Meaningful alt text on all images
- Visible focus indicators (`:focus-visible`)
- Form labels associated with inputs; fieldset/legend for radio group
- `aria-current="page"` on active nav links
- `prefers-reduced-motion` media query
- Table headers with `scope` attributes
- Colour contrast targeting WCAG 2.1 AA

---

## 5. Visual design specification

### 5.1 Brand identity

- **Name:** NorthLight Iceland
- **Tagline:** Travel with clarity
- **Personality:** Premium, calm, editorial — trustworthy guide rather than tour operator

### 5.2 Colour palette

| Token | Hex | Usage |
|-------|-----|-------|
| Background | `#f6f5f2` | Page background |
| Surface | `#ffffff` | Cards, header |
| Text | `#1a2332` | Body copy |
| Accent | `#2d6a6a` | Links, eyebrows, CTA band |
| Highlight | `#b8924a` | Primary buttons |

### 5.3 Typography

- **Display:** Georgia (headings, logo)
- **Body:** System UI stack (Segoe UI, Roboto, sans-serif)
- Base size: 17px (1.0625rem), line-height 1.65

### 5.4 Imagery

Royalty-free photographs from Unsplash. Full attributions on Contact page and in References document.

---

## 6. Competitive comparison

Three established Iceland travel websites were reviewed to inform structure and differentiation.

### 6.1 Comparison summary

| Criterion | Visit Iceland (visiticeland.com) | Guide to Iceland (guidetoiceland.is) | Iceland Travel (icelandtravel.is) | NorthLight Iceland |
|-----------|----------------------------------|--------------------------------------|-----------------------------------|-------------------|
| Primary purpose | Official tourism promotion | Booking marketplace + guides | Package tours and tailor-made trips | Independent planning guides |
| Navigation depth | Deep, multi-level mega-menu | Commerce-heavy, many categories | Service-focused | Flat, six-page structure |
| Content tone | Inspirational marketing | Mixed editorial and sales | Sales-oriented | Practical, editorial |
| Accessibility | Large site; variable page quality | Complex JS interactions | Standard corporate | WCAG-conscious by design |
| Mobile experience | Responsive, image-heavy | Responsive, ad/booking focus | Responsive | Mobile-first, lightweight |
| Unique strength | Authority and breadth | Comprehensive booking | Expert-led packages | Clarity and realistic planning |

### 6.2 Differentiation strategy

NorthLight Iceland deliberately avoids:

- Booking engines and payment flows
- Heavy JavaScript carousels or pop-ups
- Generic stock phrases ("once-in-a-lifetime", "hidden gem")

Instead it offers:

- Route-first itineraries tied to driving times
- Honest aurora expectations
- Structured comparison tables
- Accessible, fast-loading static pages

---

## 7. Content sources and references

Factual content draws on publicly available tourism information. External links to official resources:

- Icelandic Road and Coastal Administration (road.is)
- Icelandic Met Office (vedur.is)

Full references in AU Harvard format: see `docs/references.md`.

---

## 8. Deployment

The website is deployed to GitHub Pages from the `COM4014/NorthLight-Iceland` directory.

**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

---

## 9. File inventory

| File | Purpose |
|------|---------|
| `index.html` | Home page |
| `destinations.html` | Regional guides |
| `aurora.html` | Northern lights guide |
| `plan-your-trip.html` | Planning and budgets |
| `experiences.html` | Activities |
| `contact.html` | Form + attributions |
| `thank-you.html` | Form confirmation |
| `css/styles.css` | Shared styles |
| `docs/website-specification.md` | This document |
| `docs/evaluation-report.md` | Testing and evaluation |
| `docs/references.md` | AU Harvard references |

---

## 10. Submission checklist

- [x] Website specification document
- [x] Minimum 5 content pages + form page
- [x] HTML and CSS only
- [x] Responsive layouts (mobile, tablet, desktop)
- [x] Accessible markup and design
- [x] Image attributions
- [x] Anonymous submission (no student name)
- [x] AU Harvard references
- [ ] Live URL confirmed in report
- [ ] ZIP archive of website files
- [ ] HTML/CSS validation screenshots
- [ ] WAVE accessibility report screenshots
