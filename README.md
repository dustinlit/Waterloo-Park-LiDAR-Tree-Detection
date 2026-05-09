# Waterloo-Park-LiDAR-Tree-Detection
An exploration of machine learning techniques to detect and quantify individual trees in Waterloo Park in Lebanon, Oregon.


## Data
WaterLoo Park Lidar: https://www.fisheries.noaa.gov/inport/item/74249
## LiDAR Metadata Summary (USGS Contract 140G0221D0012, NV5 Geospatial)

### Acquisition
- **Contractor:** NV5 Geospatial  
- **Sensors:** Riegl VQ‑880GII‑IR (topographic), Riegl VQ‑880G‑Green (bathymetric)  
- **Spec:** USGS Lidar Base Specification 2022 (Rev A)  
- **Max returns:** 15  
- **Vertical datum:** GEOID18  

### Point Density
**Topographic IR**
- Nominal NPS: 0.35 m  
- Nominal density: 8 pts/m²  
- Achieved NPS: 0.18 m  
- Achieved density: ~30 pts/m²  

**Bathymetric Green**
- Nominal NPS: 0.50 m  
- Nominal density: 4 pts/m²  
- Achieved density: ~18 pts/m²  

### Flight Parameters
- Altitude: 400–1100 m AGL  
- Speed: 130–145 knots  
- Scan angle: 40–42°  
- Swath width: 291–845 m  
- Overlap: 60–70%  

### LAS Structure
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

### Point Attributes
- 14 core LAS 1.4 PF6 fields  
- + Extra Bytes (bathy + QC)  
- Total: ~26–32 attributes per point

## NAIP Orthoimagery Metadata Summary (USDA / USGS EROS, 2022)

### Acquisition
- **Program:** National Agriculture Imagery Program (NAIP)
- **Agency:** U.S. Department of Agriculture (USDA)
- **Distributor:** USGS EROS Center
- **Acquisition date:** 2022‑06‑24
- **Product type:** 4‑band orthoimagery (CIR/true color)
- **Format:** Raster (JPEG2)
- **DOI:** https://doi.org/10.5066/F7QN651G

### Purpose
- Annual agricultural‑season aerial imagery for public and government use.
- Supports land management, vegetation mapping, and general geospatial analysis.

### Spatial Coverage
- **Location:** United States (tile centered near 44.4357° N, –122.8777° W)
- **Tile ID:** M_4412234_NW_10_030_20220624

### Data Quality
- Radiometry visually inspected.
- Minor tonal differences may occur between adjacent tiles.
- NAIP imagery accepted by APFO before USGS distribution.

### Access & Use
- **Use constraints:** None (public domain).
- **Accuracy disclaimer:** Not guaranteed for critical applications.
- **Download:** USGS EarthExplorer (https://earthexplorer.usgs.gov)

### Contact
- **USGS EROS Customer Service**
  - custserv@usgs.gov
  - 605‑594‑6151
  - Sioux Falls, SD

### Lineage
- Source: USDA aerial photography (2022‑06‑24)
- Processing & distribution by USGS EROS


