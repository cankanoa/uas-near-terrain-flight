# uas-near-terrain-flight: raster manipulation toolkit

This repository provides a Python-based toolkit for manipulating raster (DSM or DEM) data tailored for UAS flights near terrain. It enables flights extremely close to objects by providing scirpts to change the raster that drones use for terrain following. It contains a sequence of pre-processing steps: resolution adjustment, elevation buffering, and smoothing. These steps are used to prepare terrain data for advanced applications like flight planning or geospatial analysis.

This process can be effectively applied in the field as follows: An initial DSM is generated through a high-altitude flight, utilizing photogrammetry to produce an orthomosaic while capturing elevation data at a lower resolution to facilitate faster processing. The provided scripts are employed to adjust raster values, ensuring optimized terrain-following capabilities. The updated DSM serves as the basis for a subsequent low-altitude flight with enhanced terrain following, enabling the acquisition of ultra-high-resolution orthomosaics and point clouds. This methodology offers significant benefits for precise, high-resolution data collection and analysis.

## Project Structure:

1. **`_1_change_resolution.py`**
   A script to change the resolution (pixel size) of raster data while maintaining NoData values and performing maximum value resampling.

2. **`_2_buffer_elevation.py`**
   A script to elevate raster values within a defined buffer radius, preserving geometrical and topographical dependencies.

3. **`_3_smooth_elevation.py`**
   A script to smooth elevation values of DEMs using a Gaussian filter or other approaches for reducing noise or preparing surface for terrain following.

4. **`automated_script.py`**
   A master script that automates the entire workflow.

## Prerequisites:

- Python 3.6+
- Required Python libraries:
  - `numpy`
  - `rasterio`
  - `osgeo` (GDAL)
  - `scipy`

You can install the required libraries using:
```bash
pip install numpy rasterio gdal scipy
```
## Usage:

### Individual Scripts:
You can run any of the individual scripts to execute specific raster manipulations:

1. Change resolution: Configure input_path, output_path, and resolution to desired values as indicated in the script and run the scirpt.
2. Specify input raster path, output raster path, and buffer radius in meters and run the scirpt.
3. Modify input/output paths and smoothing parameters in the script and run the scirpt.

### Automated Workflow:
To process an entire workflow pipeline use this script. Each output will be saved to the output folder and be used as inputs for the next step.