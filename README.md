# liars-dice-site

Marketing, support, rules and privacy site for the [Liar's Dice](https://apps.apple.com/app/id6767948698) iOS app. Plain HTML and CSS, no build step, hosted on GitHub Pages.

## Live URLs

- **Home:** https://codyni123.github.io/liars-dice-site/
- **How to play:** https://codyni123.github.io/liars-dice-site/how-to-play/
- **Support:** https://codyni123.github.io/liars-dice-site/support/ (App Store Connect "Support URL")
- **Privacy:** https://codyni123.github.io/liars-dice-site/privacy/ (App Store Connect "Privacy Policy URL")

## Editing

Edit the files, commit, push `main` — GitHub Pages redeploys within about a minute.

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

## Preview locally

```bash
python3 -m http.server 8765
```

Then open http://localhost:8765/.

## App repo

Source code for the app itself lives in [codyni123/liars-dice](https://github.com/codyni123/liars-dice) (private).
