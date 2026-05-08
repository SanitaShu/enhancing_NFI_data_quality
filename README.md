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

## Research Objectives

The main objective of this project was to develop an inventory-oriented approach for improving forest inventory data quality using supervised machine learning and Sentinel-1/2 data.

Specific objectives included:

1. Analysing factors affecting the quality and consistency of inventory data
2. Extracting spectral and SAR predictors from Sentinel imagery
3. Developing supervised ML models for forest attribute estimation and classification
4. Evaluating prediction errors and residual patterns
5. Identifying high-deviation stands as potential indicators of inventory inconsistencies

---

# Repository Structure

## `/data`

Contains processed datasets used for machine learning analysis.

### Files

* `inventory_data.csv` – cleaned and harmonised forest inventory dataset
* `sentinel_features.csv` – Sentinel-1 and Sentinel-2 predictors extracted in Google Earth Engine
* `merged_dataset.csv` – final dataset used for modelling

---

## `/gee_scripts`

Google Earth Engine JavaScript scripts used for satellite data preprocessing and feature extraction.

### Files

* `sentinel_feature_extraction.js` – extraction of Sentinel-1 and Sentinel-2 predictors
* `visualisation_export.js` – export of RGB satellite images and polygon overlays

Main processing steps:

* cloud masking
* summer composite generation
* vegetation index calculation
* SAR metric generation
* polygon-level aggregation using `reduceRegions()`

---

## `/notebooks`

Jupyter notebooks used for data analysis and modelling.

### Files

* `01_data_preprocessing.ipynb` – data cleaning and preprocessing
* `02_feature_analysis.ipynb` – exploratory analysis and correlation filtering
* `03_regression_models.ipynb` – GSV and height modelling
* `04_classification_models.ipynb` – species and age-class classification
* `05_residual_analysis.ipynb` – residual analysis and identification of high-deviation stands

---

## `/models`

Saved machine learning models.

### Files

* `rf_gsv_model.joblib`
* `rf_height_model.joblib`
* `rf_species_model.joblib`
* `rf_ageclass_model.joblib`
* `gb_models/`

---

## `/figures`

Contains figures used in the thesis and presentation.

### Includes

* feature importance plots
* scatter plots
* confusion matrices
* residual distributions
* high-deviation stand examples
* workflow diagrams

---

## `/results`

Model evaluation outputs and summary tables.

### Includes

* regression metrics
* classification metrics
* confusion matrices
* residual statistics
* high-deviation stand analysis

---

## `/thesis`

Master’s thesis document and presentation materials.

### Files

* `master_thesis.pdf`
* `conference_presentation.pdf`
* `appendices.pdf`

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

# Main Findings

* Moderate predictive performance was achieved for GSV and stand height estimation
* Age-class classification performed better than dominant species classification
* Optical Sentinel-2 predictors were generally more important than SAR variables
* Smaller and older stands showed larger prediction residuals
* High-deviation residuals helped identify potentially inconsistent inventory records

The results demonstrate that machine learning and Sentinel data can support not only forest attribute estimation, but also forest inventory quality assessment.

---

# Tools and Technologies

* Python
* Google Earth Engine
* scikit-learn
* pandas
* geopandas
* rasterio
* matplotlib
* QGIS

---

# Author

Sanita Ma

Master’s thesis developed at:

* Transport and Telecommunication Institute (TSI)
* University of the West of England (UWE)

Supervisor:
Professor Dr.sc.ing. Irina Jackiva (Yatskiv)

---

# License

This repository is provided for academic and research purposes.
