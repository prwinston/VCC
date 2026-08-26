# Victory Community Centre — Website

Static homepage for **Victory Community Centre** (Assemblies of God).
_Developing Leaders, Inspiring Community._

Single self-contained page — no build step, no dependencies. Fonts load from Google Fonts CDN.

```
site/
  index.html     ← the homepage (open in any browser)
  _headers        ← Cloudflare Pages caching/security headers
README.md
```

## Preview locally
Just open `site/index.html` in a browser. Or serve it:
```bash
cd site
python3 -m http.server 8000    # then visit http://localhost:8000
```

## Put it on GitHub
```bash
git init
git add .
git commit -m "Victory Community Centre homepage"
git branch -M main
git remote add origin https://github.com/<your-username>/vcc-website.git
git push -u origin main
```

## Deploy with Cloudflare Pages
1. Go to **Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git**.
2. Pick your `vcc-website` repository.
3. Build settings:
   - **Framework preset:** `None`
   - **Build command:** _(leave blank)_
   - **Build output directory:** `site`
4. **Save and Deploy.** Cloudflare gives you a `*.pages.dev` URL.
5. To use your own domain: **Custom domains → Set up a domain** and follow the DNS steps.

Every push to `main` redeploys automatically.

## Still to fill in before going live
- Replace the placeholder image blocks (marked in the layout) with real photos.
- Swap the bank account number `•••• 0000` and add the real e-wallet QR image on the Give section/page.
- Wire the nav links to real inner pages (Sermons, Testimonies, History gallery, Why You Need Jesus, Articles, Bible Study, Giving) — currently anchor links / `#`.
