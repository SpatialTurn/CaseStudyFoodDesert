---
title: "Case Study: Food Deserts"
teaching: 45
exercises: 60
---

:::::::::::::::::::::::::::::::::::::: questions

- What is a food desert, and how does the USDA formally define one?
- Where can we find data on food deserts in the U.S., and how has that data changed?
- How can you visualize and reproduce the food desert analysis for your region of interest?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain the concept and history of food deserts and the USDA's Low Income, Low Access (LILA) framework
- Provide an overview of the Food Access Research Atlas data from the USDA
- Visualize official food desert designations for any U.S. state (Beginner notebook)
- Reproduce the USDA methodology from raw open data and validate it against the official Atlas (Expert notebook)

::::::::::::::::::::::::::::::::::::::::::::::::

## What is a Food Desert?

A food desert is an area where residents have limited access to affordable and nutritious food, most often because they live far from a supermarket and lack the income or transportation to overcome that distance. The term is thought to have originated in Scotland in the early 1990s, where it described public housing estates left without grocery stores, and it entered mainstream U.S. policy during the 2000s as researchers connected neighborhood food environments to diet quality and health outcomes.

Distance alone does not make a food desert. A wealthy suburb ten miles from a supermarket is not one, because its residents can drive there without difficulty. Food deserts emerge from the combination of two conditions:

1. **Low income**: many residents cannot afford to travel far for groceries or to pay higher prices at small convenience stores.
2. **Low access**: the nearest supermarket, supercenter, or large grocery store is far away by neighborhood standards.

This pairing is why the USDA's formal term is **LILA**: Low Income, Low Access. Throughout this lesson "food desert" and "LILA tract" mean the same thing.

## How the USDA Measures It

In the 2008 Farm Bill, Congress directed the USDA to study food access nationwide. The USDA's Economic Research Service (ERS) released the Food Desert Locator in 2011, which became the **Food Access Research Atlas** in 2013. The Atlas was updated with data for 2015 (released in 2017) and 2019 (released in 2021). In July 2026 the ERS renamed that atlas the **Large Retailer Access Map** and added a second map built on newer data (see "The 2026 update" below). The rest of this section describes the original method, which is the one the notebooks in this lesson use.

The Atlas works at the level of the **census tract**, a statistical neighborhood of roughly 4,000 people. Each tract is evaluated on both conditions:

**Low income** follows the Treasury Department's New Markets Tax Credit rule. A tract qualifies if its poverty rate is at least 20 percent, or its median family income is at or below 80 percent of the statewide median, or, for tracts inside a metropolitan area, at or below 80 percent of the metro area median.

**Low access** is measured by distance to the nearest supermarket, supercenter or large grocery store. Convenience stores, dollar stores, drug stores and warehouse clubs do not count, because they rarely stock a full range of fresh food. The USDA overlays the country with a grid of half kilometer cells, estimates the population of each cell, and measures the straight line distance from each cell to the nearest store. A tract is low access if at least 500 people, or at least a third of the population, live beyond a distance threshold. Because "far" means something different in a city than in the countryside, the threshold depends on whether the tract is urban or rural. The Atlas publishes several combinations rather than one official answer:

| Measure | Urban threshold | Rural threshold |
|---|---|---|
| Standard | 1 mile | 10 miles |
| Strict urban | half a mile | 10 miles |
| Strict rural | 1 mile | 20 miles |
| Vehicle based | at least 100 households with no vehicle live more than half a mile away | at least 500 people, or a third of residents, live more than 20 miles away |

The vehicle measure captures an important nuance: a mile is trivial by car and a serious barrier on foot with grocery bags, so households without vehicles face low access at much shorter distances.

These definitions have limitations worth keeping in mind. Straight line distance ignores rivers, highways, and transit routes (the [grocery access case study](grocery-network.md) in this module shows how much longer real routes can be). The store list counts supermarkets but says nothing about prices or food quality, and some researchers argue the bigger problem in many neighborhoods is a "food swamp", an abundance of fast food and convenience stores rather than an absence of anything. Treating the Atlas as a starting point for questions, not a final verdict, is good practice.

## The 2026 update: two maps

In July 2026 the ERS reorganized the Food Access Research Atlas into two maps:

| | Large Retailer Access Map (LRAM) | SNAP-Authorized Retailer Access Map (SRAM) |
|---|---|---|
| What it is | The original Atlas, renamed | A new map, first released in July 2026 |
| Stores counted | Supermarkets, supercenters and large grocery stores | All brick-and-mortar stores authorized to accept SNAP benefits (excluding farmers markets and delivery routes) |
| Store data | 2019 | 2025 |
| Census tracts | 2010 boundaries | 2020 boundaries |
| Distance | Straight line | Straight line, plus driving distance along the road network |
| Next update | Expected winter 2026 to 2027 | Updated as needed |

Because the SRAM counts every SNAP-authorized store, including many smaller shops, it answers a different question from the LRAM: access to *any* store that accepts SNAP, rather than access to a large, full-service store. The two maps are not directly comparable, so always say which one you use. The notebooks in this lesson use the 2019 LRAM data, which is still the ERS's measure of access to large food retailers.

## The Data We Work With

#### TIGER Shapefiles

A TIGER/Line shapefile (Topologically Integrated Geographic Encoding and Referencing) is the Census Bureau's free digital format for geographic boundaries such as roads, rivers, and administrative areas. We use the census tract boundary files, published per state. A shapefile is a bundle: the `.shp` holds the geometry, the `.dbf` holds the attribute table, and the `.shx` links the two, so all three must stay together. Conveniently, geopandas can read the whole zipped bundle directly from the Census Bureau's URL, so nothing has to be downloaded by hand.

#### The Food Access Research Atlas

The Atlas is a single Excel file covering every census tract in the country. It contains three sheets: a Read Me with citation information, a Variable Lookup that serves as the metadata dictionary explaining every column, and the data sheet itself. The LILA columns contain only 0s and 1s, where 1 means the tract qualifies under that measure. The file describes the entire country, so the first step of any analysis is filtering to a state or county of interest, which also keeps maps readable.

## Learning Pathway: From Viewing the Atlas to Rebuilding It

This lesson is built around two notebooks that form a deliberate progression.

The <a href="https://colab.research.google.com/github/SpatialTurn/DataCollection-Notebooks/blob/main/Census/TIGER_FoodDesert_Tutorial.ipynb" target="_blank">**Beginner notebook**</a> works with the USDA's published answers. You read a state's tract boundaries straight from the Census Bureau, read the Atlas straight from the USDA, join the two tables on the tract identifier (`GEOID` on the Census side, `CensusTract` on the USDA side, both converted to strings before merging), and map the four LILA measures side by side. You will see how the picture of food access shifts as the definition tightens or loosens, and how to zoom in on a single county, using Marion County, Indiana as the example. Everything is parameterized by the state FIPS code, so the same notebook runs for any state.

Working with the published Atlas has two limits, and they motivate the second notebook. First, the Atlas is a finished product: you cannot ask it what happens with a different store list, a different threshold, or a different year. Second, its large-retailer data still describes 2019, and the food landscape has changed since then.

The <a href="https://colab.research.google.com/github/SpatialTurn/DataCollection-Notebooks/blob/main/Census/Food_Desert_Analysis_Automated.ipynb" target="_blank">**Expert notebook**</a> therefore rebuilds the entire analysis from raw ingredients. Income, poverty, population, and vehicle data come from the Census API, so you need your own free Census API key (see Setup). Supermarket locations come from OpenStreetMap, pinned to a chosen date so the store data matches the analysis year. The notebook constructs the same half kilometer grid the USDA uses, allocates population to it, computes distances, and applies the LILA rules exactly as defined above. Crucially, it then validates itself: it reads the official 2019 Atlas and reports, tract by tract, how closely the open data reproduction matches the USDA's own result, which relies on a commercial store list that is not public. Once validated, the same pipeline can compute food access for years the USDA never published, turning a static 2019 snapshot into an instrument for studying change over time.

Complete the Beginner notebook first. The concepts it introduces, tracts, joins, LILA flags, and choropleth maps, are exactly the vocabulary the Expert notebook builds on.

::::::::::::::::::::::::::::::::::::: challenge

## Which definition?

A city council asks you to map food deserts so it can decide where to fund a new grocery store. Many residents of one neighborhood are older adults without cars, and the nearest supermarket is 0.8 miles away. Which LILA measure would flag this neighborhood, and which would miss it?

:::::::::::::::: solution

The **standard** measure (1 mile in urban areas) would miss it, because 0.8 miles is under the threshold. The **strict urban** measure (half a mile) would flag it if enough residents live beyond half a mile. The **vehicle based** measure would flag it if at least 100 households without a vehicle live more than half a mile from the store. The choice of measure is a policy decision as much as a technical one, which is why the Atlas publishes several.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Explore your own state

Run the Beginner notebook for your home state (or Indiana) by changing the state FIPS code. Which of the four LILA measures flags the most tracts, and which the fewest? Why?

:::::::::::::::: solution

Some answers follow from the definitions. The **strict urban** measure (half a mile and 10 miles) can never flag fewer tracts than the **standard** measure (1 mile and 10 miles), because its urban bar for "far" is lower, and in most states it flags the most. The **strict rural** measure (1 mile and 20 miles) can never flag more tracts than the standard one, because its rural bar is higher. The **vehicle based** measure follows its own logic, so compare it on the map: it tends to pick out city neighborhoods where many households have no car.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## What Can This Analysis Be Used For?

- **Public policy**: identifying tracts that qualify for healthy food financing programs and evaluating whether interventions changed access over time.
- **Site selection**: retailers and food banks can locate the underserved areas where a new store or distribution point would matter most.
- **Transportation planning**: overlaying LILA tracts with transit networks reveals where bus routes could connect residents to existing stores.
- **Research**: joining food access with health, environment, or demographic data supports studies of diet, equity, and urban form.

::::::::::::::::::::::::::::::::::::: keypoints

- A food desert combines two conditions: low income and low physical access to supermarkets, which the USDA formalizes as LILA tracts
- The Food Access Research Atlas publishes several distance based measures rather than one official definition, and the choice of measure changes the map
- The Atlas data supports policy analysis, site selection for new grocery stores, and spatial analysis of transportation networks
- In July 2026 the Atlas became two maps: the Large Retailer Access Map (2019 data) and the new SNAP-Authorized Retailer Access Map (2025 data, with driving distances); they measure different things
- The Beginner notebook visualizes the published 2019 Atlas for any state; the Expert notebook reproduces the methodology from open data, validates it against the Atlas, and extends it to other years

::::::::::::::::::::::::::::::::::::::::::::::::
