BRICK BUILDER: deploy folder
============================
Upload everything in this folder to the ROOT of your website. It is a static site:
no server, database or build step is needed.

What's inside
  index.html             the whole app (code + styles inline)
  favicon.svg/.ico/.png  browser tab icons
  apple-touch-icon.png   iPhone/iPad home-screen icon
  icons/                 PWA icons (192, 512, maskable)
  manifest.webmanifest   lets visitors "Install app" / "Add to Home Screen"
  sw.js                  offline support (only activates on https)
  og-image.png           preview image for WhatsApp / Facebook / X / Discord links
  robots.txt             search engine rules
  404.html               "page not found" page
  _headers               security + cache headers (Netlify / Cloudflare Pages only; harmless elsewhere)

Hosting
  - Netlify / Cloudflare Pages / Vercel / GitHub Pages: drag the folder or point to it. No build command, publish directory = this folder.
  - Shared hosting / cPanel: upload to public_html (the folder that holds your site root).
  - HTTPS is strongly recommended (needed for offline mode and "Install app").
  - If you put it in a sub-folder (example.com/bricks/) everything still works, because all paths are relative
    except 404.html (edit its "/" links).

Domain-specific SEO (optional, recommended)
  After you know your domain, rebuild once so link previews and Google use absolute URLs:
      SITE_URL=https://yourdomain.com node build.mjs
  This adds the canonical URL, absolute og:image and a sitemap.xml, then re-fill the site/ folder.

Updating later
  Change the code, run `node build.mjs`, re-upload site/. If visitors don't see the new version,
  bump VERSION in public/sw.js.

Notes
  - Projects are saved in each visitor's own browser (IndexedDB). They can move them with Export / Import.
  - Online share links and a public gallery need a backend; the current Share button exports a file / image.
  - Needs a browser with WebGL2 (all current Chrome, Edge, Firefox, Safari).
