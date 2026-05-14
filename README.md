# liars-dice-site

Static support and privacy site for the [Liar's Dice](https://apps.apple.com/) iOS app.

## Live URLs

- **Home:** https://codyni123.github.io/liars-dice-site/
- **Support:** https://codyni123.github.io/liars-dice-site/support/
- **Privacy:** https://codyni123.github.io/liars-dice-site/privacy/

These are the URLs listed in App Store Connect for the app's Support and Privacy fields.

## Editing

Plain HTML and CSS, no build step. Edit the files, commit, push — GitHub Pages picks up changes within ~30 seconds.

```
.
├── index.html        # Landing page
├── support/          # Support page (App Store "Support URL")
├── privacy/          # Privacy policy (App Store "Privacy Policy URL")
├── style.css         # Shared styles (Dawn palette, system stack)
├── favicon.svg       # Favicon
├── icon.svg          # Larger app icon used on landing
└── .nojekyll         # Skip Jekyll processing
```

## App repo

Source code for the app itself lives in [codyni123/liars-dice](https://github.com/codyni123/liars-dice) (private).
