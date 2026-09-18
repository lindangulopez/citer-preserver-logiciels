# Data

These files are the local data sources for [`../qgis/rewilding_portugal_species_2025.qgs`](../qgis/rewilding_portugal_species_2025.qgs) (and its `.qgz` convenience copy).

## Provenance

They were originally produced for Linda Angulo Lopez's private rewilding-illustration
research project (`Solo-field-illustrator-project-for-Rewilding-Portugal`), covering
ecological-connectivity monitoring in the Greater Côa Valley (Portugal). They are **repurposed
here as a teaching example** for the 2026-10-15 SWHID/CodeMeta webinar — they are not the
canonical, currently-maintained copies of this data, and the QGIS project's data source paths
have been re-pointed (from that project's original layout) to these local, relative paths so
the project opens correctly straight after a fresh `git clone`/fork, with no other setup.

## Files

| File | Used by layer(s) | Content |
| --- | --- | --- |
| `study_area.gpkg` | Côa river, Greater Côa Valley study area (30km) | GeoPackage with the `coa_river` line layer and the `study_area` 30km buffer polygon. |
| `annual_review_2025_species.csv` | Named species present (Greater Côa Valley) | Non-spatial table of named species present across the monitoring sites (2025 annual review). |
| `annual_review_2025_aggregate_counts.csv` | Aggregate species counts (not itemised in report) | Non-spatial table of aggregate species counts from the 2025 annual review. |
| `visitor_board_species_2026.csv` | Species — Faia Brava, Vale Carapito, Ermo das Águias, Ribeira do Mosteiro | Geocoded (`x`/`y`, EPSG:4326) visitor-board species sightings at four named sites. |

Two other layers in the project need no local data: the OpenStreetMap basemap (remote XYZ
tiles) and "Carte du monde" (QGIS's own bundled `inbuilt:/data/world_map.gpkg` sample data).

## QGIS version

The project was authored and re-pointed with **QGIS 3.34 (LTR, "Prizren")**. Any recent QGIS
3.x desktop install with GeoPackage/OGR and delimited-text support should open it correctly.

## Metadata

Both the project and its key layers (`study_area`, `coa_river`, the two annual-review CSVs, and
the visitor-board CSV) carry native QGIS metadata (title/abstract/author/keywords, and a
per-layer lineage note repeating the provenance above) — open **Project Properties → Metadata**
or a layer's **Properties → Metadata** tab in QGIS to see it. This is a deliberate teaching
example of QGIS's own metadata, distinct from and complementary to this repo's `codemeta.json`
(which describes the *software*, not the *data*) — see [`../docs/guided-demo.md`](../docs/guided-demo.md).
