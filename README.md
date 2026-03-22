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

## Example workflow

```bash
./download-images https://catalog.archives.gov/id/332275713
./create-pdf ./results/number-66-1-of-2
```

## Requirements

- Node.js `^24.0.0`
- [pnpm](https://pnpm.io/)

## Install

```bash
pnpm install
```

## Dependencies

- [`playwright`](https://playwright.dev/) — browser automation
- [`pdf-lib`](https://pdf-lib.js.org/) — PDF creation
- [`sharp`](https://sharp.pixelplumbing.com/) — image processing
