# Strong Bailey Christmas Countdown

A kawaii Christmas countdown featuring Strong Bailey, an interactive snow globe unlocking Mariah Carey, drifting frost, a gold wand cursor, photo booth and an embedded Spotify playlist.

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

## How HTML, CSS, and JavaScript work together

Everything runs in the browser from `index.html`:

- **HTML** defines the page structure, buttons, four photo slots, video element, and Spotify embed.
- **CSS** controls the layout, colours, responsive styling, animations, and when each photo's Delete button appears on hover or keyboard focus. Touch devices always show Delete on captured photos.
- **JavaScript** handles the countdown, button interactions, camera access, photo capture, collage creation, downloading, and copying.

### Where JavaScript is used

The JavaScript lives inside the `<script>` block near the bottom of [index.html](index.html). There is no separate `.js` file or JavaScript framework.

| Feature | What JavaScript does | Main functions or handlers |
| --- | --- | --- |
| Christmas countdown | Calculates the remaining time, updates it every second, and triggers the Christmas release. | `tick()`, `setInterval()` |
| Interactive snow globe | Responds to clicks and keyboard input, reveals cracks, and triggers CSS animations. | `shake()` |
| Preview the thaw | Toggles the Christmas animation preview and resets it. | `previewThaw()` |
| Playlist button | Scrolls to Spotify and updates the playback hint. Playback itself is handled by Spotify's embedded player. | `playButton` click handler |
| Camera | Requests permission, shows the live feed in the next empty photo slot, and stops the camera after four shots or when leaving the page. | `positionBoothCamera()`, `stopBoothCamera()`, `boothCameraButton` click handler |
| Take photos | Captures a mirrored frame from the camera using Canvas and keeps the photo in browser memory. | `boothSnapButton` click handler |
| Delete one photo | Adds a Delete button to each slot, removes only the selected photo, and clears the previous collage so the empty slot can be retaken. | `.photo-delete` click handler, `nextBoothSlot()`, `clearBoothExport()` |
| Retake all | Clears all four photos and the generated collage. | `boothRetakeButton` click handler |
| Build the collage | Draws the four photos, frame, text, and branding onto a Canvas and exports a PNG. | `composeBooth()`, `loadImage()`, `drawCover()`, `roundedRect()` |
| Download photo | Uses a browser object URL and a download link to save the PNG. | `boothDownloadButton` click handler |
| Copy photo | Writes the PNG to the clipboard through the browser Clipboard API. | `boothCopyButton` click handler, `navigator.clipboard.write()` |
| Status messages | Explains camera, capture, export, and permission states. | `setBoothStatus()` |

Photo capture and export use built-in browser APIs. No Docker, Java service, Python backend, database, or separate Save button is required. Python is only an optional way to serve the files locally.

## Photo booth saving and retakes

- After four photos, JavaScript prepares a PNG collage. Download photo saves this collage; no separate Save button is required.
- Copy photo needs HTTPS (or localhost), a browser supporting image clipboard writes, and clipboard permission. Embedded previews may block copying or downloading; open the site directly in a browser.
- If copying is blocked, use Download photo. If downloading is blocked, allow downloads in your browser and try again.
- Hover over a captured photo to reveal Delete. Keyboard users can Tab to Delete; touch devices always show it. Deleting a shot preserves the other photos. Turn the camera back on if needed and capture the empty slot; the collage regenerates when all four slots are filled.
- Deleting or retaking photos clears the previous export. Photos stay in memory and disappear when the page is refreshed or closed.
- Use localhost or HTTPS for the full branded export. When opened as a local file, decorative images are omitted from the export to avoid browser canvas restrictions.

## Spotify notes

The page embeds the supplied playlist; it does not sign in to or control a visitor's Spotify account. Visitors start or pause playback inside Spotify's player. An internet connection is required.

The countdown currently targets Christmas 2026. To reuse it another year, update the UTC target in the page's JavaScript and the displayed date in the page text.

## Licensing

The website code is licensed under the MIT License (see [LICENSE](LICENSE)).

Strong Bailey character, logo, and original artwork © 2026 Janice Mook.
All rights reserved. These assets are not covered by the MIT License.

Third-party images, likenesses, and playlist content remain subject to
their respective rights holders’ terms.