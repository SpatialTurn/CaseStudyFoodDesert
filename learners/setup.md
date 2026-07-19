---
title: Setup
---

This lesson is designed to run in **Google Colab**, a free service that runs Jupyter notebooks in your browser. Nothing needs to be installed on your computer, and every dataset used in the lesson is fetched automatically by the notebooks themselves.

## Data Sets

There is nothing to download before class. Both notebooks read their data directly from the source URLs while they run:

- Census tract boundaries (TIGER/Line shapefiles) are read straight from the U.S. Census Bureau.
- The USDA Food Access Research Atlas spreadsheet is read straight from the USDA ERS website.
- The Expert notebook additionally fetches data live from the Census API and OpenStreetMap.

The only thing you need is a stable internet connection. The USDA spreadsheet is large, so the cell that reads it can take a couple of minutes on slower connections. This is normal.

The Expert notebook uses a free Census API key. A shared key is included in the notebook, but if you plan to use it heavily you should request your own (it takes one minute) at https://api.census.gov/data/key_signup.html

## Software Setup

::::::::::::::::::::::::::::::::::::::: discussion

### Details

The recommended way to follow this lesson is Google Colab, which requires only a web browser and a Google account. If you prefer working on your own machine, a local Jupyter installation works too. Instructions for both are in the dropdowns below. Later modules in this curriculum may use desktop GIS software such as QGIS or ArcGIS; setup instructions for those tools will be added here when those modules are released.

:::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::: spoiler

### Google Colab (recommended)

1. Make sure you are signed in to a Google account.
2. Click one of the notebook links on the lesson page (for example the Beginner notebook). It opens directly in Colab from GitHub.
3. Colab opens the notebook in read-only mode. To run and edit it, save your own copy first: **File, then Save a copy in Drive**. Your copy lives in your Google Drive and keeps any changes you make.
4. Run cells one at a time with **Shift + Enter**, or run everything with **Runtime, then Run all**.
5. The first time you run a notebook, Colab may show a warning that the notebook was not authored by Google. Click **Run anyway**.
6. All required Python libraries (pandas, geopandas, matplotlib) come pre-installed on Colab. If a notebook ever needs an extra package, the install command is included in the notebook itself.
7. Colab disconnects idle sessions after a while. If that happens, reconnect and rerun the cells from the top. Files created during a session (like saved GeoPackages) disappear when the session ends, so download anything you want to keep via the file browser in the left sidebar.

::::::::::::::::::::::::

:::::::::::::::: spoiler

### Local Jupyter installation (alternative)

If you would rather run the notebooks on your own computer:

1. Install Python 3.10 or newer, ideally through Miniconda or Anaconda.
2. Install the required libraries:

```bash
pip install jupyterlab pandas geopandas matplotlib openpyxl scipy requests
```

3. Download the notebooks from the lesson's GitHub repository.
4. Start JupyterLab with `jupyter lab`, open a notebook, and run cells with **Shift + Enter**.

::::::::::::::::::::::::

:::::::::::::::: spoiler

### GIS desktop software (coming later)

Some later modules will use desktop GIS applications such as QGIS or ArcGIS Pro, and data portals such as USGS EarthExplorer. You do not need any of these for the Food Desert lesson. Setup instructions will be added to this page when those modules are published.

::::::::::::::::::::::::
