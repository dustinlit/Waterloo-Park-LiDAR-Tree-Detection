# Rasterio Reference: Parameters, Attributes, and Functions

## 1. Opening & Inspecting Datasets
- **[rasterio.open](ca://s?q=Rasterio_open_usage)** — Opens a raster for reading or writing.
- **[dataset.profile](ca://s?q=Rasterio_profile)** — Full metadata dict: driver, dtype, count, width, height, CRS, transform, etc.
- **[dataset.meta](ca://s?q=Rasterio_meta)** — Legacy alias for profile.
- **[dataset.read](ca://s?q=Rasterio_read)** — Reads full raster or a window into a NumPy array.
- **[dataset.read_masks](ca://s?q=Rasterio_read_masks)** — Reads mask band(s).
- **[dataset.tags](ca://s?q=Rasterio_tags)** — Reads global metadata.
- **[dataset.tags(band=i)](ca://s?q=Rasterio_band_tags)** — Reads per-band metadata.

---

## 2. CRS & Georeferencing
- **[dataset.crs](ca://s?q=Rasterio_crs)** — Returns CRS object (EPSG, WKT, PROJ).
- **[dataset.transform](ca://s?q=Rasterio_transform)** — Affine transform mapping pixel → world coordinates.
- **[Affine.from_gdal](ca://s?q=Rasterio_Affine_from_gdal)** — Build transform from GDAL geotransform.
- **[dataset.bounds](ca://s?q=Rasterio_bounds)** — Returns bounding box in CRS units.
- **[dataset.index](ca://s?q=Rasterio_index)** — Convert (x, y) → (row, col).
- **[dataset.xy](ca://s?q=Rasterio_xy)** — Convert (row, col) → (x, y).

---

## 3. Windowed Reading & Writing
- **[rasterio.windows.Window](ca://s?q=Rasterio_Window)** — Defines a pixel window (row/col offsets + size).
- **[rasterio.windows.from_bounds](ca://s?q=Rasterio_window_from_bounds)** — Build window from geographic bounds.
- **[dataset.read(window=...)](ca://s?q=Rasterio_read_window)** — Read a subset of the raster.
- **[dataset.write(window=...)](ca://s?q=Rasterio_write_window)** — Write into a subset of the raster.
- **[rasterio.windows.transform](ca://s?q=Rasterio_window_transform)** — Compute transform for a window.

---

## 4. Writing New Rasters
- **[dataset.write](ca://s?q=Rasterio_write)** — Write NumPy arrays to a raster.
- **[rasterio.open(..., 'w')](ca://s?q=Rasterio_open_write)** — Create a new raster with a profile.
- **[profile.update](ca://s?q=Rasterio_profile_update)** — Modify metadata before writing.
- **[dataset.close](ca://s?q=Rasterio_close)** — Flush and close file handles.

---

## 5. Masks, Nodata, and Dtypes
- **[dataset.nodata](ca://s?q=Rasterio_nodata)** — Returns nodata value.
- **[dataset.read(masked=True)](ca://s?q=Rasterio_masked_read)** — Returns masked array respecting nodata.
- **[dataset.dtypes](ca://s?q=Rasterio_dtypes)** — Data type(s) of bands.
- **[dataset.colorinterp](ca://s?q=Rasterio_colorinterp)** — Color interpretation (RGB, alpha, palette).

---

## 6. Raster Properties & Structure
- **[dataset.width](ca://s?q=Rasterio_width)** — Number of columns.
- **[dataset.height](ca://s?q=Rasterio_height)** — Number of rows.
- **[dataset.count](ca://s?q=Rasterio_count)** — Number of bands.
- **[dataset.block_shapes](ca://s?q=Rasterio_block_shapes)** — Internal tile/block size.
- **[dataset.overviews](ca://s?q=Rasterio_overviews)** — Overview levels for each band.

---

## 7. Reprojection & Warping
- **[rasterio.warp.reproject](ca://s?q=Rasterio_reproject)** — Reproject arrays between CRS.
- **[rasterio.warp.calculate_default_transform](ca://s?q=Rasterio_calculate_default_transform)** — Compute new transform/resolution for reprojection.
- **[rasterio.warp.resample](ca://s?q=Rasterio_resample)** — Resampling methods (nearest, bilinear, cubic).

---

## 8. Dataset Creation & Drivers
- **[GTiff driver](ca://s?q=Rasterio_GTiff_driver)** — Standard GeoTIFF.
- **[COG driver](ca://s?q=Rasterio_COG_driver)** — Cloud-Optimized GeoTIFF.
- **[MemoryFile](ca://s?q=Rasterio_MemoryFile)** — In-memory raster creation.
- **[rasterio.shutil.copy](ca://s?q=Rasterio_copy)** — Copy rasters with new metadata.

---

## 9. Raster Math & Masking Helpers
- **[rasterio.mask.mask](ca://s?q=Rasterio_mask)** — Mask raster by polygons.
- **[rasterio.features.rasterize](ca://s?q=Rasterio_rasterize)** — Burn vector shapes into a raster.
- **[rasterio.features.shapes](ca://s?q=Rasterio_shapes)** — Polygonize raster regions.
- **[rasterio.enums.Resampling](ca://s?q=Rasterio_Resampling)** — Enum of resampling methods.

---

## 10. Common Utility Functions
- **[rasterio.plot.show](ca://s?q=Rasterio_plot_show)** — Quick visualization.
- **[rasterio.merge.merge](ca://s?q=Rasterio_merge)** — Mosaic multiple rasters.
- **[rasterio.mask.bounds](ca://s?q=Rasterio_mask_bounds)** — Compute bounds of masked region.
- **[rasterio.fill.fillnodata](ca://s?q=Rasterio_fillnodata)** — Interpolate nodata regions.

