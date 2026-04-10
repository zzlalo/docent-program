# Conference Docent Program — Quarto Website

A multi-page Quarto website for recruiting experienced conference attendees to serve as docents (friendly guides) for first-time attendees.

## Project Structure

```
docent-quarto/
├── _quarto.yml          # Project config, navbar, footer, theme
├── custom.scss          # SCSS theme (colors, typography, components)
├── styles.css           # Additional CSS overrides
├── index.qmd            # Home page (hero, overview, CTA)
├── about.qmd            # About the program
├── how-it-works.qmd     # Step-by-step process
├── faq.qmd              # Frequently asked questions
├── signup.qmd           # Volunteer signup form
└── README.md            # This file
```

## Prerequisites

- **RStudio** (2023.06 or later recommended)
- **Quarto** (1.3+ — bundled with recent RStudio versions)
- A **Quarto Pub** account (free at <https://quartopub.com>)

## Setup Instructions

### 1. Create the Project in RStudio

1. Copy this entire `docent-quarto/` folder to your desired location
2. Open RStudio → **File → Open Project** → navigate to the folder
   - Or: **File → New Project → Existing Directory** → select the folder
3. RStudio will recognize it as a Quarto project from `_quarto.yml`

### 2. Preview Locally

In the RStudio **Terminal** tab (not Console), run:

```bash
quarto preview
```

This opens the site in your browser with live reload — any edits you save will refresh automatically.

Alternatively, click the **Render** button in RStudio when viewing any `.qmd` file.

### 3. Customize the Content

**Things you'll want to update:**

| File | What to Change |
|------|---------------|
| `_quarto.yml` | `site-url` → your Quarto Pub URL; footer email address |
| `index.qmd` | Conference name, any org-specific language |
| `about.qmd` | Organization details, program history |
| `how-it-works.qmd` | Specific logistics (orientation time, location) |
| `faq.qmd` | Add/remove questions relevant to your conference |
| `signup.qmd` | **Form action URL** (see Form Setup below) |
| `custom.scss` | Colors, fonts if you want to match your org branding |

### 4. Set Up the Signup Form

The signup form in `signup.qmd` uses a `<form>` tag that needs a backend to receive submissions. Here are three easy options:

#### Option A: Formspree (Recommended — Free Tier)
1. Go to [formspree.io](https://formspree.io) and create a free account
2. Create a new form and copy your form endpoint
3. In `signup.qmd`, replace `YOUR_FORM_ID` in the action URL:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

#### Option B: Google Forms
1. Create a Google Form with matching fields
2. Replace the `<form>` section in `signup.qmd` with an embedded Google Form:
   ```html
   <iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true"
           width="100%" height="800" frameborder="0">Loading…</iframe>
   ```

#### Option C: Microsoft Forms
Same approach as Google Forms — embed with an `<iframe>`.

## Publishing to Quarto Pub

### First-Time Publish

In the RStudio **Terminal**, run:

```bash
quarto publish quarto-pub
```

You'll be prompted to:
1. Authorize with your Quarto Pub account (opens browser)
2. Confirm the site name

Quarto will render and deploy the site. Your URL will be:
```
https://YOUR-USERNAME.quarto.pub/docent-program/
```

### Subsequent Updates

After making changes, just run the same command:

```bash
quarto publish quarto-pub
```

It will remember your settings and republish.

## Customizing the Design

### Colors
Edit the variables at the top of `custom.scss`:

```scss
$deep-teal: #1A5C57;     // Primary dark color (navbar, headings)
$bright-teal: #2A8C84;   // Links, accents
$gold: #D4A853;           // CTA buttons, highlights
$coral: #E07A5F;          // Accent color
$warm-cream: #FBF7F0;    // Page background
```

### Fonts
The site uses two Google Fonts:
- **Fraunces** (serif) — headings and display text
- **Source Sans 3** (sans-serif) — body text

To change them, update the `@import url(...)` line in `custom.scss` and the `$font-family-*` variables.

### Navbar
Edit the `website: navbar:` section in `_quarto.yml` to add/remove/reorder navigation links.

## Tips

- **Images**: Place any images in an `images/` folder and reference them in your `.qmd` files
- **Analytics**: Add Google Analytics by adding `google-analytics: "G-XXXXXXXXXX"` under `website:` in `_quarto.yml`
- **Custom domain**: Quarto Pub supports custom domains — see their docs for setup
- **Favicon**: Add `favicon: images/favicon.png` under `website:` in `_quarto.yml`


