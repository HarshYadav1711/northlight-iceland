# NorthLight Iceland

NorthLight Iceland is a destination-focused travel website designed to help visitors explore Iceland's most remarkable landscapes, experiences, and travel opportunities through a simple, intuitive, and accessible web experience.

The platform brings together practical travel information, destination highlights, activity recommendations, planning resources, and visitor feedback in a clean and responsive interface. The goal is to make trip planning straightforward while showcasing the unique character of Iceland's natural environment.

## Overview

Travel websites often overwhelm visitors with excessive information, cluttered navigation, and inconsistent user experiences. NorthLight Iceland was created with a different approach: present useful information clearly, prioritize usability, and make discovering destinations enjoyable.

The website provides:

* Destination guides covering major regions of Iceland
* Information about popular activities and experiences
* Practical travel planning resources
* Image galleries showcasing key attractions
* A visitor feedback and enquiry form
* Responsive layouts for desktop, tablet, and mobile devices

## Features

### Destination Discovery

Explore some of Iceland's most popular locations, including:

* Reykjavík
* The Golden Circle
* South Coast
* Akureyri
* Westfjords

Each destination includes concise information, key highlights, and travel inspiration.

### Experiences

Discover activities that make Iceland one of the world's most unique travel destinations:

* Northern Lights viewing
* Glacier hiking
* Whale watching
* Geothermal hot springs
* Ice cave exploration

### Travel Planning Resources

Visitors can access practical information to help prepare for their journey, including:

* Best times to visit
* Transportation guidance
* Budget considerations
* Safety recommendations
* Packing suggestions

### Gallery

A curated visual collection designed to showcase Iceland's landscapes, culture, and natural attractions.

### Feedback Form

A dedicated contact page allows visitors to submit feedback and travel enquiries through a structured form with fields for name, email, destination interest, preferred travel season, and message. Submissions redirect to a confirmation page (demonstration flow; no server processing).

## Design Principles

NorthLight Iceland was developed around four core principles:

### Clarity

Content is organised into logical sections with straightforward navigation and consistent layouts.

### Accessibility

The website follows accessibility best practices by using:

* Semantic HTML structure
* Meaningful heading hierarchy
* Alternative text for images
* Accessible form labels
* Keyboard-friendly navigation
* Sufficient colour contrast

### Responsiveness

Layouts adapt across different screen sizes to provide a consistent experience on:

* Desktop computers
* Tablets
* Mobile devices

### Performance

The site uses no JavaScript and no CSS frameworks—only HTML, modular CSS, and Google Fonts (Montserrat and Poppins) for typography.

## Technology Stack

### Frontend

* HTML5
* CSS3

### Layout Techniques

* CSS Flexbox
* CSS Grid
* CSS custom properties (design tokens)
* Responsive media queries

Styles are split into layered files (`tokens`, `base`, `layout`, `components`) imported through a single entry point (`css/styles.css`).

No frontend frameworks or UI libraries were used. The interface was built from the ground up to maintain full control over structure, styling, and performance.

## Project Structure

```text
northlight-iceland/
│
├── index.html              # Homepage
├── destinations.html
├── experiences.html
├── travel-guide.html
├── gallery.html
├── contact.html
├── thank-you.html          # Form confirmation
├── template.html           # Reusable page shell
│
├── css/
│   ├── styles.css          # Main stylesheet (imports layers below)
│   ├── tokens.css
│   ├── base.css
│   ├── layout.css
│   └── components.css
│
├── images/                 # Local assets (optional; gallery uses Unsplash CDN)
│
├── .github/workflows/      # GitHub Pages deployment
├── SUBMISSION-REVIEW.md    # Validation and accessibility review notes
└── README.md
```

Course specification and evaluation documents are in `COM4014/docs/`.

## Live Site

Deployed via GitHub Pages on push to `main`:

**https://harshyadav1711.github.io/northlight-iceland/**

## Local Preview

Open `index.html` in a browser, or run a local server from the repository root:

```powershell
python -m http.server 8080
```

Then visit http://localhost:8080

## User Experience Goals

The website was designed to help visitors:

* Quickly understand what Iceland offers
* Navigate between sections without confusion
* Access information efficiently on any device
* Submit travel enquiries easily
* Enjoy a visually engaging browsing experience

## Future Enhancements

Potential future improvements include:

* Interactive destination maps
* Weather integration
* Itinerary planning tools
* Multi-language support
* Search functionality
* Booking integrations

## Credits

Photographs are sourced from [Unsplash](https://unsplash.com/) under the [Unsplash License](https://unsplash.com/license). Full photographer attributions are listed on the [Contact page](https://harshyadav1711.github.io/northlight-iceland/contact.html#attributions).

Travel information on this site is for informational and educational purposes. NorthLight Iceland does not sell tours or travel packages.

## Author

Developed and maintained by Harsh Yadav.

For collaboration opportunities, feedback, or project discussions, feel free to get in touch.
