# spb_mountains_tiles

Static XYZ raster tile pyramid for the **SPb Mountains** longread ([spbmlaplus/SPb_Mountains](https://github.com/spbmlaplus/SPb_Mountains)), covering the St. Petersburg agglomeration (~28.9–31.9°E, 59.5–60.4°N). Generated with `gdal2tiles.py --xyz --resampling=bilinear` from source TIFFs in EPSG:3857. Zoom range: **10–14**.

Migrated from the original `Pashteto/gavr-tiles` repo (2026-06-18). Only the `relief_hillshade` pyramid — the base raster actually rendered by the live site (base composition #1) — was carried over.

## Pyramid

| Path | Source | Tile URL template |
|---|---|---|
| `relief_hillshade/` | Pixel-wise multiply of `relief × hillshade luma`, pre-baked because MapLibre GL JS has no `mix-blend-mode: multiply` for raster layers. (15,719 PNGs, ~262 MB) | `relief_hillshade/{z}/{x}/{y}.png` |

`relief_hillshade` is the base raster for composition #1 in the longread's base-layer spec.

## Serving

- **GitHub Pages** (once enabled by a repo owner: Settings → Pages → Deploy from branch `main`): `https://spbmlaplus.github.io/spb_mountains_tiles/relief_hillshade/{z}/{x}/{y}.png`
- **jsDelivr CDN** (works without Pages): `https://cdn.jsdelivr.net/gh/spbmlaplus/spb_mountains_tiles@main/relief_hillshade/{z}/{x}/{y}.png`
