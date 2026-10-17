---
title: Setup
---

The **food desert** case study runs in **Google Colab**, a free service that runs Jupyter notebooks in your browser. Nothing needs to be installed on your computer, and every dataset is fetched automatically by the notebooks themselves.

The **grocery access** case study uses **QGIS**, a free desktop GIS. See [the last section](#grocery-access-case-study-qgis) of this page.

## Data Sets

There is nothing to download before class. Both food desert notebooks read their data directly from the source URLs while they run:

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

3. Download the two notebooks from the `notebooks` folder of [this lesson's repository](https://github.com/SpatialTurn/CaseStudies/tree/main/notebooks).
4. Start JupyterLab with `jupyter lab`, open a notebook, and run cells with **Shift + Enter**.

::::::::::::::::::::::::

## Grocery access case study: QGIS

**QGIS** is a free, open source Geographic Information System for viewing, analyzing and mapping spatial data.

1. Go to <https://qgis.org> and click **Download**.
2. Choose the **Long Term Release (LTR)** version, the most stable one.
   - **Windows:** the standalone installer (`.msi`)
   - **macOS:** the macOS installer (`.dmg`). The first time you open QGIS, you may need to right-click the
     app and choose **Open** to get past the security warning.
   - **Linux:** follow the instructions for your distribution on the QGIS download page
3. Run the installer and keep the default settings, then open **QGIS Desktop**.

If you are new to QGIS, the Data Visualization module's "Getting Started with QGIS" episode introduces the
interface.

### Loading the lesson data in QGIS

Part 2 reads its three data files straight from this lesson's repository, so there is nothing to download:

1. **Layer > Add Layer > Add Vector Layer**
2. **Source Type**: **Protocol: HTTP(S), cloud, etc.**
3. Paste the address given in the episode into **URI**, then click **Add**

### QField (optional)

Part 1 is a demonstration, so QField is not required. To try field data collection yourself:

1. Install **QField** from <https://qfield.org/> (Android and iOS app stores, or Windows, macOS and Linux).
2. In QGIS, install the **QFieldSync** plugin: **Plugins > Manage and Install Plugins**, search for
   QFieldSync, and click **Install Plugin**.

### Troubleshooting

| Problem | Fix |
|---|---|
| QGIS will not open on macOS | Right-click the app, choose **Open**, then confirm |
| A layer loaded from a web address shows nothing | Right-click the layer and choose **Zoom to Layer**; check that the address was pasted completely |
| Network analysis costs look tiny (such as 0.04) | Set the project coordinate system to EPSG:26916 (bottom-right corner of the QGIS window) |
