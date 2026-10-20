---
title: "Park Access in Lafayette (Python)"
teaching: 15
exercises: 60
---

:::::::::::::::::::::::::::::::::::::: questions

- What share of residents, children and car-free households can walk to a public park in Lafayette and West
  Lafayette?
- Which neighborhoods have the least access?
- How much do the analyst's decisions change the answer?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Turn a policy standard (the 10-minute walk) into a measurable definition of access
- Decide which features count as parks, and document the decision
- Estimate access for several population groups with buffers and areal weighting in GeoPandas
- Run a sensitivity analysis and state the limitations of a buffer-based measure

::::::::::::::::::::::::::::::::::::::::::::::::

## Why parks, and why walking distance?

Parks are linked to physical activity, mental health, cooler neighborhoods in heat waves and social contact. What
matters for everyday use is **proximity**: many park visits, especially by children and older adults, are on foot, and
households without a car cannot easily reach a park across town. Many cities therefore adopt a **10-minute walk**
standard: every resident within about a half mile (**800 m**) of a park, the benchmark used by the Trust for
Public Land's ParkScore and by city park plans.

This case study asks, for Lafayette and West Lafayette, Indiana:

1. What share of residents lives within 800 m of a public park?
2. Are **children** and **households without a car** as well served as everyone else?
3. Which neighborhoods have the least access?

It is an **intermediate** case study: it uses only the tools of the Geoprocessing episodes (buffer, dissolve,
clip, intersect, areal weighting) and the Foundations episodes on tables and joins. The new work is in the
**decisions**, and in showing how much the answer depends on them.

## Decisions that shape the answer

| Decision | Choice here | Alternatives |
|---|---|---|
| What counts as a park | OpenStreetMap features tagged `leisure=park`, **minus** 13 that are not public recreational parks: campus malls and plazas, intramural fields, a scout camp, a shrine, an apartment dog park and Wolf Park (admission) | All OSM parks; the cities' official park lists; only parks over a minimum size |
| How far is close | **800 m** straight line from the park **edge** | 400 m (5 minutes); network distance along walkable streets; distance to entrances |
| Where people live | Census tracts, with **areal weighting** inside each tract | Block groups or blocks; dasymetric estimation with land cover |
| Who counts | Residents, children (under 18), households without a car | Older adults, low-income households |

Every row is a judgment call. Write each one down with its reason, and test the ones that might change the
answer (a **sensitivity analysis**).

## What the analysis finds

- About **71%** of residents in the two cities live within 800 m of a public park, but only about **63%** of
  **children**, while **78%** of households without a car do.
- Access is lowest in **Census Tracts 17.01 (east-central Lafayette) and 15.01 (southwest Lafayette)**, home to
  more than 8,000 people with median incomes well below the county's typical level, where almost no one lives
  within 800 m of a public park.
- Across income thirds there is **no simple gradient** (about 67%, 72% and 64% from lowest to highest income).
- Dropping the 13 non-park features barely changes the result, but the **distance** does: at 400 m only about
  41% of residents and 34% of children are served.

## Limitations

- **Straight lines** ignore barriers: the Wabash River, railroads and highways. Network distance (Data Analysis
  module, Network Analysis; Case Studies, Grocery Access Part 2) is more realistic.
- **Edges, not entrances**, and **all parks count the same**, whatever their size or facilities.
- **Areal weighting** spreads people evenly within tracts.
- **OpenStreetMap completeness**: a park missing from OSM looks like a gap in access. Check low-access tracts
  against official park lists, imagery or a site visit before recommending anything.

::::::::::::::::::::::::::::::::::::: callout

## Before you start

You should be comfortable with the Data Analysis module's
[Geoprocessing in Python](https://spatialturn.github.io/DataAnalysis/geoprocessing-python.html) episode (notebooks
01a to 01c). The [QGIS version](park-access-qgis.md) of this case study uses the same data and reaches the same
numbers.

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Which decision matters most?

Look at the sensitivity table in the notebook. Which decision changes the result most: the list of parks, or the
distance? What would you report to a city council?

:::::::::::::::: solution

The **distance**: moving from 800 m to 400 m drops the share of residents served from about 71% to about 41%,
while removing the 13 non-park features changes it by less than one point. Report the 800 m result as the main
figure (it matches the policy standard), state the 400 m result alongside it, and name the neighborhoods with
the lowest access, since those findings hold under every choice.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Why might children have less access?

Children are less well served than residents overall. Suggest two explanations you could check with the data in
this case study.

:::::::::::::::: solution

Possible explanations: (1) families with children live disproportionately in **newer subdivisions on the city
edges**, farther from the older parks near the center; check by mapping `pop_under18` as a share of residents
against access. (2) Areas with many residents but few children, such as **campus and downtown**, are close to
parks and raise the overall residents' figure; check by comparing access in tracts with high and low shares of
children. Both are about **where** groups live, which is what an access measure captures.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- An access measure is a chain of decisions: what counts as a facility, how far is close, where people live
- Buffer from facility edges, dissolve, intersect with tracts and areal-weight each group's counts
- Report results for groups and places, not only one city-wide number
- A sensitivity analysis shows which decisions matter; state limitations plainly

::::::::::::::::::::::::::::::::::::::::::::::::

## Notebook

| Notebook | What you will do |
|---|---|
| <a href="https://colab.research.google.com/github/SpatialTurn/CaseStudies/blob/main/notebooks/Park_Access_Lafayette.ipynb" target="_blank">Park Access in Lafayette</a> | Define public parks, build the 10-minute walk zone, estimate access for residents, children and car-free households, find the least-served tracts, compare income groups and run a sensitivity table |
