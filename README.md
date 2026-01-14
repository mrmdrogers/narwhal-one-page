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
    │   ├── hero.png          # Cut-out hero portrait (transparent background)
    │   └── badge.png         # Campaign badge / logo
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

-   The hero portrait is positioned via CSS using a movable `artbox`
    container.
-   The image is clipped by the `.frame` container to respect rounded
    corners.
-   The portrait may intentionally overlap under the footer band for
    visual depth.
-   All layout behavior is controlled via CSS custom properties for easy
    tuning.

No client-side JavaScript is used.

------------------------------------------------------------------------

## Favicon

The favicon is a simplified, square version of the campaign badge.

Browsers load it automatically via:

``` html
<link rel="icon" href="/favicon.png">
```

------------------------------------------------------------------------

## Editing Content

To change: - **Text:** edit `index.html` - **Colors / layout:** edit
`styles.css` - **Links:** update the `<a href>` targets in
`index.html` - **Hero image positioning:** adjust CSS variables at the
top of `styles.css`

------------------------------------------------------------------------

## License / Usage

Internal campaign use only.
