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

The Expert notebook needs a free **Census API key**, and every learner needs their own. The Census API refuses any request without a key.

1. Request a key at <https://api.census.gov/data/key_signup.html>. It arrives by email within a few minutes.
2. Click the activation link in that email. The key does not work until you do.
3. In the Expert notebook, paste the key between the quotes in `API_KEY = ""` in the setup section.

Treat the key like a password: do not post it online or leave it in a notebook you share.

## Software Setup

::::::::::::::::::::::::::::::::::::::: discussion

### Details

The recommended way to follow this lesson is Google Colab, which requires only a web browser and a Google account. If you prefer working on your own machine, a local Jupyter installation works too. Instructions for both are in the dropdowns below.

:::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::: spoiler

### Google Colab (recommended)

1. Make sure you are signed in to a Google account.
2. Click one of the notebook links on the lesson page (for example the Beginner notebook). It opens directly in Colab from GitHub.
3. Colab opens the notebook in read-only mode. To run and edit it, save your own copy first: **File > Save a copy in Drive**. Your copy lives in your Google Drive and keeps any changes you make.
4. Run cells one at a time with **Shift + Enter**, or run everything with **Runtime > Run all**.
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

3. Download the two notebooks from the `Census` folder of the [DataCollection-Notebooks repository](https://github.com/SpatialTurn/DataCollection-Notebooks/tree/main/Census).
4. Start JupyterLab with `jupyter lab`, open a notebook, and run cells with **Shift + Enter**.

::::::::::::::::::::::::
