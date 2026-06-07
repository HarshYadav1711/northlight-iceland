# NorthLight Iceland — Website Specification

**Document version:** 1.0  
**Date:** June 2026  
**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

---

## Website objectives

NorthLight Iceland is a static destination website that helps independent travellers plan trips to Iceland with clarity and confidence. The site prioritises practical planning information — drive times, seasonal access, realistic activity expectations — over promotional content or booking functionality.

Primary objectives:

- Present regional guides and experience overviews that support route planning
- Offer structured travel advice covering transport, budget, safety, and packing
- Showcase Iceland through an accessible image gallery with full attribution
- Provide a contact form for visitor feedback and travel enquiries
- Deliver a fast, responsive, standards-compliant experience without JavaScript

The site does not sell tours or packages. Content is editorial and informational, written in a direct, trustworthy tone.

---

## Target audience

| Segment | Characteristics | Primary needs |
|---------|-----------------|---------------|
| First-time visitors | One- to two-week trips, often self-driving | Route suggestions, season comparison, driving safety |
| Returning travellers | Focus on specific regions or aurora viewing | Deeper regional content, seasonal activity guidance |
| Accessibility-conscious users | Screen reader, keyboard, or mobile users | Semantic markup, sufficient contrast, labelled forms |

The tone is natural, concise, and confident — an editorial travel brand rather than a sales brochure.

---

## Site structure

```
NorthLight Iceland
├── Home (index.html)
├── Destinations (destinations.html)
│   └── Reykjavík, Golden Circle, South Coast, Akureyri, Westfjords
├── Experiences (experiences.html)
│   └── Northern Lights, glacier hiking, hot springs, whale watching, ice caves
├── Travel Guide (travel-guide.html)
│   └── Timing, transport, budget, safety, packing
├── Gallery (gallery.html)
├── Contact (contact.html)
│   └── Feedback form and image attributions
└── Thank you (thank-you.html)
```

Every content page shares a persistent header with primary navigation, breadcrumbs on inner pages, a skip link to main content, and a footer with secondary navigation. A reusable `template.html` shell supports consistent page structure during development.

---

## Functional specification

### Technical stack

| Requirement | Implementation |
|-------------|----------------|
| Markup | HTML5 semantic elements (`header`, `nav`, `main`, `section`, `article`, `footer`, `form`) |
| Styling | Layered CSS imported through `css/styles.css` (`tokens`, `base`, `layout`, `components`) |
| Scripting | None — CSS-only mobile navigation toggle |
| Frameworks | None |
| Typography | Google Fonts: Montserrat (display) and Poppins (body) |
| Hosting | GitHub Pages (static deployment) |

### Responsive breakpoints

| Viewport | Layout behaviour |
|----------|------------------|
| Mobile (&lt; 768px) | Single column, checkbox-toggle navigation, stacked cards |
| Tablet (768px – 959px) | Two-column grids, horizontal navigation |
| Desktop (960px+) | Three-column card grids, max-width container (75rem) |

### Contact form

| Field | Type | Validation |
|-------|------|------------|
| Name | Text | Required, 2–80 characters |
| Email | Email | Required |
| Destination interest | Select | Required |
| Preferred travel season | Select | Required |
| Message | Textarea | Required, 20–2000 characters |
| Consent | Checkbox | Required |

The form submits via GET to `thank-you.html` as a demonstration flow. Production deployment would use POST to a server endpoint or form service.

### Accessibility features

Skip navigation link, `lang="en"` on `<html>`, descriptive page titles and meta descriptions, meaningful alt text on images, visible `:focus-visible` indicators, form labels associated with inputs, `aria-current="page"` on active nav links, `prefers-reduced-motion` support, table captions with `scope` attributes, and colour contrast targeting WCAG 2.1 AA.

---

## Competitive comparison

Three established national tourism websites were reviewed to inform structure, tone, and differentiation.

| Criterion | Visit Iceland | Tourism Australia | Visit Dubai | NorthLight Iceland |
|-----------|---------------|-------------------|-------------|-------------------|
| Primary purpose | Official destination promotion | National tourism marketing and inspiration | City tourism and events promotion | Independent planning guides |
| Navigation depth | Deep multi-level menus | Broad category structure with regional hubs | Experience-led, visually rich sections | Flat six-page structure |
| Content tone | Inspirational, brand-led | Aspirational lifestyle marketing | Luxury and experience focused | Practical, editorial |
| Booking integration | Links to partners and operators | Strong booking and itinerary tools | Integrated booking and offers | None — planning only |
| Accessibility | Large site; variable page quality | Mature platform with mixed page-level results | Image-heavy, interactive elements | WCAG-conscious by design |
| Mobile experience | Responsive, media-rich | Responsive, campaign-driven | Responsive, animation-heavy | Mobile-first, lightweight |
| Unique strength | Official authority and breadth | Global brand recognition and content depth | Strong visual storytelling | Clarity, realistic planning advice |

NorthLight Iceland deliberately avoids booking engines, heavy JavaScript interactions, and generic promotional language. Instead it offers route-first guidance, honest seasonal expectations, structured comparison tables, and fast-loading static pages optimised for accessibility.

---

## Deployment

The website deploys to GitHub Pages from the repository root on push to `main`.

**Live URL:** https://harshyadav1711.github.io/northlight-iceland/

Full references in AU Harvard format: see `docs/references.md`.
