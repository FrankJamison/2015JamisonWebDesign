# Jamison Web Design v2015

Static, multi-page “brochure” website (2015 vintage) showcasing services, projects, and testimonials. This repo is intentionally build-free: plain HTML/CSS/JavaScript that can be hosted as static files.

## Live Preview

- Production/live preview: https://jamisonwebdesign2015.fcjamison.com/

## Quick Start (Local)

There are two common ways to preview this project locally:

### Option 1: Local static server (portable/recommended)

This is the most reliable approach if you just want the site running.

- Python (Windows):
  - `py -m http.server 8080`
  - Open `http://localhost:8080/` (most servers will auto-load `index.htm`; otherwise open `http://localhost:8080/index.htm`).
- Node:
  - `npx serve .`
  - Open the URL printed in the terminal.

Why serve instead of double-clicking files?

- Some browser behaviors differ on `file://` URLs (especially around relative paths and legacy scripts). Serving via HTTP matches real hosting more closely.

### Option 2: Local vhost-style URL (repo’s VS Code task)

This workspace includes a VS Code task that opens:

- `http://jamisonwebdesignv2015.localhost/`

This is meant for a “vhost” style local setup (Apache/Nginx/IIS/etc.) where that hostname is mapped to this folder.

Important:

- The task only opens the browser. It does not start a web server.
- Modern Chromium-based browsers often resolve `*.localhost` to `127.0.0.1` automatically, but the hostname still needs to be served by a local web server to show this site.
- If `http://jamisonwebdesignv2015.localhost/` does not resolve on your machine, you can either:
  - Switch to Option 1 (static server + `http://localhost:PORT/`), or
  - Add a hosts entry and configure a local web server/vhost.

Hosts file location (Windows):

- `C:\Windows\System32\drivers\etc\hosts` (requires admin rights)
- Example entry: `127.0.0.1 jamisonwebdesignv2015.localhost`

## VS Code

### Included Task(s)

- **Open in Browser**
  - File: `.vscode/tasks.json`
  - Opens: `http://jamisonwebdesignv2015.localhost/`

To run it:

- VS Code → Terminal → Run Task… → **Open in Browser**

If you prefer the portable “static server” workflow, update the task URL to match your chosen port (example: `http://localhost:8080/`).

Notes:

- The task currently targets Windows (`start chrome ...`). On macOS/Linux you’ll need to adjust the task command (for example `open` on macOS).

## Project Structure

Top-level pages:

- `index.htm` — Home (hero slideshow)
- `services.html` — Services
- `projects.html` — Portfolio/projects
- `testimonials.html` — Testimonials
- `contact.html` — Contact form + direct contact info
- `thankyou.html` — Form success page
- `error.html` — Form error page

Assets:

- `css/style.css` — Primary stylesheet
- `js/image_slide.js` — Site-specific slideshow/caption behavior (jQuery)
- `js/jquery.js` — Vendored jQuery 1.4.2
- `js/modernizr-1.5.min.js` — Vendored Modernizr 1.5
- `images/` — Images referenced by the layout and slideshow
- `fonts/` — Font assets + licensing note

SEO/verification:

- `sitemap.xml` — Sitemap (contains absolute URLs)
- `BingSiteAuth.xml` — Bing site verification file

## Developer Maintenance Guide

### Shared layout is duplicated per page

This site is classic static HTML: header, navigation, and footer markup are repeated across pages.

- If you change navigation labels/links, you must apply the same change to each page.
- Quick way to keep things consistent is to search for the navigation `<ul id="nav">` block and update it everywhere.

Tip: the current site already contains small differences across pages (for example, the Services link text).

### Home page slideshow

Where to edit:

- Markup: `index.htm` contains the slideshow `<ul class="slideshow">` and its `<li><img ...></li>` items.
- Behavior: `js/image_slide.js`

How it works:

- `js/image_slide.js` fades between `<li>` elements every 4 seconds.
- Captions are sourced from each slide image’s `alt` attribute and rendered into a caption element that the script appends at runtime.

If you add slides:

- Add another `<li>` containing an `<img>`.
- Ensure the `alt` text is what you want displayed as the caption.

### Metadata and SEO (legacy defaults)

Several pages include legacy-era metadata and hard-coded canonical-ish URLs.

- Many pages contain two `meta name="description"` tags.
- Pages include `og:url` pointing at `http://jamisonwebdesign.com/`.
- `sitemap.xml` uses absolute URLs under `http://www.jamisonwebdesign.com/`.

For a modern deployment, you’ll usually want to normalize these to your actual domain.

### Character encoding

Some pages declare both `windows-1252` and UTF-8 `Content-Type` meta tags. Most browsers will cope, but if you see “odd characters” issues:

- Standardize on UTF-8 and ensure the file is saved as UTF-8.

## Tech Notes

### No build step

- There is no bundler, package.json, transpilation, or compilation.
- Any static hosting (S3/CloudFront, GitHub Pages, Netlify, IIS, Apache, etc.) can serve this as-is.

### Browser/era context

- Markup is “classic/legacy era” (XHTML doctype in `index.htm`, older jQuery/Modernizr). Treat this as a snapshot-style site.

## URL & Metadata Notes (Localhost vs Live)

This repo contains hard-coded absolute URLs from the original site domain (`jamisonwebdesign.com`). If you deploy to a different domain (including the live preview domain), these are the primary places to review:

- Open Graph URL metadata:
  - Many pages include: `<meta property="og:url" content="http://jamisonwebdesign.com/" />`
- Sitemap:
  - `sitemap.xml` uses `http://www.jamisonwebdesign.com/...`
- Contact form redirects:
  - `contact.html` includes hidden `thankyou_url` / `error_url` pointing at `http://jamisonwebdesign.com/...`

If your goal is historical fidelity, leave these as-is.
If your goal is a “clean” deployment, update them to your target domain (for example: `https://jamisonwebdesign2015.fcjamison.com/`).

## Contact Form Notes

The contact form posts to an external hosted endpoint:

- `http://www.powweb.com/scripts/formemail.bml`

That endpoint controls actual email delivery and uses the `thankyou_url` / `error_url` values to redirect.

For modern deployments you will typically replace this with:

- A serverless form provider, or
- A small backend/API endpoint, or
- A static-host form feature (depending on your host)

## Deployment

Deploy by uploading the repository contents as static files.

Common gotchas:

- Default document: this project uses `index.htm` (not `index.html`). If your host expects `index.html`, configure the host or add a redirect.
- Case sensitivity: Windows is case-insensitive, but many hosts are case-sensitive (Linux). Ensure file names referenced in HTML/CSS match the actual casing in `images/`, `css/`, etc.

## Credits / Third-Party

- Template attribution is linked in the site footer (Jamison Web Design + Free HTML5 Templates).
- Vendored libraries: jQuery 1.4.2 and Modernizr 1.5.
- Font licensing information is included under `fonts/`.
