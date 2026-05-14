# Trunk ID Algorithm:
- Clip point cloud
- Load point cloud
- Keep only unclassified or related vegetation parameter
- define point cloud bounds
    - clound_min_x,cloud_min_y, cloud_max_x, cloud_max_y

- define resolution
    - match resolution of orthophoto
    - statistical?
    - parameter?
    - limited by compute time
    - box_size = 1

- result_raster - create 2D raster same size and resolution of ortho 

ortho = .3 m
NPS = .5 m
typical trunk size 1.5 m to 2.5 m

- first Loop:
    - for each block in result_raster
        - create bounding box size of raster
        - points_in_block - list to store pointids falling within bounding box
        - store points_in_block in result raster

total_points into result raster

int tree_ids

- for each 3 x 3 convolution
    - if current center > mean total points? upper 25th percentile?
        - compare current center to neighbors
            - check neighbors tree_id
            - if exists, set current center to existing tree_id
            - if no tree_id, create new tree_id at center
    - for each pointid in points_in_block 
        - set classification flag to trunk
        - assign treeID




import pandas
import laspy
## import raster
from osgeo import gdal, osr

# Load the LAS/LAZ file
las = laspy.read("data/clipped_point_cloud.las")

# Build a DataFrame with only the fields you want
cloud = pd.DataFrame({
    "x": las.x,
    "y": las.y,
    "z": las.z,
    "classification": las.classification
    "keypoint": las.keypoint_flag
})

ds = gdal.Open("data/clipped_ortho.tif")

## function to get basic raster information
gt = ds.GetGeoTransform()

x_min = gt[0]          # upper-left X
d     = gt[1]          # pixel width
y_max = gt[3]          # upper-left Y
pixel_height = gt[5]   # negative

cols = ds.RasterXSize    # number of columns
ny = ds.RasterYSize    # number of rows

x_max = x_min + nx * d
y_min = y_max + ny * pixel_height   # pixel_height is negative

# 1. Compute raster cell indices for ALL points (vectorized)

# Column index (how far right the point is)
i = ((cloud.x - x_min) / d).astype(int)

# Row index (how far down the point is — note the Y flip)
j = ((y_max - cloud.y) / d).astype(int)


# 2. Keep only points that fall inside the raster extent

valid = (
    (i >= 0) & (i < cols) &
    (j >= 0) & (j < rows)
)

# Filter indices and point objects
i_valid = i[valid]
j_valid = j[valid]
points_valid = cloud[valid]   # actual point references


# 3. (Optional) Build a density raster for visualization

density = np.zeros((rows, cols), dtype=int)

# Increment the count for each valid point's cell
np.add.at(density, (j_valid, i_valid), 1)

# 4. Store ACTUAL point objects into bins

# Loop over the filtered points and place each one
# into its corresponding raster cell.
for idx in range(len(points_valid)):
    row = j_valid[idx]
    col = i_valid[idx]
    bins[row][col].append(points_valid[idx])


############# Output Density Raster #################

# Create a new GeoTIFF with the same spatial reference


driver = gdal.GetDriverByName("GTiff")
out_ds = driver.Create(
    "density.tif",
    cols,          # width
    rows,          # height
    1,             # number of bands
    gdal.GDT_Int32 # data type
)

# Apply the same geotransform as the orthophoto
out_ds.SetGeoTransform(gt)

# Apply the same projection as the orthophoto
out_ds.SetProjection(ds.GetProjection())


# Write the density raster to band 1


out_band = out_ds.GetRasterBand(1)
out_band.WriteArray(density)

# Optional: set NoData value
out_band.SetNoDataValue(-9999)

# Flush to disk
out_band.FlushCache()
out_ds = None

