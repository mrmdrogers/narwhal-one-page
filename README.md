# Campaign Landing Page

This repository contains a **simple static landing page** intended to
route visitors to:

-   A **ballot petition** website
-   The **main campaign website**

The page is intentionally minimal: plain HTML, CSS, and static images
--- no JavaScript frameworks or build tools.

------------------------------------------------------------------------

## Project Structure

    .
    ├── index.html            # Main landing page
    ├── styles.css            # Page styles
    ├── favicon.ico           # Site favicon (recommended over .png)
    ├── apple-touch-icon.png  # Apple Touch icon
    ├── images/
    │   ├── hero.png          # Ken Miyagishima portrait (transparent cut-out)
    │   ├── jc-lopez.png      # J.C. Lopez portrait (transparent cut-out)
    │   ├── badge.png         # KEN campaign badge / logo
    │   ├── zia_badge.png     # New Mexico Zia badge
    │   └── video-poster.jpg  # Poster frame shown before the video plays
    ├── videos/
    │   └── landing-video.mp4 # Web-optimized campaign video (H.264, faststart)
    └── README.md

------------------------------------------------------------------------

## Local Development

No build step is required.

### Option 1: Open directly

You can open `index.html` directly in your browser.

### Option 2: Local web server (recommended)

Using Python:

``` bash
python3 -m http.server 5500
```

Then open:

    http://localhost:5500

This more closely matches production behavior.

------------------------------------------------------------------------

## Deployment (Cloudflare Pages)

This site is designed to be deployed via **Cloudflare Pages**.

### Recommended setup

-   **Framework preset:** None
-   **Build command:** *(leave empty)*
-   **Output directory:** `/`

Cloudflare Pages will automatically serve `index.html` at the root.

Every push to `main` triggers a new deployment.

------------------------------------------------------------------------

## Assets & Design Notes

The palette is indigo-forward on a light base; yellow is used only as a
deliberate accent (the headline marker, the accent shape behind the video,
the petition buttons, link underlines). Headlines use the **Archivo**
display typeface (loaded from Google Fonts); body text falls back to the
system sans. The layout uses **rounded, overlapping panels** rather than
flat stacked bands, so the sections interlock (soft seams + layering)
instead of reading as boxes.

1.  **Sticky nav (frosted white)** — the KEN brand lockup (badge mark +
    "Ken / for New Mexico"), the ticket wordmark, and an always-visible
    "Sign the petition" pill that jumps to the CTA (`#sign`).
2.  **Hero (asymmetric)** — headline on the left, the campaign video on
    the right (over a tilted yellow accent shape). The video is
    click-to-play so Ken's spoken message and audio are preserved;
    `images/video-poster.jpg` (the campaign splash end-card) is shown
    until it plays, and the player dips down over the ticket panel below.
    `videos/landing-video.mp4` is a web-optimized H.264 encode (the large
    camera-original source is git-ignored). To refresh it, re-encode with
    faststart, e.g.
    `ffmpeg -i SOURCE -c:v libx264 -crf 24 -movflags +faststart -c:a aac -b:a 128k videos/landing-video.mp4`.
3.  **Ticket (light panel)** — both candidates as transparent cut-out
    portraits in rounded, hover-lift cards (editorially staggered): Ken
    Miyagishima (`images/hero.png`) for Governor and J.C. Lopez
    (`images/jc-lopez.png`) for Lt. Governor.
4.  **Call to action (indigo panel)** — placed *after* the ticket. New
    Mexico requires separate signatures per candidate, so there are two
    petition buttons linking to each candidate's own SOS petition URL.
5.  **Footer (deep indigo)** — the Zia identity mark, the ticket
    wordmark, and the legally required "Paid for by…" disclaimer.

-   Copy is written in the first person ("we / us / our"), as the ticket
    addressing the voter.
-   Spacing, color, max-width, and panel rounding are driven by CSS
    custom properties and `clamp()` at the top of `styles.css`.
-   Responsive: the hero stacks under 860px; the ticket goes
    single-column and buttons full-width under 640px. Hover lifts and
    smooth scrolling respect `prefers-reduced-motion`.

No client-side JavaScript is used. The only external dependency is the
Google Fonts stylesheet for Archivo.

------------------------------------------------------------------------

## Favicon

The favicon is a simplified, square version of the campaign badge.

Browsers load it automatically via:

``` html
<link rel="icon" href="/favicon.png">
```

------------------------------------------------------------------------

## Editing Content

To change: - **Text / candidate names:** edit `index.html` - **Colors,
spacing, max-width:** edit the CSS custom properties at the top of
`styles.css` - **Petition links:** update the two `Sign for ...` button
`<a href>` targets in the CTA section of `index.html` (J.C. Lopez's
is marked with a `TODO` comment until his own petition URL is known) -
**Website link:** update the `.cta__website` and `.brand` targets -
**Video:** replace `videos/landing-video.mp4` - **Candidate photos:**
replace `images/hero.png` / `images/jc-lopez.png` (transparent cut-outs,
framed 4:5 and top-aligned inside `.candidate__photo`)

------------------------------------------------------------------------

## License / Usage

Internal campaign use only.
