---
title: "Food Desert"
teaching: 100
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a food desert?
- Where can we find data on food deserts in the U.S.?
- How can you visualize the food desert data for your region of interest?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Provide an overview of the Food Access Research Atlas data from the USDA
- Explain how to download and visualize data from the USDA

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- The Food Access Research Atlas data can be used to study food access in terms of socioeconomic factors
- It can be used for site selection for new grocery stores
- Public policy analysis
- Spatial analysis of public transportation networks
- Beginner, Intermediate, Expert Modules

::::::::::::::::::::::::::::::::::::::::::::::::

## What are we working with?

#### TIGER Shape File
A TIGER/Line Shapefile is a digital file format used by the U.S. Census Bureau to represent geographic and cartographic information. These files contain data about various geographic features such as roads, rivers, railways, boundaries, and are used for performing spatial analysis. They are free to download from the U.S. Census Bureau website which makes them a valuable resource for researchers, planners, and anyone interested in the field of geospatial analysis. This data comes by state.

#### Food Desert Data
This data consists of information regarding the accessibility of affordable and nutritious food, and demographics of people living in an area. These areas are categorized by the presence of supermarkets and grocery stores in the area. It considers multiple other factors like income that could potentially affect the accessibility of food to people living in an area. The latest data is from 2019, and it comes for all the states/counties in the USA, ideally, we would want to minimize our analysis area to maximize the quality of the result.

### Overview
This Python notebook provides a comprehensive guide for analyzing food deserts in the United States with a specific focus on Indiana as an example. The notebook is designed to be robust, i.e., it can be used to perform the food desert analysis on any state. The tutorial demonstrates how to collect, merge, and visualize geospatial data to identify low-income and low-access areas with limited access to food resources.

## Objectives
- Data Collection: Retrieve and process TIGER shapefiles and USDA food desert datasets.
- Data Merging: Combine geospatial shape file and food desert data for analysis.
- Visualization: Create maps to highlight low-income and low access census tracts within Indiana.
- Flexibility: Enable analysis for any U.S. state by adjusting input parameters.

### The Setup
Importing essential Python libraries for data manipulation and visualization:
- pandas: For handling tabular data (e.g., Excel, text files).
- geopandas: For working with geospatial data (e.g., shapefiles).
- matplotlib.pyplot: For generating plots and maps.
- requests, zipfile, os, shutil: For downloading and managing files.

### Data Processing
- Download and extract TIGER shapefiles for the specified state (Indiana in this case).
- Load USDA food desert data into a pandas DataFrame.
- Merge the geospatial TIGER data with the USDA Food desert data based on census tract identifiers.
- GEOID and Census Tract are used as the common fields to perform this join.
- The values for both these columns are first converted to the same data type (either strings or integer) and then the merging is performed.

### Visualization
Explore the metadata for the USDA Food Desert Excel file to understand what each column means. The ones that we are interested in plotting would LILATracts (Low Income & Low Access) and Low Income. The columns only contain 0s and 1s which indicate whether the tract is Low Income or Low Access. 1 indicates "Yes" and 0 indicates "No". For a more detailed analysis, you can plot a smaller area like for our case we chose Marion County. After merging the two datasets, a subset can be taken based on the County code which can be found here. Low Income Marion County Indiana 2019: Low Income Tracts in Marion County, Indiana. Green Indicates regions of Low Income.

## Module Overview

| Lesson            | Overview                                                                                                   |
|-------------------|------------------------------------------------------------------------------------------------------------|
| <a href="https://colab.research.google.com/github/SpatialTurn/DataCollection-Notebooks/blob/main/Census/TIGER_FoodDesert_Tutorial.ipynb" target="_blank">Beginner</a> | Learn how to visualize and work with tabular data downloaded from the USDA Food Access Research Atlas. |
| [Intermediate]()  | (To be added)                                                                                              |
| <a href="https://colab.research.google.com/github/SpatialTurn/DataCollection-Notebooks/blob/main/Census/Expert/Grided_LILA_Analysis_Comparison.ipynb" target="_blank">Expert</a> | Uses all the taught basic tutorials to perform a full spatial and network analysis of food deserts in Indiana. |