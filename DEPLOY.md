# Deploying will-oyston.dev

This is a static site: no build step. Publish the folder as-is.

## Option A: Cloudflare Pages (free, recommended)
1. Put this folder in a GitHub repo.
2. Cloudflare dashboard > Workers & Pages > Create > Pages > connect the repo.
3. Build command: none. Output directory: `/` (the repo root).
4. Custom domains > add `will-oyston.dev` and `www.will-oyston.dev`.
   If the domain's DNS is on Cloudflare this is automatic. Otherwise add the CNAME it shows you.
5. `_headers` and `_redirects` are read automatically. HTTPS is on by default.

## Option B: Netlify
Drag the folder into app.netlify.com/drop, then Domain management > add `will-oyston.dev`.
Netlify reads `_headers` and `_redirects` too.

## Your URLs
- will-oyston.dev            -> index.html
- will-oyston.dev/learn/     -> learn/index.html
- will-oyston.dev/learn/python/ (and html-css, javascript, hosting)
- will-oyston.dev/cdn/courses/download/python-course.zip

## Adding files
Drop a ZIP into `cdn/courses/download/` and link to `/cdn/courses/download/yourfile.zip`.
The four ZIPs here are placeholders: overwrite them with your real course files, keeping the same names.

## Own server (nginx) instead
Point the document root at this folder and use:
    location /cdn/courses/download/ { add_header Content-Disposition attachment; }
    error_page 404 /404.html;
