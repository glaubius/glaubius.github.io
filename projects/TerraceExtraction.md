## Terrace Extraction from DEM

**Project description:** Agricultural terraces are anthropogenic landscape features found in many parts of the world. As part of a project modeling the impact of terraces on landscape evolution, I needed the spatial location of terraces in Vernazza, Cinque Terre, Italy (ADD pic). I had a 1-m resolution DEM of the study area and found [instructions on how to extract terraces using ArcGIS](https://www.researchgate.net/post/How_to_detect_extract_in_GIS_field_boundaries_walls_on_the_basis_of_DEM_and_SLOPE_raster). Since I did not have access to ArcGIS, I instead extracted the terraces using open source tools, namely QGIS and a command line tool called [Centerline](https://github.com/fitodic/centerline).

### 1. Characteristics of terraces used for extraction

EDIT - Terraced landscapes are often described as "stairstep" due to the flattened treads and verical risers. <img src="images/VernazzaTerraces.jpg?raw=true"/> This characteristic morphology can be used to extract terrace walls (risers) from a DEM because the riser is located at a change in profile curvature. (ADD pic?)

### 2. Tools for terrace extraction

EDIT - I used open-source tools for the terrace wall/riser extraction, namely QGIS and a command line tool called Centerline. Within QGIS, profile curvature was calculated from the DEM using SAGA tools in the geoprocessing toolbox. (ADD pic)

### 3. Processes in terrace extraction

EDIT - The process involved:
1. smoothing the DEM
2. calculating profile curvature of smoothed DEM
3. reclassify profile curvature into high (wall/riser) and low (non-wall) classes using a threshold (ADD pic)
4. convert the classified curvature into polygons
5. clean up polygons and simplify
6. skeletonize (convert into polylines) the polygons using Centerline (ADD pic)
7. clean the polylines

### 4. Terrace extraction results
EDIT - The final product was a polyline shapefile of the terrace walls/risers. (ADD pic) I converted the shapefile into a raster in QGIS, to create the data for modeling terraces in a LEM.

For step-by-step instructions see [Terrace Extraction from DEM tutorial](/pdf/extract-terraces-DEM.pdf).
