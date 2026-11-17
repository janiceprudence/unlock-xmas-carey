# Strong Bailey Christmas Countdown

A kawaii Christmas countdown featuring the Strong Bailey mascot, an interactive snow globe, drifting frost, a gold wand cursor, and an embedded Spotify playlist.

## Features

- Counts down to **December 25, 2026 at midnight HKT (UTC+8)**.
- Shake the globe to wobble it, swirl the snow, and reveal up to three cracks.
- Preview the Christmas release now, then reset the globe and replay it. Previewing does not change the countdown.
- At Christmas midnight HKT, the glass fades, the singer rises, and starbursts appear.
- Features a chibi Mariah Carey illustration inside the globe, drifting frost particles across the page, and a gold magic-wand cursor on desktop. Touch devices keep their normal pointer behavior.
- A landscape four-photo booth creates a single Strong Bailey Christmas collage; users can copy it to the clipboard or download it. Camera access starts only after the user taps Turn on camera, and photos stay in the browser.
- Spotify's embedded player provides its own play and pause controls.
- Kawaii pink-and-cream layout with responsive desktop/mobile styling and reduced-motion support.

## Project files

- `index.html` — complete page, including the inline snow-globe SVG.
- `assets/favicon.svg` — browser tab icon.
- `assets/magic-wand-cursor.svg` — custom 32 × 32 gold wand cursor; the hotspot is the star tip.
- `assets/chibi-mariah.png` — transparent chibi singer artwork in the globe.
- `assets/strong-bailey-logo.png` — Strong Bailey brand logo.
- `assets/strong-bailey-mascot.png` — the Strong Bailey mascot with a ribboned candy cane, styled to match the holiday sticker set.
- `assets/strong-bailey-stickers.png` — three Strong Bailey sticker poses used on the photo booth frame.
- `assets/strawberry-apples.png` — cartoon strawberry-apple friends and a Christmas deer for the playlist, matching Strong Bailey’s sticker style.
- `assets/snowflake.svg` — shake button icon.
- `assets/social-card.svg` — social preview graphic.

The globe frame stays inline in `index.html` so CSS can animate the glass, snow, cracks, and character layers. Character art and the Strong Bailey stickers are separate transparent PNG assets. The page has no JavaScript dependencies.

## Run locally

Serve the folder over HTTP so the Spotify embed and relative assets load consistently:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>. On Windows you can use `py -m http.server 8000` instead. Docker, Java, and a backend are not needed.

## Photo booth saving and retakes

- After four photos, JavaScript prepares a PNG collage and displays a full-size preview. Download photo saves this collage; no separate Save button is required.
- Copy photo needs HTTPS (or localhost), a browser supporting image clipboard writes, and clipboard permission. Embedded previews may block copying or downloading; open the site directly in a browser.
- If the browser blocks a button, right-click or press and hold the preview to save or copy the image, or use Open / save full-size photo.
- Hover over a captured photo to reveal Delete. Keyboard users can Tab to Delete; touch devices always show it. Deleting a shot preserves the other photos. Turn the camera back on if needed and capture the empty slot; the collage regenerates when all four slots are filled.
- Deleting or retaking photos clears the previous export. Photos stay in memory and disappear when the page is refreshed or closed.
- Use localhost or HTTPS for the full branded export. When opened as a local file, decorative images are omitted from the export to avoid browser canvas restrictions.

## Publish with GitHub Pages

1. Create a GitHub repository and upload `index.html`, `README.md`, and the `assets` folder.
2. Open **Settings → Pages** in the repository.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the default branch and the repository root, then save.
5. Open the Pages URL GitHub displays after deployment.

For a custom domain, use an absolute URL for the Open Graph image in the `og:image` metadata.

## Spotify notes

The page embeds the supplied playlist; it does not sign in to or control a visitor's Spotify account. Visitors start or pause playback inside Spotify's player. An internet connection is required.

The countdown currently targets Christmas 2026. To reuse it another year, update the UTC target in the page's JavaScript and the displayed date in the page text.

## License

No license is specified. Add one before granting reuse rights.
