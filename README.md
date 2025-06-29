# 📄 shrink-scanned-pdf

A lightweight shell script to **compress and resize scanned PDF files** that are made up of full-page JPEG scans. Perfect for shrinking large PDFs from scanners while maintaining readability.

---

## 🚀 Features

- ✅ Recompresses embedded JPEG scans with custom quality
- ✅ Optionally resizes each page (e.g. scale to 50%)
- ✅ Accepts easy-to-use command-line flags
- ✅ Prompts to install missing tools via Homebrew
- ✅ Written in pure Bash — no Python or bloated dependencies

---

## 🛠️ Dependencies

These tools are required (you'll be prompted to install via Homebrew if missing):

- [`pdfimages`](https://poppler.freedesktop.org/) – from Poppler
- [`mogrify`](https://imagemagick.org/) – from ImageMagick
- [`img2pdf`](https://gitlab.mister-muffin.de/josch/img2pdf) – lightweight PDF builder from images

To install them manually:

```bash
brew install poppler imagemagick img2pdf
```

---

## 📦 Installation

Clone the repo and make the script executable:

```bash
git clone https://github.com/yourusername/shrink-scanned-pdf.git
cd shrink-scanned-pdf
chmod +x shrinkpdf
```

---

## 📋 Usage

```bash
./shrinkpdf input.pdf output.pdf [--quality N] [--resize PERCENT]
```

### Example:

```bash
# Basic usage (default quality 40, no resize)
./shrinkpdf scan.pdf compressed.pdf

# Custom JPEG quality
./shrinkpdf scan.pdf compressed.pdf --quality 30

# Resize pages to 50% and compress
./shrinkpdf scan.pdf compressed.pdf --quality 35 --resize 50
```

---

## ⚙️ Options

| Flag           | Description                                        | Default |
|----------------|----------------------------------------------------|---------|
| `--quality N`  | JPEG quality (1–100). Lower = smaller file.        | `40`    |
| `--resize P`   | Resize each page to P%. E.g. `50` = half size.     | `100`   |

### 🔍 Tips:

- **Quality 60–80** ➜ High-quality scans (e.g. for documents with images)
- **Quality 30–50** ➜ Good for most text-only scans
- **Resize 50%** ➜ Reduces physical size and file weight
- Combine both to shrink files significantly!

---

## 🧪 How it works

1. Extracts each page image from the PDF using `pdfimages`
2. Recompresses images using `mogrify` (ImageMagick)
3. Optionally resizes the images
4. Reassembles the final PDF using `img2pdf`

This is especially useful for:
- Scans made from physical printers
- PDFs that are actually image dumps
- Reducing storage or upload size

---

## ✅ License

MIT – free to use, share, and adapt.

---

## 📬 Contributions

PRs and issues welcome! If you want to add multi-threading, batch support, or preserve metadata — feel free to contribute!
