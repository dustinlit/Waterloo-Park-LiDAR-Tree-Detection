### **WaterLoo Park Lidar:**
 Download: https://www.fisheries.noaa.gov/inport/item/74249
<br> 


#### Acquisition
- **Contractor:** NV5 Geospatial  
- **Sensors:** Riegl VQ‑880GII‑IR (topographic), Riegl VQ‑880G‑Green (bathymetric)  
- **Spec:** USGS Lidar Base Specification 2022 (Rev A)  
- **Max returns:** 15  
- **Vertical datum:** GEOID18  

#### Point Density
**Topographic IR**
- Nominal NPS: 0.35 m  
- Nominal density: 8 pts/m²  
- Achieved NPS: 0.18 m  
- Achieved density: ~30 pts/m²  

**Bathymetric Green**
- Nominal NPS: 0.50 m  
- Nominal density: 4 pts/m²  
- Achieved density: ~18 pts/m²  

#### Flight Parameters
- Altitude: 400–1100 m AGL  
- Speed: 130–145 knots  
- Scan angle: 40–42°  
- Swath width: 291–845 m  
- Overlap: 60–70%  

#### LAS Structure
- LAS version: 1.4  
- Point format: 6  
- Intensity: 16‑bit  
- Overlap & withheld bits used  

**Classes**
- 1 – Unclassified  
- 2 – Ground  
- 7W – Low noise  
- 9 – Water  
- 17 – Bridge decks  
- 18W – High noise  
- 20 – Ignored ground  
- 40 – Submerged topo  
- 41 – Water surface  
- 45 – Water column  

#### Point Attributes
- 14 core LAS 1.4 PF6 fields  
- + Extra Bytes (bathy + QC)  
- Total: ~26–32 attributes per point

### Bytes per point (LAS 1.4 formats)

- *[Point Format 0](ca://s?q=LAS_point_format_0_bytes)* — 20 bytes  
- *[Point Format 1](ca://s?q=LAS_point_format_1_bytes)* — 28 bytes  
- *[Point Format 2](ca://s?q=LAS_point_format_2_bytes)* — 26 bytes  
- *[Point Format 3](ca://s?q=LAS_point_format_3_bytes)* — 34 bytes  
- *[Point Format 4](ca://s?q=LAS_point_format_4_bytes)* — 57 bytes  
- *[Point Format 5](ca://s?q=LAS_point_format_5_bytes)* — 63 bytes  

### LAS 1.4 “6‑9” formats (modern)

- **[Point Format 6](ca://s?q=LAS_point_format_6_bytes)** — 30 bytes  
- *[Point Format 7](ca://s?q=LAS_point_format_7_bytes)* — 36 bytes  
- *[Point Format 8](ca://s?q=LAS_point_format_8_bytes)* — 38 bytes  
- *[Point Format 9](ca://s?q=LAS_point_format_9_bytes)* — 59 bytes  
- *[Point Format 10](ca://s?q=LAS_point_format_10_bytes)* — 67 bytes  

### `laspy.read()`

**Overview:**  
Loads a `.las` or `.laz` file and returns a `LasData` object containing all point attributes and metadata.

**Parameters:**  
- **filename** — Path to the LAS/LAZ file.  
- **closefd** — Whether to close the file descriptor after reading (default `True`).  
- **do_compress** — Rarely used; relevant mainly for writing workflows.

**Returns:**  
- **LasData** — In‑memory LiDAR dataset with coordinates, classifications, intensity, returns, header, VLRs, etc.

### `las.point_format.dimensions`

- **[X](ca://s?q=LAS_point_format_X_bytes)** — 4 bytes  
- **[Y](ca://s?q=LAS_point_format_Y_bytes)** — 4 bytes  
- **[Z](ca://s?q=LAS_point_format_Z_bytes)** — 4 bytes  
- **[Intensity](ca://s?q=LAS_point_format_intensity_bytes)** — 2 bytes (16‑bit)  
- **[Return Number + Number of Returns + Flags](ca://s?q=LAS_point_format_return_flags)** — 1 byte  
- **[Classification Flags](ca://s?q=LAS_point_format_classification_flags)** — 1 byte  
- **[Classification](ca://s?q=LAS_point_format_classification)** — 1 byte  
- **[Scan Angle](ca://s?q=LAS_point_format_scan_angle)** — 1 byte (signed)  
- **[User Data](ca://s?q=LAS_point_format_user_data)** — 1 byte  
- **[Point Source ID](ca://s?q=LAS_point_format_point_source_id)** — 2 bytes  
- **[GPS Time](ca://s?q=LAS_point_format_gps_time)** — 8 bytes  

### `las.point_format.extra_dimensions` 
function to see extra dimensions

### `las.point_format.size`
overall storage size of 1 point in bytes

## LASpy Inspection Functions & Attributes

`las.header`  
Full LAS header object (version, point format, scales, offsets, VLRs, point counts).

`las.header.version`  
LAS version number (e.g., 1.4).

`las.header.point_format`  
Point format object describing the structure of each point.

`las.header.point_count`  
Total number of points in the file.

`las.header.scales`  
Scale factors for X, Y, Z.

`las.header.offsets`  
Offset values for X, Y, Z.

`las.header.mins`  
Minimum X, Y, Z (lower bound of extent).

`las.header.maxs`  
Maximum X, Y, Z (upper bound of extent).

`las.header.vlrs`  
List of all VLRs (projection, extra bytes, waveform, metadata).

`las.header.evlrs`  
List of EVLRs (extended VLRs).

---

## Point Format & Byte Layout

`las.point_format`  
Point format object describing dimensions, sizes, and byte layout.

`las.point_format.dimensions`  
Standard dimensions (x, y, z, intensity, etc.) with type, size, offset.

`las.point_format.extra_dimensions`  
Vendor‑defined Extra Bytes (bathymetry, waveform, etc.) with metadata.

`las.point_format.dimension_names`  
Names of all dimensions (standard + extra).

`las.point_format.size`  
Total bytes per point (core + extra bytes).

---

## Point Data (Standard Dimensions)

`las.x`, `las.y`, `las.z`  
Scaled coordinates as float arrays.

`las.X`, `las.Y`, `las.Z`  
Raw integer coordinates before scale/offset.

`las.intensity`  
16‑bit intensity values.

`las.return_number`  
Return number for each point.

`las.number_of_returns`  
Total returns for the pulse.

`las.classification`  
ASPRS classification code.

`las.classification_flags`  
Bit flags (withheld, overlap, synthetic, keypoint).

`las.scan_angle`  
Signed scan angle.

`las.user_data`  
User data byte.

`las.gps_time`  
GPS timestamp (if present).

`las.red`, `las.green`, `las.blue`  
RGB color channels (if present).

---

## Extra Bytes (Vendor Fields)

`las["field_name"]`  
Access an Extra Byte dimension by name.

`las.point_format.extra_dimensions`  
Metadata for each extra field (name, type, size, offset).

---

## VLR / Metadata Inspection

`las.header.vlrs`  
List of all VLRs in the file.

`las.header.evlrs`  
List of all EVLRs.

`las.header.parse_crs()`  
Returns a CRS object if GeoTIFF projection keys exist.

---

## Utilities

`len(las.points)`  
Number of points in the file.

`las.chunk_iterator(n)`  
Iterate through points in chunks of size `n` (memory‑efficient).

`las.write("out.laz")`  
Write a LAS/LAZ file to disk.
