## PDF Signature Tool

Add a signature image to a PDF (bottom-right of the last page) entirely in your browser.

### Features
- **Local-only processing**: Your PDF and signature never leave your machine.
- **Background removal**: Optional removal of white/light backgrounds with feathered edges.
- **PNG/JPG support**: JPG or PNG input; processed output is embedded with transparency.
- **No build step**: Open a single HTML file in a modern browser.

### Requirements
- A modern browser (Chrome, Edge, or Firefox latest recommended).
- Local files: `Sig_add_tool.html` in this folder.

### Quick Start
1. Open `Sig_add_tool.html` in your browser.
2. Step 1: Upload your PDF.
3. Step 2: Upload your signature image (PNG/JPG).
4. (Optional) Check "Remove white background" for scanned signatures.
5. Click "Add Signature & Download" to save the signed PDF.

### How It Works
- Uses `pdf-lib` to load and modify the PDF.
- Embeds your signature image and positions it at the bottom-right corner of the last page with padding.
- When background removal is enabled, the signature image is processed on a canvas to make white/light pixels transparent and feather edge halos.

### Background Removal Notes
- The algorithm uses luminance and saturation thresholds with a smooth feather (`smoothstep`) between `featherStart` and `featherEnd` to reduce halos.
- Tunable constants live inside `removeWhiteBackground(...)` in `Sig_add_tool.html`:
  - `luminanceThreshold`
  - `saturationThreshold`
  - `featherStart`
  - `featherEnd`
- If halos persist, slightly lower `featherStart` or increase `featherEnd` for a stronger fade.

### Troubleshooting
- **Button disabled**: Ensure both a PDF and an image are selected.
- **No transparency**: Ensure "Remove white background" is checked for scanned signatures with white paper; PNG output with alpha is embedded.
- **Large images look small**: The signature is scaled to a fixed width (default 100px). Adjust `signatureWidth` in `Sig_add_tool.html`.
- **Positioning**: Adjust `padding` and/or change `x`/`y` in `drawImage` to move the signature.
- **Errors**: Open the browser console for details (F12).

### Privacy & Security
- All operations are client-side; no files are uploaded.
- You can run fully offline once dependencies are cached by the browser. First load requires network to fetch CDNs:
  - `https://cdn.tailwindcss.com`
  - `https://unpkg.com/pdf-lib@1.17.1/dist/pdf-lib.min.js`

### Development
- Main file: `Sig_add_tool.html`
- Key functions: `removeWhiteBackground(...)`, `dataURLToUint8Array(...)`
- Library: `PDFLib` (`pdf-lib` via CDN)

### License
Add your preferred license here.


