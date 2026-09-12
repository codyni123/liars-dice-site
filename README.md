# liars-dice-site

Marketing, support, rules and privacy site for the [Liar's Dice](https://apps.apple.com/app/id6767948698) iOS app. Plain HTML and CSS, no build step, hosted on GitHub Pages.

## Live URLs

- **Home:** https://codyni123.github.io/liars-dice-site/
- **How to play:** https://codyni123.github.io/liars-dice-site/how-to-play/
- **Support:** https://codyni123.github.io/liars-dice-site/support/ (App Store Connect "Support URL")
- **Privacy:** https://codyni123.github.io/liars-dice-site/privacy/ (App Store Connect "Privacy Policy URL")

## Editing

Edit the files, commit, push `main` — GitHub Pages redeploys within about a minute.

Every page carries the GA4 tag for the "Liar's Dice site" property (`G-HQY2RR5TW8`, same Google account as Search Console); copy the snippet from any page's `<head>` into new pages. The property is linked to the Search Console property.

```
.
├── index.html            # Landing page
├── how-to-play/          # The rules (mirrors the in-app How to play screen)
├── support/              # Support + FAQ (App Store "Support URL")
├── privacy/              # Privacy policy (App Store "Privacy Policy URL")
├── 404.html              # GitHub Pages custom 404 (uses absolute /liars-dice-site/ paths)
├── style.css             # Shared styles — the app's Dawn palette, system type stack, CSS-drawn dice
├── favicon.svg           # Favicon (the app icon)
├── img/
│   ├── appstore-badge.svg  # Apple's official badge artwork — do not restyle or redraw
│   ├── og.jpg              # 1200×630 social card
│   ├── touch-icon.png      # 180×180 apple-touch-icon
│   ├── app-icon-512.png    # App icon, used to regenerate og.jpg
│   └── shots/*.jpg         # Raw simulator captures, 750px wide, framed by the site's own CSS bezel
├── robots.txt, sitemap.xml
└── .nojekyll             # Skip Jekyll processing
```

## Conventions

- **Paths are relative** (`img/…`, `../style.css`) so the site works at the GitHub Pages sub-path and when served locally from any directory. The only exception is `404.html`, which GitHub serves for any missing URL and therefore uses absolute `/liars-dice-site/` paths.
- **The email address is never visible text.** Contact buttons are `mailto:` links only.
- **Light mode only, on purpose.** The app launches in the Dawn light palette regardless of system appearance, and the site matches it.
- **Dice are drawn in CSS** (`.die[data-v="1…6"]` with one `<i>` per pip); a 1 renders its pip in the accent because ones are wild. Never use the dice emoji.
- **Screenshots** come from `marketing/screenshots/public/screenshots/apple/iphone/en/` in the app repo (1206×2622 captures with the 9:41 status bar), downscaled with Pillow to 750px JPEG.
- **Motion** is limited to reveal-on-scroll, a slow drift on the hero pieces, and the cup lift in the reveal tile; all of it is disabled under `prefers-reduced-motion`.

## SEO and AI discoverability

What's in place:

- Keyword-bearing `<title>`, meta description, and a real `<h1>` ("Liar's Dice — a bluffing dice game for iPhone & iPad") on the landing page; the big statement below it is a styled paragraph.
- JSON-LD on every page: `Organization` + `WebSite` + `VideoGame`/`MobileApplication` + `FAQPage` on the home page, `Article` on the rules page, `BreadcrumbList` on the inner pages. The FAQ markup mirrors the visible FAQ word for word.
- `canonical`, Open Graph and Twitter cards, `og.jpg`, `sitemap.xml` with `lastmod`, `robots.txt`, and `llms.txt` (a plain-Markdown summary for AI crawlers and answer engines).
- Plain, crawlable HTML — nothing is rendered by JavaScript, so Googlebot, Bingbot, GPTBot, ClaudeBot and friends see the whole page.

Google Search Console ownership is proven two ways — the `google4733d915db45d4de.html` file at the site root and the `google-site-verification` meta tag in every page's `<head>`. **Never delete either**, or the property loses verification.

Two things only the account owner can do:

1. **Google Search Console.** Add a URL-prefix property for `https://codyni123.github.io/liars-dice-site/`, verify with the HTML-tag method (paste the `google-site-verification` meta tag into the `<head>` of every page, or drop Google's HTML file in the repo root), then submit `sitemap.xml` and request indexing for the four URLs under URL Inspection. Google feeds Gemini.
2. **Bing Webmaster Tools.** Import the site from Search Console (one click) or verify the same way, and submit the sitemap. Bing feeds ChatGPT search and Copilot; Claude's web search and Perplexity crawl the open web directly and follow sitemaps too.

IndexNow (Bing, Yandex and the engines behind ChatGPT search) is wired up: the key file `6aca7462c36e0ec0375117e6aea916be.txt` lives at the site root, so after any content change you can notify them with:

```bash
curl -s -X POST https://api.indexnow.org/indexnow -H "Content-Type: application/json; charset=utf-8" -d '{"host":"codyni123.github.io","key":"6aca7462c36e0ec0375117e6aea916be","keyLocation":"https://codyni123.github.io/liars-dice-site/6aca7462c36e0ec0375117e6aea916be.txt","urlList":["https://codyni123.github.io/liars-dice-site/","https://codyni123.github.io/liars-dice-site/how-to-play/","https://codyni123.github.io/liars-dice-site/support/","https://codyni123.github.io/liars-dice-site/privacy/"]}'
```

One caveat: crawlers read `robots.txt` and `llms.txt` only at the origin root (`https://codyni123.github.io/`), which is served by the separate `codyni123.github.io` repo. That root currently has no `robots.txt`, which means allow-all, so nothing blocks indexing. To point crawlers at this sitemap from the root, add a `robots.txt` to that repo with `Sitemap: https://codyni123.github.io/liars-dice-site/sitemap.xml`.

## Preview locally

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765/.

## App repo

Source code for the app itself lives in [codyni123/liars-dice](https://github.com/codyni123/liars-dice) (private).
