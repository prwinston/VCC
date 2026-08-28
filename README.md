# Victory Community Centre — Website

Static website for **Victory Community Centre A/G** (Assemblies of God), Taman Desa, Kuala Lumpur.
_Developing Leaders, Inspiring Community._

Multi-page static site — no build step, no dependencies. Fonts load from Google Fonts CDN.

```
site/
  index.html              ← homepage (services, sermon audio, directions & parking, giving)
  leadership.html         ← leadership bios
  memory-gallery.html     ← photo scrapbook + church history (2002–now)
  why-you-need-jesus.html ← outreach article
  robots.txt              ← search-engine crawl rules
  sitemap.xml             ← page index for search engines
  _headers                ← Cloudflare Pages caching/security headers
  assets/                 ← images, e-wallet QR, sermon audio
  assets/gallery/         ← memory-gallery collage images
README.md
```

## Preview locally
Open `site/index.html` in a browser, or serve it:
```bash
cd site
python3 -m http.server 8000    # then visit http://localhost:8000
```

## Option A — Deploy via GitHub (recommended, auto-redeploys)
```bash
git init
git add .
git commit -m "Victory Community Centre website"
git branch -M main
git remote add origin https://github.com/<your-username>/vcc-website.git
git push -u origin main
```
Then in Cloudflare:
1. **Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git**.
2. Pick your `vcc-website` repository.
3. Build settings:
   - **Framework preset:** `None`
   - **Build command:** _(leave blank)_
   - **Build output directory:** `site`
4. **Save and Deploy.** You get a `*.pages.dev` URL.

Every push to `main` redeploys automatically.

## Option B — Direct upload (no GitHub)
1. **Cloudflare dashboard → Workers & Pages → Create → Pages → Upload assets**.
2. Drag in the **contents of the `site/` folder** (the files inside it — not the folder itself).
3. **Deploy.**

The whole site is well under Cloudflare's 100-file drag-and-drop limit.

## Custom domain
**Custom domains → Set up a domain** and follow the DNS steps to use `victorycommunitycentre.org`.

## Notes
- Contact uses WhatsApp deep-links (no form/backend needed).
- Giving: e-wallet QR + Public Bank 3196 736 325 (Victory Community Centre A/G).
- Sermon audio ("God Pursues Us with the Weight of His Mercy") is served from `assets/`. As the archive grows, consider moving audio to Cloudflare R2 / a podcast host and linking out, to keep the site light.
