# moustaphakallias.com

Portfolio site for Moustapha Kallias. Single static page, no build step.

```
public/
  index.html          the whole site (HTML, CSS, JS inline)
  favicon.svg
  assets/img/         hero painting (WebP, 1280 and 2400 wide) and og.jpg share image
wrangler.jsonc        Cloudflare Workers static-assets config
```

## Features

- EN / ES / FR language switcher (English is the HTML source; Spanish and French live in the `I18N` object in `index.html`). Choice is remembered per browser.
- Hero intro: the painting fades in, the name rises letter by letter and the surname brushes in gold. Embers and mist drift over the hero (canvas) and scatter around the cursor; a torchlight glow and slight depth shift follow the cursor.
- Contact section: a compass whose needle follows the cursor (it sways on its own when idle or on touch), with embers and sea mist behind it.
- Cards tilt toward the cursor, buttons pull toward it, stat tiles flip to show context, the experience timeline fills in gold as you scroll, and clicking a language in the Profile section switches the site to it.
- Scrollspy nav, scroll progress bar, count-up stats, rotating analytics card, copy-email button with toast, back-to-top.
- "Download résumé (PDF)" opens the print dialog; the print stylesheet renders a clean one-page résumé, so choose "Save as PDF".
- Respects `prefers-reduced-motion`.

## Editing

All text is in `public/index.html`. When you change an English line that has a `data-i18n="key"` attribute, update the same key in the `es` and `fr` blocks of the `I18N` object near the bottom of the file.

## Deploying

The live domain is served by the Cloudflare Worker `divine-river-f6c1`.

**Auto-deploy from GitHub (recommended):** Cloudflare dashboard > Workers & Pages > divine-river-f6c1 > Settings > Build > Connect to Git > pick this repo, branch `main`. Leave the build command empty and the deploy command as `npx wrangler deploy`. Every push to `main` then goes live on moustaphakallias.com.

**Manual:** upload the contents of `public/` through Workers & Pages > divine-river-f6c1 > Create deployment.

**Local preview:** `cd public && python -m http.server 8000`, then open http://localhost:8000.
