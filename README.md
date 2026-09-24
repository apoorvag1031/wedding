# Apoorv & Arushi, 25 and 26 November 2026, Jaipur

Wedding invitation site. Two design versions, live side by side so they can be
compared on a real phone.

| File | URL | Treatment |
|---|---|---|
| `index.html` | `/` | Horizontal swipeable function posters |
| `v2.html` | `/v2.html` | Loading screen, larger sentence-case names, vertical posters that scale on scroll |

## How it works

Each file is completely self-contained: all artwork is inline SVG and CSS, so
there are no images to upload and nothing to build. The only external request is
to Google Fonts. Editing is a matter of opening the file in any text editor.

Roughly 47 KB compressed per page, which is what a guest actually downloads.

## Publishing

GitHub Pages serves this repository directly. Settings, then Pages, then deploy
from the `main` branch, root folder. Changes go live about a minute after a
commit.

`.nojekyll` tells GitHub to serve the files as-is rather than running them
through Jekyll.

## Picking one version

Once a version is chosen, rename it to `index.html` and delete the other. The
URL to share stays the same.

## Still to fill in

- Pheras time
- Venue spelling, Aamantran or Aamanatran
- Parents' names
- Dress code per function
- Google Maps link
- Contact phone numbers
- Devanagari proofread
- `og-card.png`, the WhatsApp link preview image, is currently a stopgap
  screenshot that includes the site header
