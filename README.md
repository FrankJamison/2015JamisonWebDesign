# 2015 Jamison Web Design

Static, multi‑page “brochure” website showcasing web design services and portfolio work. This repo is intentionally build‑free (plain HTML/CSS/JavaScript), designed for easy hosting as static files.

## Highlights (Recruiter-Friendly)

### Design & UX

- **Consistent layout system** across pages (header + navigation + content + footer)
- **Hero image slideshow** with caption overlay and hover‑to‑pause interaction
- **Custom typography** via embedded `@font-face` (“News Cycle”)
- **Visual depth** using shadows, gradients, rounded corners, and a translucent content panel overlay
- **Clear information architecture**: Services, Projects, Testimonials, Contact, and post‑submit confirmation/error pages

### Development

- **No build step / no framework**: open the files directly or serve via any static server
- **Progressive enhancement**: Modernizr enables HTML5 element support and feature detection for older browsers
- **Separation of concerns**:
  - Presentation in `css/style.css`
  - Behavior in `js/image_slide.js` (site-specific) + vendor libraries in `js/`
- **SEO & sharing metadata**: Open Graph meta tags on pages + `sitemap.xml` for crawlers
- **Contact workflow**: HTML form posts to a hosted form handler and routes to `thankyou.html` / `error.html`

## Tech Stack

- **HTML**: static pages (primarily classic/legacy era markup)
- **CSS**: single main stylesheet at `css/style.css`
- **JavaScript**:
  - `js/image_slide.js` – slideshow/caption behavior (jQuery)
  - `js/jquery.js` – jQuery 1.4.2 (vendored)
  - `js/modernizr-1.5.min.js` – Modernizr (vendored)

## Pages

- `index.htm` — Home
- `services.html` — Services
- `projects.html` — Portfolio/projects
- `testimonials.html` — Testimonials
- `contact.html` — Contact form + direct contact info
- `thankyou.html` — Form success page
- `error.html` — Form error page

Supporting:

- `sitemap.xml` — sitemap for search engines

## Project Structure

```
.
├─ index.htm
├─ services.html
├─ projects.html
├─ testimonials.html
├─ contact.html
├─ thankyou.html
├─ error.html
├─ sitemap.xml
├─ css/
│  └─ style.css
├─ js/
│  ├─ image_slide.js
│  ├─ jquery.js
│  └─ modernizr-1.5.min.js
├─ images/
└─ fonts/
```

## Run Locally

### Option A: Open directly

Open `index.htm` in a browser.

### Option B: Serve via a static server (recommended)

From the project folder:

- Python (Windows): `py -m http.server 8080`
- Node: `npx serve .`

Then visit `http://localhost:8080/` (or the URL your server prints) and open `index.htm`.

### VS Code task

If you use the included task, it opens a configured local URL:

- `.vscode/tasks.json` → **Open in Browser** (points at `http://2015jamisonwebdesign.localhost/`)

## Contact Form Notes

The contact form in `contact.html` posts to a hosted endpoint (Powweb’s `formemail.bml`) and uses:

- `thankyou.html` on success
- `error.html` on failure

If you deploy this site somewhere else, you’ll likely want to replace the form handler (or update the redirect URLs) to match your hosting platform.

## SEO / Verification Notes

- `sitemap.xml` is included for search engine indexing.
- `BingSiteAuth.xml` is intentionally **ignored** by git in this repo; if you need Bing verification for a deployment, add the file at the site root locally.

## Credits / Third‑Party

- Template attribution is linked in the site footer (Jamison Web Design + Free HTML5 Templates).
- Vendored libraries: jQuery 1.4.2 and Modernizr 1.5.
- Font license information is included under `fonts/`.
