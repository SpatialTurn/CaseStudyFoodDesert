---
title: 'Instructor Notes'
---

## Food deserts: overall approach

- The food desert case study has a short reading part (the concept, the USDA method and its limitations)
  and two notebooks. The Beginner notebook takes about 30 to 45 minutes; the Expert notebook is longer and
  works best as a guided demonstration or take-home exercise.
- Ask learners to request and **activate** a Census API key before the session. The Expert notebook's
  `API_KEY` is empty by default, and the Census API refuses requests without a key.
- The Data Collection module's Census notebooks (boundaries, the Census API and joining tables to maps) are
  good preparation.

## Food deserts: teaching tips

- Start by asking learners how *they* would define a food desert. Then show how many choices the USDA has to
  make: which stores count, how far is "far", urban or rural, and whether car ownership matters.
- Compare the four LILA maps from the Beginner notebook side by side; the change between measures is the
  main lesson.
- Mention the **July 2026 update**: the Atlas is now two maps. The notebooks use the 2019 Large Retailer
  Access Map data. The new SNAP-Authorized Retailer Access Map counts many more (smaller) stores, so it
  usually shows less "low access", and the two are not directly comparable.
- Discuss limitations openly: straight-line distance, the store list, food prices and quality, and the
  "food swamp" critique.

## Grocery access (Parts 1 and 2)

- The two parts share one example: grocery stores in Lafayette and West Lafayette, Indiana. Part 1 is a
  **demonstration** of a QField project; Part 2 is hands-on in QGIS. Suggested timing: Part 1 about 45
  minutes, Part 2 about 75 minutes.
- Part 1: if time and devices allow, a short walk to map a few campus locations with a prepared QField
  project makes it memorable.
- Part 2: the most important setting is the **project CRS** (EPSG:26916). If learners see costs around
  0.04, their project is still in EPSG:4326.
- Do **not** clip the roads to the city limits; the episode shows why. All 17 supermarkets are reachable
  with the provided road layer.
- With the full layer, routes from the Purdue Memorial Union to the 17 supermarkets average about 5.7 km by
  road against 5.0 km in a straight line. About 11% of city street length is within 800 m of a supermarket
  along the network, and about 40% within 1,600 m.
- The grocery store data comes from OpenStreetMap (October 2026) and is not field verified; say so when
  presenting results.
- The case pairs well with the food desert episode: the USDA uses straight-line distance, and Part 2 shows
  how much longer real routes are.
- The Data Collection module's Census episode (notebook 1c) makes the map of households without a car used
  in Part 2, Step 9. The Data Analysis module's Network Analysis episode does the same kind of analysis in
  Python with OSMnx.

## Common problems

| Symptom | Likely cause | Fix |
|---|---|---|
| The Atlas cell is slow | The USDA spreadsheet is large | Wait a few minutes; this is normal |
| Census API errors in the Expert notebook | `API_KEY` empty, mistyped or not activated | Paste the key and check its activation email |
| The join produces no matches | Tract IDs stored as numbers | Convert both `GEOID` and `CensusTract` to strings, padded to 11 characters |
| OpenStreetMap request fails or times out | The Overpass server is busy | Wait a minute and rerun the cell |
| Network costs are tiny (about 0.04) | Project CRS is EPSG:4326 | Set the project CRS to EPSG:26916 |
| Some routes have a NULL cost | Network broken, often by clipping | Use the full road layer |
| A web layer loads but nothing appears | Off screen or under another layer | Right-click > **Zoom to Layer**; reorder layers |
