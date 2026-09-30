# Apoorv & Arushi, 25 and 26 November 2026, Jaipur

Wedding invitation site. Two design versions, live side by side so they can be
compared on a real phone.

| File | URL | Treatment |
|---|---|---|
| `index.html` | `/` | Horizontal swipeable function posters |
| `v2.html` | `/v2.html` | Loading screen, larger sentence-case names, vertical posters that scale on scroll |

## How it works

There is nothing to build. `index.html` holds the layout, text and animation;
its illustrations (palace, elephant, flowers, horses, chandeliers, the Sangeet
scene, the Reception couple and the venue courtyard) are WebP files in `assets/`, so that
folder must be uploaded alongside it. `v2.html` is still all inline SVG and CSS.
The only external request is to Google Fonts. Editing is a matter of opening the
file in any text editor.

A guest downloads roughly 56 KB of compressed page plus 1.6 MB of artwork
(20 WebP files).

## Publishing

GitHub Pages serves this repository directly. Settings, then Pages, then deploy
from the `main` branch, root folder. Changes go live about a minute after a
commit.

`.nojekyll` tells GitHub to serve the files as-is rather than running them
through Jekyll.

## Connecting the RSVP form

GitHub Pages cannot store form answers, so the RSVP form on the page posts them
to a Google Form, which saves each reply as a row in a Google Sheet. It is free
and needs no server.

1. Create a Google Form with three questions:
   - **Full name**: short answer
   - **Joining us for**: checkboxes, with exactly these options: `Maayra`,
     `Sangeet`, `Haldi`, `Reception`, `Not attending`
   - **Guests**: short answer
2. In the Form's settings, turn off "Collect email addresses" and "Limit to 1
   response". Otherwise Google asks guests to sign in and the page's replies are
   rejected.
3. Open the menu (⋮), choose **Get pre-filled link**, type anything into each
   question, and copy the link. It contains `entry.NNNNNNNNN=` once per question.
   Those three numbers are the field IDs.
4. In `index.html`, search for `RSVP_CONFIG` and fill it in:
   ```js
   var RSVP_CONFIG = {
     action: "https://docs.google.com/forms/d/e/<FORM_ID>/formResponse",
     fields: { name: "entry.111", events: "entry.222", guests: "entry.333" }
   };
   ```
   `<FORM_ID>` is the long ID from the pre-filled link, and `viewform` becomes
   `formResponse`.
5. In the Form's **Responses** tab, choose **Link to Sheets** to see every reply
   in one spreadsheet.

Test it once from the live site and check that a row appears. Until
`RSVP_CONFIG` is filled in, the form tells guests it isn't connected yet rather
than pretending to send.

## Picking one version

Once a version is chosen, rename it to `index.html` and delete the other. The
URL to share stays the same.

## Still to fill in

- Jaipur highlights: swap in your own favourites
- Devanagari proofread
- `og-card.png`, the WhatsApp link preview image, is currently a stopgap
  screenshot that includes the site header
