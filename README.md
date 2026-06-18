# spb_mountains_tiles

Static XYZ raster tile pyramid for the **SPb Mountains** longread ([spbmlaplus/SPb_Mountains](https://github.com/spbmlaplus/SPb_Mountains)), covering the St. Petersburg agglomeration (~28.9–31.9°E, 59.5–60.4°N). Generated with `gdal2tiles.py --xyz --resampling=bilinear` (or equivalent) from source TIFFs in EPSG:3857. Zoom range: **10–14**.

Migrated from the original `Pashteto/gavr-tiles` repo (2026-06-18).

## Pyramids

| Path | Source | Tiles | Size | Tile URL template |
|---|---|---:|---:|---|
| `relief_water1/` | `relief_water1.tif` — composite relief + water bodies (RGBA). Built 2026-06-18. **Target layer for base composition #1** (pending app manifest update in `SPb_Mountains`). | 15,719 | ~191 MB | `relief_water1/{z}/{x}/{y}.png` |
| `relief_hillshade/` | Legacy: pixel-wise multiply of `relief × hillshade luma`. Retained until the app switches to `relief_water1`. | 15,719 | ~262 MB | `relief_hillshade/{z}/{x}/{y}.png` |

`relief_water1` shares the same XYZ grid as `relief_hillshade` (identical tile indices at z=10–14).

## Serving

- **GitHub Pages** (Settings → Pages → Deploy from branch `main`):
  - `https://spbmlaplus.github.io/spb_mountains_tiles/relief_water1/{z}/{x}/{y}.png`
  - `https://spbmlaplus.github.io/spb_mountains_tiles/relief_hillshade/{z}/{x}/{y}.png` (legacy)
- **jsDelivr CDN**: `https://cdn.jsdelivr.net/gh/spbmlaplus/spb_mountains_tiles@main/relief_water1/{z}/{x}/{y}.png`

## Regeneration

See `../tile-build/README.md` in the parent workspace for the build script and validation steps.
