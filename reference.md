---
title: 'Reference'
---

## Glossary

Census tract
:   A small census area of about 1,200 to 8,000 people (4,000 on average). The unit used by the Food Access
    Research Atlas.

Coordinate reference system (CRS)
:   The system that links map coordinates to places on Earth, identified by an EPSG code such as EPSG:4326
    (latitude and longitude) or EPSG:26916 (UTM zone 16N, in meters).

Food Access Research Atlas
:   The USDA Economic Research Service's tract-level data on food access. In July 2026 it was reorganized into
    the Large Retailer Access Map and the SNAP-Authorized Retailer Access Map.

Food desert
:   An area where residents have limited access to affordable, nutritious food, usually because they have low
    income and live far from a supermarket. The USDA's formal term is a low-income, low-access (LILA) tract.

Food swamp
:   An area with many fast food and convenience outlets relative to healthy food options.

GEOID
:   A census geography's identifier. For a census tract it has 11 characters: state (2), county (3) and tract
    (6). Called `CensusTract` in the Food Access Research Atlas. Keep it as text.

Large Retailer Access Map (LRAM)
:   The original Food Access Research Atlas, renamed in July 2026. It measures distance to supermarkets,
    supercenters and large grocery stores, using 2019 store data and 2010 census tracts.

LILA (low income, low access)
:   A census tract that is both low income (by the New Markets Tax Credit rule) and low access (many residents
    live beyond a distance threshold from a large food store).

Low access
:   At least 500 people, or a third of a tract's population, live beyond a set distance from the nearest
    supermarket (for example, 1 mile in urban tracts or 10 miles in rural tracts).

Low income
:   A tract with a poverty rate of at least 20 percent, or a median family income at or below 80 percent of
    the state (or metropolitan area) median.

Network analysis
:   Analysis of movement along a network, such as roads, for example finding shortest paths or service
    areas.

New Markets Tax Credit (NMTC)
:   A U.S. Treasury program whose definition of a low-income community is used for the "low income" part of
    LILA.

OpenStreetMap
:   A free, volunteer-built map of the world. The Expert notebook uses it for supermarket locations, and the
    grocery access case study's store points come from it.

QField
:   A free, open source app for collecting field data on phones and tablets, using projects prepared in
    QGIS.

Service area
:   The part of a network that can be reached from a starting point within a given distance or time.

Shortest path
:   The route between two points along a network with the lowest total distance (or time).

SNAP
:   The Supplemental Nutrition Assistance Program, the largest U.S. food assistance program.

SNAP-Authorized Retailer Access Map (SRAM)
:   A map added to the Food Access Research Atlas in July 2026. It measures distance to any brick-and-mortar
    store authorized to accept SNAP, using 2025 store data, 2020 census tracts, and both straight-line and
    driving distance.

Urban and rural tracts
:   In the Atlas, a tract is urban if its population-weighted center lies in a Census urban area, and rural
    otherwise. Urban and rural tracts use different distance thresholds.

## Further reading

- [USDA ERS: Food Access Research Atlas](https://www.ers.usda.gov/data-products/food-access-research-atlas/)
- [USDA ERS: Food Access Research Atlas documentation](https://www.ers.usda.gov/data-products/food-access-research-atlas/documentation)
- [USDA ERS: update and revision history](https://www.ers.usda.gov/data-products/food-access-research-atlas/update-and-revision-history)
- [QField documentation](https://docs.qfield.org/)
- [QGIS documentation: network analysis tools](https://docs.qgis.org/latest/en/docs/user_manual/processing_algs/qgis/networkanalysis.html)
