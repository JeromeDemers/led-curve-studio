# Clicks LED — Curve Studio

A dependency-free LED animation designer that runs entirely in one `index.html`.

## Use it

Open `index.html` in a current browser. No install, build step, web server, or network connection is required.

1. Choose **Change image** or drop a photo onto the preview.
2. Choose **Edit LED**, then drag the LED body to move it.
3. Use the corner and rotation handles to size and orient the light.
4. Pick a shape, color, glow spread, preset, and cycle speed.
5. Drag curve points to control brightness over time. Double-click the curve to add a point or a non-endpoint handle to remove it.

The playhead can be dragged to preview a moment in the cycle. Keyboard users can nudge the LED with the arrow keys and edit selected curve points with the arrow and Delete keys.

## Saving and sharing

- Settings save automatically in browser storage.
- Uploaded images are resized to a maximum 1600 px edge and kept locally in IndexedDB.
- **Copy Settings JSON** shares the small animation and placement setup without the image.
- **Download Project JSON** includes the current image.
- **Paste / Import** accepts either format and validates values before applying them.

All processing stays in the browser. The app has no runtime dependencies and makes no network requests.
