# GraphForge public homepage copy

This folder is the public-homepage build of GraphForge. It is generated from
`../GraphForge.html` by `../build-public.js`; the application HTML, CSS, and
JavaScript are copied unchanged.

Only public-facing presentation and hosting metadata differ from the regular
single-file build:

- English document title/description and Open Graph/Twitter metadata
- JSON-LD `SoftwareApplication` metadata and a web app manifest
- a `<noscript>` notice for visitors without JavaScript
- `robots.txt`, `.nojekyll`, and optional `_headers` security headers
- a copied social preview image

## Deploy

Upload the contents of this folder to any static host:

- GitHub Pages, Cloudflare Pages, Netlify, Vercel, or an ordinary web server
- entry point: `index.html`
- no build step, server-side code, database, or external CDN is required

After changing the application, rebuild both files from the project root:

```bash
node build.js
node build-public.js
```

Do not hand-edit `public/index.html`; it will be overwritten.

## Public-site notes

- Graph data, project files, preferences, and code stay in the visitor's
  browser. There are no analytics, tracking pixels, remote fonts, or uploads.
- Project imports are limited to 8 MB and validated before applying. Imported
  Python/batch code is never executed automatically; it only runs when the
  visitor explicitly starts it in the sandboxed iframe.
- The built app is offline-capable as a single local file, but hosting it over
  HTTPS is recommended for clipboard access and browser security features.
- If the app is served from a subdirectory, keep `index.html`, `preview.png`,
  `icon.svg`, and `manifest.webmanifest` together.
- The metadata intentionally has no canonical URL or `og:url`; add those only
  after the final public URL is known.
- The optional `_headers` file is for Netlify/Cloudflare Pages-style hosts.
  A stricter CSP can be added at the host once the deployment URL is fixed;
  test dynamically exported HTML and the Python sandbox before enforcing it.
