# 20357382-Geospatial-Analysis

LS-LRSI Landslide Risk Assessment Workflow

1. Project Overview
This project implements a Python/Jupyter Notebook workflow for a prototype Landslide Risk-Specific Index (LS-LRSI) for Badulla District, Sri Lanka.

The workflow is divided into two notebooks:
1. `Setup and Dataset.ipynb` – creates the project directory structure, documents/downloads the required spatial datasets, inspects datasets, prepares the Badulla administrative boundary, and retrieves the SoilGrids layer.
2. `LS-LRSI.ipynb` – performs exploratory data analysis (EDA), indicator normalization, expert-weighted Hazard/Exposure/Vulnerability index construction, final LS-LRSI calculation, risk classification, sensitivity analysis, validation, and output generation.

Important: The current `LS-LRSI.ipynb` contains a prototype/demo implementation in which several environmental, exposure, and vulnerability arrays are generated synthetically with NumPy. Therefore, the numerical EDA, risk percentages, and validation metrics produced by that notebook demonstrate the implementation and behavior of the indexing algorithm; they should not be interpreted as independently validated measurements of actual Badulla District risk.

2. System Requirements
Recommended environment:
- Anaconda or Miniconda
- Python 3.11+ (the supplied notebook was saved with a Python 3.13 kernel)
- Jupyter Notebook
- Internet connection for external dataset downloads
A Conda environment is recommended for geospatial packages such as `rasterio` and `geopandas`.


3. Project Structure
LS-LRSI-Project/
│
├── Setup and Dataset.ipynb
├── LS-LRSI.ipynb
│
└── LS_LRSI_Data/
    ├── DEM/
    ├── Rainfall/
    ├── Sentinel2/
    ├── Admin/
    ├── Landslide/
    ├── Soil/
    ├── OSM/
    ├── Processed/
    └── Output/


4. Required Datasets
|SRTM DEM | Elevation and terrain derivatives | `LS_LRSI_Data/DEM/srtm_badulla.tif` |
| CHIRPS rainfall | Rainfall indicator | `LS_LRSI_Data/Rainfall/` |
| Administrative boundary | Badulla study boundary | `LS_LRSI_Data/Admin/badulla_boundaries.shp` |
| OpenStreetMap | Roads/settlements/exposure | `LS_LRSI_Data/OSM/sri-lanka-latest.osm.pbf` |
| SoilGrids | Soil indicator | `LS_LRSI_Data/Soil/soilgrids_lka.tif` |
| Sentinel-2 | NDVI/imagery; real-data input planned | `LS_LRSI_Data/Sentinel2/` |
| Landslide inventory | Landslide observations/validation; real-data input planned | `LS_LRSI_Data/Landslide/` |


6. End-to-End Execution
Step 1 – Place both notebooks in one folder
  LS-LRSI-Project\
    Setup and Dataset.ipynb
    LS-LRSI.ipynb
Open Jupyter from this folder.

Step 2 – Run `Setup and Dataset.ipynb`
  Run all cells **from top to bottom**.
  The notebook creates the required directory structure and provides dataset download instructions.

Step 3 – Provide/download the input datasets
  Place datasets in the expected folders.

Step 4 – Verify CHIRPS

Step 5 – Prepare the Badulla boundary
  The notebook retrieves Sri Lankan administrative boundaries and identifies Badulla among the 25 districts.

Step 6 – Run SoilGrids extraction
  The notebook transforms the boundary to EPSG:4326:

7. Run `LS-LRSI.ipynb`
  After completing the setup notebook, open: `LS-LRSI.ipynb`

  Run all cells from top to bottom.
  The processing sequence is:
  Data Loading
      ↓
      EDA
      ↓
  Indicator Preparation
      ↓
  Normalization
      ↓
  Expert Weighting
      ↓
  Hazard Index
      ↓
  Exposure Index
      ↓
  Vulnerability Index
      ↓
  LS-LRSI
      ↓
  Risk Classification
      ↓
  Sensitivity Analysis
      ↓
  Validation
      ↓
  Output Files


8. Generated Outputs
  The main output directory is: `LS_LRSI_Data/Output/`

  Expected files include:
  `summary_statistics.csv
  ls_lrsi_components_map.png
  weight_sensitivity.csv
  performance_metrics.csv
  interpretation_recommendations.txt`


  
