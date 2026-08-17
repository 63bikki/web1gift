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

## Layout

The video is a full-bleed background at every screen size, with all type overlaid
on top of it. Legibility comes from three light layers rather than one heavy one,
so the picture stays visible: a 20% veil over the whole frame, a gradient plate
attached to each text block (`.masthead` and `.lede`), and a shadow on the glyphs.

The plates fade in over a **fixed length** (`--fade`), not a percentage of the
viewport. That matters: a percentage-based gradient drifts out from under the copy
on short screens, which is how text ends up unreadable on a laptop but fine on a
desktop.

One trade-off worth knowing. The clip is 1440x608 — 2.37:1, nearly cinemascope. On
a tall phone, `object-fit: cover` therefore shows only part of the frame's width:

| Viewport | Frame visible |
|---|---|
| 390x844 phone | 20% |
| 768x1024 tablet | 32% |
| 1440x900 desktop | 68% |
| 844x390 phone landscape | 91% |
| 2560x1080 ultrawide | 100% |

It reads fine because the footage is a wide, even mountain scene with no single
subject to lose. If you shoot new footage for this page, export a portrait crop too
and swap it in below a 6:5 aspect ratio.

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
