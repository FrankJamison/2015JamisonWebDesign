# 2015 Jamison Web Design (Static Site)

A small, static, multi-page website built with classic HTML/CSS/JavaScript.

This workspace contains the site’s pages, styling, images, fonts, and a small amount of JavaScript for progressive enhancement and UI behavior.

## Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Site Pages](#site-pages)
- [Folder / File Structure](#folder--file-structure)
- [Run / View Locally](#run--view-locally)
- [Editing Guidelines](#editing-guidelines)
- [Forms / Contact Flow](#forms--contact-flow)
- [SEO / Crawling](#seo--crawling)
- [Browser Support Notes](#browser-support-notes)
- [Deployment](#deployment)
- [License / Credits](#license--credits)

## Project Overview

This is a traditional “brochure” style site intended to be hosted as static files:

- Multiple standalone HTML pages
- Shared stylesheet in `css/style.css`
- Images in `images/`
- JavaScript in `js/` (including a bundled jQuery copy and Modernizr)

There is no build step and no server-side runtime required to render the pages.

## Tech Stack

- **HTML**: Static pages (no templating/build pipeline)
- **CSS**: Single primary stylesheet
- **JavaScript**:
  - `js/jquery.js` (jQuery library)
  - `js/modernizr-1.5.min.js` (feature detection for older browsers)
  - `js/image_slide.js` (site-specific behavior; likely slideshow/rotation)

## Site Pages

Top-level pages in the project root:

- `index.htm` — Home page
- `services.html` — Services overview
- `projects.html` — Projects/portfolio
- `testimonials.html` — Testimonials
- `contact.html` — Contact page
- `thankyou.html` — Post-submission/confirmation page
- `error.html` — Error/fallback page

Additional non-page files:

- `sitemap.xml` — Sitemap for search engines
- `BingSiteAuth.xml` — Search engine verification file

## Folder / File Structure

- `css/`
  - `style.css` — Main site styles
- `fonts/`
  - Font license text file(s)
- `images/`
  - Site images (logos, backgrounds, portfolio images, etc.)
- `js/`
  - `image_slide.js` — Site-specific JS
  - `jquery.js` — jQuery
  - `modernizr-1.5.min.js` — Modernizr

## Run / View Locally

Because this is a static site, you can view it in a couple of simple ways:

### Option A: Open the file directly

1. In File Explorer, open `index.htm`.
2. Double-click to open it in your default browser.

Notes:

- Some browsers apply stricter rules to scripts/assets when opening files directly.
- If anything appears broken (images not loading, scripts blocked, etc.), use Option B.

### Option B: Serve the folder with a simple static server

Serving files over HTTP is closer to how the site behaves in production.

Common approaches:

- VS Code “Live Server” extension
- Any static server command (for example, from Python, Node, etc.)

Once served, open the site’s root page (`index.htm`) in your browser via the server’s URL.

## Editing Guidelines

- **Global styling**: update `css/style.css`.
- **Navigation / shared layout**: because pages are static, shared elements are duplicated across each HTML file. When changing navigation, update it consistently across:
  - `index.htm`
  - `services.html`
  - `projects.html`
  - `testimonials.html`
  - `contact.html`
  - and any other page with the same header/footer.
- **Images**: place new assets in `images/` and reference them with relative paths.
- **JavaScript behavior**:
  - Site-specific logic likely lives in `js/image_slide.js`.
  - Avoid editing `js/jquery.js` and `js/modernizr-1.5.min.js` unless you intentionally want to upgrade/replace those libraries.

## Forms / Contact Flow

The site includes `contact.html` and a `thankyou.html` page.

Important note: static hosting does not process forms by itself. If the contact form is expected to send email or store submissions, you will need one of:

- A hosted form provider (embed or post-to endpoint)
- A small server-side handler (PHP/Node/etc.)
- A serverless function (platform-specific)

If the form currently posts to a server endpoint, ensure that endpoint exists in the target hosting environment and that the success/error redirects match `thankyou.html` / `error.html`.

## SEO / Crawling

- `sitemap.xml` is present for indexing.
- `BingSiteAuth.xml` exists for site ownership verification.

When deploying:

- Ensure both XML files are available at the site root.
- If you change page names or add new pages, update `sitemap.xml` accordingly.

## Browser Support Notes

This project includes Modernizr and uses older-style front-end patterns consistent with its era.

- If you modernize any markup/CSS, verify layout in at least one evergreen browser.
- If legacy browser support matters, test carefully before removing Modernizr or changing key CSS rules.

## Deployment

This site can be deployed to any static hosting solution:

- Copy all files/folders as-is to your web root.
- Preserve the directory structure (`css/`, `js/`, `images/`, etc.).
- Ensure the default document is set to `index.htm` (some hosts default to `index.html`).
  - If your host requires `index.html`, either rename the file (and update links) or configure the host to use `index.htm`.

## License / Credits

- Font licensing information (if applicable) is included under `fonts/`.
- Third-party libraries:
  - jQuery (`js/jquery.js`)
  - Modernizr (`js/modernizr-1.5.min.js`)

If you redistribute or publish this site, review any third-party license requirements and ensure attribution/terms are satisfied.
