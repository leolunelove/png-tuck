<div align="center">

# PNG Tuck

**Less file, same image.**

A small, quiet tool for lossless PNG compression.  
Drop, choose, or paste your images. Download them a little lighter.

PNG only · Pixel-perfect · On your device

[Usage](#usage) · [Privacy](#privacy) · [Quality and limits](#quality-and-limits) · [Development](#development)

</div>

---

> **Publication status:** The application source upload and first GitHub Pages deployment are pending.

## Usage

1. **Add your PNGs.** Drag them in, choose files, or paste with `⌘ V` on macOS or `Ctrl V` on Windows and Linux.
2. **Let Tuck work.** Progress and results stay inside the drop area.
3. **Download.** Save an individual PNG or the whole batch as `png-tuck.zip`.

You can add more images to a batch, remove individual files, or clear everything and start again. No account, settings, or quality slider required.

## Privacy

Your images are processed in your browser, on your device. PNG Tuck has no image-upload endpoint, database, or analytics.

Image data stays in memory while the page is open; the app does not save it to browser storage. Downloads are saved to your device when you request them.

## Quality and limits

Tuck optimizes the PNG file without changing its decoded pixels. It preserves transparency and 16-bit detail, then checks the result against the original. If a result is larger or fails that check, it keeps the original.

Already optimized PNGs may stay the same size.

| Limit | Supported |
| :--- | :--- |
| Format | Still PNG images; animated PNGs are not supported |
| Image size | Up to 50 MiB per file |
| Dimensions | Up to 24 million pixels per image |
| Batch size | Up to 50 files, totaling 250 MiB |

## Development

<details>
<summary><strong>Local setup, project layout, and hosting</strong></summary>

These instructions apply once the application source has been uploaded.

### Run locally

From the repository root:

```sh
python3 -m http.server 4173 --directory dist
```

Open [localhost:4173](http://localhost:4173). No build step or package installation is required. Serve the files over HTTP so the compressor's Web Worker can load.

### Project layout

```text
png-tuck/
├── .github/workflows/pages.yml   # GitHub Pages deployment
├── dist/
│   ├── index.html               # Page structure
│   ├── style.css                # Layout and micro-interactions
│   ├── app.js                   # Input, queue, results, and downloads
│   ├── compress-worker.js       # Compression and pixel verification
│   └── vendor/                  # Bundled codecs and their licenses
└── README.md
```

### Hosting

The prepared GitHub Actions workflow publishes `dist` to GitHub Pages when changes reach `main`. The repository's Pages publishing source is set to **GitHub Actions**.

### Dependencies

Compression uses OxiPNG, pixel verification uses a PNG decoder, and batch downloads use JSZip. These dependencies are bundled with the application; their licenses remain alongside the vendored code.

</details>

---

<div align="center">

Created by [@leo](https://leolune.com)

</div>
