# COM4014 — NorthLight Iceland

Anonymous submission for **COM4014 Introduction to Web Authoring**.

## Project structure

```
COM4014/
├── NorthLight-Iceland/          ← Website files (submit as ZIP)
│   ├── index.html
│   ├── destinations.html
│   ├── aurora.html
│   ├── plan-your-trip.html
│   ├── experiences.html
│   ├── contact.html
│   ├── thank-you.html
│   └── css/styles.css
├── NorthLight-Iceland-website.zip
└── docs/
    ├── website-specification.md
    ├── evaluation-report.md
    ├── references.md
    └── evidence/                ← Add validation screenshots here
```

## Live site

Deploy via GitHub Pages (see below). Live URL format:

`https://<username>.github.io/<repository-name>/`

## Local preview

Open `COM4014/NorthLight-Iceland/index.html` in a browser, or run a local server:

```powershell
cd COM4014/NorthLight-Iceland
python -m http.server 8080
```

Then visit http://localhost:8080

## GitHub Pages deployment

1. Create a GitHub repository (e.g. `northlight-iceland`)
2. Push this project to the `main` branch
3. Go to **Settings → Pages → Build and deployment**
4. Set source to **GitHub Actions**
5. Push triggers `.github/workflows/pages.yml` automatically
6. Copy the deployed URL into `docs/website-specification.md` and `docs/evaluation-report.md`

## Pre-submission checklist

- [ ] Live URL added to specification and evaluation reports
- [ ] W3C HTML validation screenshots saved to `docs/evidence/`
- [ ] W3C CSS validation screenshot saved to `docs/evidence/`
- [ ] WAVE reports saved to `docs/evidence/`
- [ ] Submit `NorthLight-Iceland-website.zip`
- [ ] Confirm no student name appears anywhere

## Validation tools (free)

- HTML: https://validator.w3.org/nu/
- CSS: https://jigsaw.w3.org/css-validator/
- Accessibility: https://wave.webaim.org/
