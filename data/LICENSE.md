# Licences des données / Data licences

Le code et le projet QGIS de ce dépôt sont sous licence MIT (voir `../LICENSE`). Les données de ce dossier ont leurs propres licences, ouvertes.

The code and the QGIS project in this repository are under the MIT licence (see `../LICENSE`). The data in this folder have their own open licences.

| Fichier / File | Licence | Attribution |
| --- | --- | --- |
| `annual_review_2025_species.csv` | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | © 2026 Linda Angulo Lopez. Compilation from Rewilding Portugal, *Annual Review 2025* (page cited per row). |
| `annual_review_2025_aggregate_counts.csv` | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | © 2026 Linda Angulo Lopez. Compilation from Rewilding Portugal, *Annual Review 2025*. |
| `visitor_board_species_2026.csv` | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) | © 2026 Linda Angulo Lopez. Species listed on site information panels and tourism websites (source cited per row); geocoding by the author. |
| `study_area.gpkg` | [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/) | See below. |

## `study_area.gpkg`

The GeoPackage contains three layers:

- `coa_river`: OpenStreetMap ways. © OpenStreetMap contributors, https://www.openstreetmap.org/copyright. OpenStreetMap data is under the Open Database License, so this GeoPackage is distributed under **ODbL 1.0**, and any adapted version of it must be too.
- `study_area`: 30 km study-area polygon drawn by Linda Angulo Lopez.
- `coa_catchment_rivers` (not loaded in the QGIS project): from HydroRIVERS, HydroSHEDS. Lehner, B., Grill, G. (2013). Global river hydrography and network routing: baseline data and new approaches to study the world's large river systems. *Hydrological Processes*, 27(15), 2171-2186. https://www.hydrosheds.org/products/hydrorivers. Keep this attribution in any reuse.

## How to attribute / Comment citer

> Angulo Lopez, L. (2026). Greater Côa Valley species monitoring, teaching dataset. In *Citer et préserver des codes et logiciels avec SWHID et CodeMeta*. https://github.com/lindangulopez/citer-preserver-logiciels. Data: CC BY 4.0 (tables), ODbL 1.0 (study_area.gpkg, contains © OpenStreetMap contributors).

## Notes

- The tables record facts (species names, presence, counts) and short quotations used for citation, with their sources. The CC BY 4.0 licence covers the compilation; the sources keep their own rights.
- The OpenStreetMap basemap in the QGIS project is loaded from remote tiles and is not part of this folder: © OpenStreetMap contributors.
