# national-archives-catalog-downloader

A small toolkit for downloading images from [National Archives catalog](https://catalog.archives.gov/) pages and converting them to PDF using [Playwright](https://playwright.dev/) browser automation.

## Scripts

### `download-images <url>`

Navigates to a catalog URL, finds all image thumbnails, clicks each to load the full-resolution viewer, and downloads them sequentially.

```bash
./download-images https://catalog.archives.gov/id/332275713
```

Output is saved to `results/<page-title>/images/` with zero-padded filenames (e.g. `0001.tif`, `0002.tif`).

### `create-pdf <folder>`

Converts all images in `<folder>/images/` into a single PDF file.

```bash
./create-pdf ./results/number-66-1-of-2
```

Output: `<folder-name>.pdf` in the parent directory. Supports `.tif`, `.tiff`, `.jpg`, `.jpeg`, `.png`, `.webp`.

### `extract-text <folder>`

OCR all `.tif` files in a folder using Tesseract, outputting a `.txt` file alongside each image.

```bash
./extract-text ./results/number-66-1-of-2/images
```

Requires [`tesseract`](https://github.com/tesseract-ocr/tesseract) to be installed.

## Example workflow

```bash
./download-images https://catalog.archives.gov/id/332275713
./create-pdf ./results/number-66-1-of-2
./extract-text ./results/number-66-1-of-2/images
```

## Requirements

- [Node.js `^22.0.0`](https://nodejs.org/)
- [pnpm](https://pnpm.io/)
- [tesseract](https://github.com/tesseract-ocr/tesseract) — for `extract-text`

## Install

```bash
pnpm install
```

## Dependencies

- [`playwright`](https://playwright.dev/) — browser automation
- [`pdf-lib`](https://pdf-lib.js.org/) — PDF creation
- [`sharp`](https://sharp.pixelplumbing.com/) — image processing
