# Case Studies in Geospatial Social Science

Source for the **Case Studies** module of
[Enabling the Geospatial Turn in the Social Sciences](https://spatialturn.github.io/),
published at <https://spatialturn.github.io/CaseStudies/>.

The lesson is built with [The Carpentries Workbench](https://carpentries.github.io/sandpaper-docs/).

## Case studies

| Episode file | Case study | Notebooks |
|---|---|---|
| `episodes/introduction.md` | Food deserts: the USDA low-income, low-access (LILA) measure | `notebooks/TIGER_FoodDesert_Tutorial.ipynb` (Beginner) and `notebooks/Food_Desert_Analysis_Automated.ipynb` (Expert) |
| `episodes/grocery-qfield.md` | Grocery access, Part 1: mapping grocery stores with QField (demonstration) | None (QGIS loads `data/grocery_stores.geojson` by URL) |
| `episodes/grocery-network.md` | Grocery access, Part 2: shortest paths and service areas in QGIS | None (QGIS loads the three files in `data/` by URL) |

### Data used by the notebooks

### Food deserts

The two notebooks moved here from the retired DataCollection-Notebooks repository in October 2026.

All data is read from the web while the notebooks run:

- Census tract boundaries: U.S. Census Bureau TIGER/Line files
- Food Access Research Atlas (2019 data, now called the Large Retailer Access Map): USDA Economic Research Service
- Income, poverty, population and vehicle data (Expert notebook): U.S. Census Bureau API, which needs a free key from <https://api.census.gov/data/key_signup.html>
- Supermarket locations (Expert notebook): (c) OpenStreetMap contributors, Open Database License

### Grocery access

The case study was moved here from the Data Collection module in October 2026. QGIS reads these files from
`https://raw.githubusercontent.com/SpatialTurn/CaseStudies/main/data/<file>`.

| File | Contents | Source |
|---|---|---|
| `data/grocery_stores.geojson` | 64 food stores in and around Lafayette and West Lafayette, Indiana (17 supermarkets, 2 wholesale, 45 convenience), October 2026 | (c) OpenStreetMap contributors, [Open Database License](https://opendatacommons.org/licenses/odbl/) |
| `data/roads.geojson` | 3,466 road segments covering both cities and a margin around them | U.S. Census Bureau, TIGER/Line 2024 (public domain) |
| `data/study_area.geojson` | City limits of Lafayette and West Lafayette | U.S. Census Bureau, 2024 cartographic boundary files (public domain) |

The figures named `dc_*.png` in `episodes/` were made for the Data Collection module (with
`figure_builders/dc_figures.py`) from these files and American Community Survey 2020-2024 data. Each has a
`-dark` copy for the site's dark mode.

Contact: ilindsay@purdue.edu
