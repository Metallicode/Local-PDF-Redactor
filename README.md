
# 🔒 Secure Local PDF Redactor

A simple, privacy-focused tool to obscure sensitive information in PDF documents. It runs entirely in your web browser—**no files are ever uploaded to a server.**

## 🚀 Features

* **100% Client-Side:** Your files never leave your computer. The processing happens in your browser's memory.
* **Smart Pixelation:** Select areas to scramble text using a high-performance canvas pixelation effect.
* **Secure Export:** Downloads the redacted document as a **flattened image PDF**. This ensures the obscured text underneath cannot be selected, searched, or revealed.
* **Undo Support:** Includes a history stack with `Ctrl+Z` support.
* **Restore Tool:** Made a mistake? Use the "Restore" tool to wipe away redactions and reveal the original document.

## 🛠️ How to Use

1. **Open the Tool:** Simply double-click `redactor.html` to open it in Chrome, Firefox, or Edge.
2. **Upload:** Click "Choose File" to load a PDF.
3. **Redact:**
* Ensure the **Pixelate** tool is active.
* Click and drag a box over the text you want to hide.


4. **Correct:**
* Press `Ctrl+Z` to undo the last action.
* Or, switch to the **Restore** tool and drag over an area to fix it.


5. **Download:** Click **Download Image PDF** to save the safe version.

## ⚙️ How it Works (Technical)

This tool utilizes **HTML5 Canvas** for image manipulation.

1. **Rendering:** It uses `PDF.js` to render the PDF page onto two canvases:
* **Visible Canvas:** Where the user interacts.
* **Clean Canvas (Hidden):** Stores the original high-resolution render.


2. **Pixelation:** When you select an area, the tool shrinks that specific chunk of image data down to 20% of its size, then stretches it back up with `imageSmoothingEnabled = false`. This creates a mathematically irreversible mosaic effect.
3. **Export:** It uses `jsPDF` to take a snapshot of the canvas (as a JPEG) and wraps it inside a new PDF container.

## 📦 Dependencies

This project uses the following libraries via CDN (no installation required):

* [PDF.js](https://mozilla.github.io/pdf.js/) (by Mozilla) - For parsing and rendering PDFs.
* [jsPDF](https://github.com/parallax/jsPDF) - For generating the downloadable PDF file.

## ⚠️ Limitations

* **Single Page Only:** Currently optimized for single-page documents (or the first page of a multi-page file).
* **Resolution:** Exports are rasterized (images). While safe, they may not be as crisp as vector PDFs at very high zoom levels.

## 📝 License

Free to use and modify. MIT License.
