# Enhancing Forest Inventory Data Quality Using Machine Learning

## Project Overview

This repository contains the code, data processing workflow, and supporting materials developed for the Master’s thesis:

**"Enhancing Forest Inventory Data Quality Using Machine Learning"**

The research explores how supervised machine learning and Sentinel-1/2 satellite data can be used for identifying potential inconsistencies in National Forest Inventory (NFI) records.

The study combines forest inventory data with optical and SAR satellite predictors extracted in Google Earth Engine (GEE). Random Forest (RF) and Gradient Boosting (GB) models were used for regression and classification tasks, including:

* Growing Stock Volume (GSV) estimation
* Stand height estimation
* Dominant tree species classification
* Forest age class classification

A key focus of the thesis is residual analysis and the identification of high-deviation stands that may indicate outdated or inconsistent inventory records.

The study area consists of forest stands located in Latvia.

---

## Objectives

The main objectives of this project were to:

1. Review literature on forest inventory data quality, remote sensing, and machine learning in forestry.
2. Prepare the research dataset by cleaning inventory data and extracting Sentinel-1 and Sentinel-2 predictors.
3. Apply supervised machine learning models to estimate selected forest attributes.
4. Evaluate model performance using regression and classification metrics.
5. Analyse prediction errors and residual patterns to identify potential inconsistencies in inventory records.
6. Summarise the results and assess the practical value of the approach for forest inventory data quality improvement.

---

# Repository Structure

## Data

The `data` folder contains the input files required to run the analysis in Google Colab. These files include forest inventory tables, polygon shapefiles, administrative boundary data, and selected satellite image exports used for visual inspection.

### Main data files

- `all_properties_coded.dbf`  
  Forest inventory attribute table used in the analysis. It contains coded stand-level inventory information.

- `Latvia_NFI_S2_S1_Summer_2025_merged_coded.csv`  
Sentinel-derived feature table containing predictor variables extracted for each forest stand polygon. The file includes stand identifiers and satellite-based features used for later merging with inventory data in Python.

### Forest stand polygon files

- `Nogapoly.shp`
- `Nogapoly.dbf`
- `Nogapoly.shx`
- `Nogapoly.prj`
- `Nogapoly.cpg`

These files form the forest stand polygon shapefile. The polygon boundaries were used for spatial processing, satellite feature extraction from (GEE), and linking satellite-derived values to inventory records. 

### Latvia boundary files

- `gadm41_LVA_0.shp`
- `gadm41_LVA_0.dbf`
- `gadm41_LVA_0.shx`
- `gadm41_LVA_0.prj`
- `gadm41_LVA_0.cpg`
- `gadm41_LVA_0.json`

These files contain the administrative boundary of Latvia and were used for mapping and visualisation purposes.

### Satellite image examples

Files starting with:

- `nice_satellite_image...`
- `satellite_with_polygon...`

These are exported satellite image examples used for visual inspection of selected forest stands.

The `nice_satellite_image...` files show RGB satellite images of selected areas.

The `satellite_with_polygon...` files show the same satellite images with forest stand polygon outlines added. These images were used to compare inventory records, model predictions, and satellite appearance for selected high-deviation stands.

### Important note

All shapefile components must be kept together in the same folder. For example, `Nogapoly.shp` will not work correctly without its related `.dbf`, `.shx`, `.prj`, and `.cpg` files.
---

## `Google Earth Engine Java script`

Google Earth Engine JavaScript scripts used for satellite data preprocessing and feature extraction.

Main processing steps:

* cloud masking
* summer composite generation
* vegetation index calculation
* SAR metric generation
* polygon-level aggregation using `reduceRegions()`

---

## `Code.ipynb`

Python (colab environment) notebooks used for data analysis and modelling.

## Analysis Code

The analysis was carried out in Google Colab using Python. The code includes data preprocessing, feature selection, machine learning modelling, model evaluation, and residual analysis.

If notebooks are added later, they can be placed in a separate `notebooks` folder.

## Models

Machine learning models were trained during the analysis workflow. Saved model files are not included in this repository.
---

# Methodology Summary

## Data Sources

The study used:

* National Forest Inventory (NFI) data
* Sentinel-2 optical imagery
* Sentinel-1 SAR imagery

Satellite data were processed in Google Earth Engine using summer imagery from June–August 2025.

## Feature Extraction

The following predictors were extracted:

### Sentinel-2 bands

* B2, B3, B4, B5, B6, B7, B8, B8A, B11, B12

### Vegetation indices

* NDVI
* NDRE
* NDMI
* NBR

### Sentinel-1 SAR metrics

* VV
* VH
* VV−VH
* VH/VV

Predictors were aggregated at polygon level using mean values.

## Machine Learning Models

The following supervised ML methods were used:

* Random Forest (RF)
* Gradient Boosting (GB)

Tasks included:

* regression
* classification
* residual analysis

---

# Tools and Technologies

* Python
* Google Earth Engine
* scikit-learn
* pandas
* geopandas
* rasterio
* matplotlib


---

# Author

Sanita Šulca

Master’s thesis developed at:

* Transport and Telecommunication Institute (TSI)
* University of the West of England (UWE)

Supervisor:
Professor Dr.sc.ing. Irina Jackiva (Yatskiv)

---

# License

This repository is provided for academic and research purposes ONLY.
