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
