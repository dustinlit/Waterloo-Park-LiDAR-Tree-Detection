# LAS / LAZ File Validation Checklist (CRS, Metadata, Geometry)

## 1. Coordinate System (CRS) Checks
- **[Check CRS exists](ca://s?q=Check_LAS_CRS_exists)** — Confirm `las.header.parse_crs()` returns a valid CRS object.
- **[Check EPSG code validity](ca://s?q=Check_LAS_EPSG_validity)** — Ensure the EPSG code matches the project specification.
- **[Check projection type](ca://s?q=Check_LAS_projection_type)** — UTM vs State Plane vs Geographic; verify it matches expected region.
- **[Check units](ca://s?q=Check_LAS_units)** — Confirm horizontal & vertical units (meters vs feet).
- **[Check vertical datum](ca://s?q=Check_LAS_vertical_datum)** — NAVD88 vs ellipsoid; ensure GEOID model is documented.
- **[Check CRS VLR consistency](ca://s?q=Check_LAS_CRS_VLR_consistency)** — GeoTIFF keys, WKT VLR, and EPSG must agree.

---

## 2. Coordinate Range & Sanity Checks
- **[Check X/Y ranges](ca://s?q=Check_LAS_XY_ranges)** — Ensure coordinates fall within expected bounding box.
- **[Check Z range](ca://s?q=Check_LAS_Z_range)** — Elevation should match terrain expectations (no negative mountains).
- **[Check for unit mismatch](ca://s?q=Check_LAS_unit_mismatch)** — Z values too large/small often indicate feet vs meters confusion.
- **[Check for offset errors](ca://s?q=Check_LAS_offset_errors)** — Wrong offsets cause huge coordinate shifts (e.g., millions of meters off).
- **[Check for scale errors](ca://s?q=Check_LAS_scale_errors)** — Too-large scale causes rounding; too-small scale causes precision loss.

---

## 3. Header Integrity Checks
- **[Check point count](ca://s?q=Check_LAS_point_count)** — Compare header count vs actual count inferred from file size.
- **[Check point format](ca://s?q=Check_LAS_point_format)** — Ensure correct format (6/7/8/9/10) for the dataset type.
- **[Check point record length](ca://s?q=Check_LAS_point_record_length)** — Must match the point format + extra bytes.
- **[Check VLR presence](ca://s?q=Check_LAS_VLR_presence)** — Ensure required VLRs exist (CRS, Extra Bytes, waveform, etc.).
- **[Check EVLR presence](ca://s?q=Check_LAS_EVLR_presence)** — Required for waveform or large metadata blocks.
- **[Check creation year/day](ca://s?q=Check_LAS_creation_date)** — Should match acquisition metadata.

---

## 4. Extra Bytes & Vendor Field Checks
- **[Check Extra Byte definitions](ca://s?q=Check_LAS_extra_byte_definitions)** — Ensure every extra dimension has a matching VLR.
- **[Check for unknown dimensions](ca://s?q=Check_LAS_unknown_dimensions)** — Unknown fields indicate missing or corrupted VLRs.
- **[Check vendor-specific fields](ca://s?q=Check_LAS_vendor_fields)** — Leica, RIEGL, Optech fields must match sensor type.
- **[Check waveform metadata](ca://s?q=Check_LAS_waveform_metadata)** — Required for point formats 9 and 10.

---

## 5. Geometry & Point Attribute Checks
- **[Check return numbers](ca://s?q=Check_LAS_return_numbers)** — Ensure return numbering is valid (1 ≤ return ≤ number_of_returns).
- **[Check classification codes](ca://s?q=Check_LAS_classification_codes)** — Must follow ASPRS standards unless documented.
- **[Check intensity range](ca://s?q=Check_LAS_intensity_range)** — Should match sensor characteristics.
- **[Check GPS time continuity](ca://s?q=Check_LAS_GPS_time_continuity)** — Look for jumps or resets indicating flightline issues.
- **[Check scan angle range](ca://s?q=Check_LAS_scan_angle_range)** — Should fall within sensor limits (e.g., ±30° or ±45°).

---

## 6. File Structure & Consistency Checks
- **[Check file signature](ca://s?q=Check_LAS_file_signature)** — Must be `"LASF"`.
- **[Check header size](ca://s?q=Check_LAS_header_size)** — Must match LAS version.
- **[Check point data offset](ca://s?q=Check_LAS_point_data_offset)** — Must align with end of header + VLRs.
- **[Check for truncated file](ca://s?q=Check_LAS_truncated_file)** — Compare expected vs actual file size.
- **[Check compression integrity](ca://s?q=Check_LAS_compression_integrity)** — LAZ must decompress without errors.

---

## 7. Spatial Consistency Checks
- **[Check tile boundaries](ca://s?q=Check_LAS_tile_boundaries)** — Ensure points fall within expected tile extents.
- **[Check for duplicate points](ca://s?q=Check_LAS_duplicate_points)** — Common in merged datasets.
- **[Check for empty tiles](ca://s?q=Check_LAS_empty_tiles)** — Indicates tiling or filtering errors.
- **[Check for outliers](ca://s?q=Check_LAS_outlier_points)** — Extreme Z or isolated points often indicate sensor noise or corruption.

---

## 8. Metadata & Provenance Checks
- **[Check generating software](ca://s?q=Check_LAS_generating_software)** — Should match vendor or processing pipeline.
- **[Check system identifier](ca://s?q=Check_LAS_system_identifier)** — Identifies sensor or processing system.
- **[Check project metadata](ca://s?q=Check_LAS_project_metadata)** — Acquisition date, flightline ID, etc.
- **[Check for missing documentation](ca://s?q=Check_LAS_missing_documentation)** — CRS, vertical datum, and units must be documented externally.