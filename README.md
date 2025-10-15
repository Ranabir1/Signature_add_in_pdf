# PDF Signature & Editor Tool

A powerful, client-side web application that allows you to add digital signatures to PDF documents and edit PDFs visually (draw, shapes, text, images), plus split and merge PDFs — all locally in your browser.

## Features

### 🖊️ **Signature Management**
- Upload signature images (JPG, PNG)
- Automatic white background removal with advanced algorithms
- Real-time preview with adjustable parameters
- Support for transparent signatures

### 📄 **PDF Processing**
- Upload any PDF document
- Add signatures to specific pages (first, last, or all pages)
- Download signed PDF instantly
- No server uploads - everything happens in your browser

### ✏️ **PDF Editor (New)**
- Open `PDF Editor` from the top-right link on the main page
- Tools: Select, Draw, Text, Image, Rectangle, Ellipse, Arrow, Highlighter
- Opacity control for all items and strokes
- Move/resize items, bring forward / send backward
- Undo / Redo, Clear current page
- Keyboard shortcuts: Delete to remove, Ctrl+D to duplicate
- Export your edits into a new PDF

### 🧩 **Split & Merge (New)**
- Split current PDF by page range (e.g., `1-3,5`) and download the extracted pages
- Merge multiple selected PDFs into a single document

### ⚙️ **Advanced Tools (New)**
- Open `Advanced Tools` from the top-right link on the main page
- Page manager: drag-and-drop reorder, rotate (±90°), delete pages
- Conversions:
  - Images → PDF (each image becomes a full page)
  - PDF → Images (PNG per page, downloaded as a ZIP)
  - DOCX → PDF (client-side, basic text/image rendering)
- 100% client-side using your browser; suitable for offline use when CDNs are mirrored locally

### 🎯 **Precise Placement Control**
- **Corner positioning**: Top-left, top-right, bottom-left, bottom-right
- **Custom coordinates**: Specify exact pixel positions
- **Size control**: Adjust width (50-300px) and height (20-200px)
- **Aspect ratio**: Option to maintain original proportions
- **Live preview**: See exactly where your signature will appear

### 🎨 **Advanced Background Removal**
- Intelligent white background detection
- Adjustable saturation threshold
- Feathering controls for smooth edges
- Blue ink boost for better signature preservation
- Local window analysis for textured paper

## How to Use

### Step 1: Upload PDF
1. Click "Click to upload a PDF file"
2. Select your PDF document
3. The filename will be displayed

### Step 2: Upload Signature
1. Click "Click to upload an image (JPG, PNG)"
2. Select your signature image
3. Optionally check "Remove white background from signature"
4. If background removal is enabled, adjust the parameters using the live preview

### Step 3: Configure Placement
1. **Select Page**: Choose which page(s) to sign (first, last, or all)
2. **Choose Position**: 
   - Use corner buttons for quick placement
   - Or enable "Use custom coordinates" for precise positioning
3. **Adjust Size**: 
   - Use sliders to set width and height
   - Enable "Maintain aspect ratio" to keep proportions
4. **Preview**: See exactly where your signature will appear

### Step 4: Add Signature
1. Click "Add Signature & Download"
2. Your signed PDF will download automatically

## PDF Editor Usage

1. Open `index.html` in your browser and click `Open PDF Editor`.
2. Click `Open PDF` and choose a PDF.
3. Choose a tool and edit directly on page canvases:
   - Draw: freehand drawing with stroke width, color, opacity
   - Text: enter text, set size, color, opacity; drag to move, resize by dragging
   - Image: place a local image; drag/resize; opacity supported
   - Rect / Ellipse / Arrow / Highlighter: click-drag to create shapes; opacity supported
4. Use `Undo`, `Redo`, `Bring ↑`, `Send ↓`, and `Clear page` in the left panel.
5. Click `Download Edited PDF` to export your changes.

### Split PDF
1. With a PDF opened in the editor, click `Split`.
2. Enter a range like `1-3,5` and confirm.
3. The selected pages download as `split.pdf`.

### Merge PDFs
1. Click `Merge` and pick multiple PDF files (use Ctrl/Shift select).
2. The files are merged in the order selected and download as `merged.pdf`.

## Advanced Tools Usage

1. Open `index.html` and click `Advanced Tools` (or open `advanced.html` directly).
2. Page manager:
   - Click `Open PDF` to load a document.
   - Click thumbnails to select pages; use `Rotate ⟲/⟳` or `Delete`.
   - Reorder by dragging thumbnails; click `Download` to export.
3. Conversions:
   - Images → PDF: select multiple images, click `Create PDF`.
   - PDF → Images (ZIP): choose a PDF, click `Convert` to download a ZIP of PNGs.
   - DOCX → PDF: choose a `.docx`, click `Convert` (basic text/image layout supported).

> Note: DOCX conversion is simplified for client-side use; complex layouts (tables, headers/footers, columns) may render differently.

## Technical Details

### Technologies Used
- **HTML5**: Modern semantic markup
- **CSS3**: Tailwind CSS for responsive design
- **JavaScript**: Vanilla JS for optimal performance
- **PDF-lib**: Client-side PDF manipulation
- **Canvas API**: Image processing and background removal
- **PDF.js**: High-fidelity PDF rendering for the editor and thumbnails
- **JSZip**: Zipping rendered images for PDF → Images conversion
- **FileSaver**: Save ZIPs and generated files client-side

### Browser Compatibility
- Chrome 60+
- Firefox 55+
- Safari 11+
- Edge 79+

### File Size Limits
- PDF files: Up to 50MB (browser dependent)
- Image files: Up to 10MB recommended

## Background Removal Algorithm

The tool uses an advanced algorithm to remove white backgrounds:

1. **Luminance Analysis**: Calculates pixel brightness
2. **Local Mean Comparison**: Compares each pixel to its local neighborhood
3. **Saturation Filtering**: Preserves colored ink while removing white
4. **Blue Ink Boost**: Special handling for blue ink signatures
5. **Feathering**: Smooth transitions for natural-looking edges

### Adjustable Parameters
- **Saturation Threshold**: How much color to preserve
- **Feather Start/End**: Transition zone boundaries
- **Local Window**: Neighborhood size for analysis
- **Blue Ink Boost**: Special treatment for blue signatures

## Privacy & Security

- **100% Client-side**: No files are uploaded to any server
- **Local Processing**: All operations happen in your browser
- **No Data Collection**: No personal information is stored or transmitted
- **Secure**: Your documents never leave your device

## Installation

No installation required! Simply:

1. Download the repository or the `index.html` entry page
2. Open it in any modern web browser
3. Use links to access `PDF Editor` and `Advanced Tools`

## File Structure

```
Signature_add_in_pdf/
├── index.html          # Signature tool (upload PDF + image signature)
├── editor.html         # Visual PDF editor (draw/text/image/shapes, split/merge)
├── advanced.html       # Advanced page manager + conversions (images↔PDF, DOCX→PDF)
└── README.md           # This documentation
```

## Troubleshooting

### Common Issues

**"Please select both a PDF and an image"**
- Ensure both files are selected before clicking "Add Signature & Download"

**Signature appears too small/large**
- Use the size controls in Step 3 to adjust width and height
- Enable "Maintain aspect ratio" for proportional scaling

**Background removal not working well**
- Adjust the saturation threshold (try values between 0.15-0.35)
- Modify feather start/end values (try 0.80-0.95)
- Increase local window size for textured paper

**PDF download not starting**
- Check if your browser blocks pop-ups
- Ensure you have sufficient disk space
- Try a different browser if issues persist

**Error: attempting to access detached ArrayBuffer (Split/Download)**
- Reload the page and open the PDF again; the app keeps a persistent copy internally
- Make sure to use the `Open PDF` button before `Split`

**PDF rendering not visible (Editor/Advanced)**
- Ensure internet access for the CDN of PDF.js
- If using offline environment, replace CDN with local copies of `pdf.min.js` and `pdf.worker.min.js`

### Performance Tips

- Use PNG images for signatures with transparency
- Keep PDF file sizes under 20MB for best performance
- Use JPG for signatures without transparency needs
- Close other browser tabs if processing large files

## Contributing

This is a standalone tool, but suggestions and improvements are welcome!

## License

This project is open source and available under the MIT License.

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Ensure you're using a supported browser
3. Try with smaller files to test functionality

---

**Made with ❤️ for easy PDF signing & editing**
