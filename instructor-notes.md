---
title: 'Instructor Notes'
---

## Overall approach

- The food desert case study has a short reading part (the concept, the USDA method and its limitations)
  and two notebooks. The Beginner notebook takes about 30 to 45 minutes; the Expert notebook is longer and
  works best as a guided demonstration or take-home exercise.
- Ask learners to request and **activate** a Census API key before the session. The Expert notebook's
  `API_KEY` is empty by default, and the Census API refuses requests without a key.
- The Data Collection module's Census notebooks (boundaries, the Census API and joining tables to maps) are
  good preparation.

## Teaching tips

- Start by asking learners how *they* would define a food desert. Then show how many choices the USDA has to
  make: which stores count, how far is "far", urban or rural, and whether car ownership matters.
- Compare the four LILA maps from the Beginner notebook side by side; the change between measures is the
  main lesson.
- Mention the **July 2026 update**: the Atlas is now two maps. The notebooks use the 2019 Large Retailer
  Access Map data. The new SNAP-Authorized Retailer Access Map counts many more (smaller) stores, so it
  usually shows less "low access", and the two are not directly comparable.
- Discuss limitations openly: straight-line distance, the store list, food prices and quality, and the
  "food swamp" critique.

## Common problems

| Symptom | Likely cause | Fix |
|---|---|---|
| The Atlas cell is slow | The USDA spreadsheet is large | Wait a few minutes; this is normal |
| Census API errors in the Expert notebook | `API_KEY` empty, mistyped or not activated | Paste the key and check its activation email |
| The join produces no matches | Tract IDs stored as numbers | Convert both `GEOID` and `CensusTract` to strings, padded to 11 characters |
| OpenStreetMap request fails or times out | The Overpass server is busy | Wait a minute and rerun the cell |
