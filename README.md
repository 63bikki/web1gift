# Giftrav — coming soon

Static site. No build step, no dependencies. Published with GitHub Pages from the
`main` branch, root folder.

**Live:** https://63bikki.github.io/web1gift/

## Files

```
index.html                  the page
ds/broadsheet/styles.css    Broadsheet design system — design tokens
fonts/                      Source Serif 4, self-hosted (two weights, 42 KB)
media/giftrav-hero.webm     hero video, VP9        247 KB
media/giftrav-hero.mp4      hero video, H.264      358 KB  (Safari < 14 fallback)
media/poster.jpg            first frame — holds the page before the video paints
media/og-image.jpg          1200x630 social share card
favicon.svg, favicon-32.png, apple-touch-icon.png
.nojekyll                   stops GitHub Pages running the files through Jekyll
```

## Two things to know before editing

**Don't put files starting with `_` in this repo.** GitHub Pages runs Jekyll by
default, and Jekyll silently excludes any file or folder whose name starts with an
underscore. The design system folder used to be called `_ds/`, which meant
`styles.css` returned a 404 on the live site while looking perfectly fine in the
repo. It's `ds/` now, and `.nojekyll` is here as a second line of defence.

**Don't publish the `.dc.html` file.** That format needs a JavaScript runtime plus
React loaded from a CDN. Renaming it to `index.html` produces a blank page. This
`index.html` is plain HTML and CSS and does not depend on either.

## Custom domain

If you point a domain here, add a `CNAME` file at the root containing just the
domain, then update these in `index.html` — they're absolute URLs and Facebook
and LinkedIn won't resolve them otherwise:

- `og:image`
- `og:url`
- `twitter:image`
- `<link rel="canonical">`

Then run the URL through Facebook's Sharing Debugger once to refresh their cache.
