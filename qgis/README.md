# Projet QGIS : suivi des espèces dans la Grande Vallée du Côa

Projet QGIS utilisé comme fil rouge du webinaire « Citer et préserver des codes et logiciels avec SWHID et CodeMeta » (15 octobre 2026). Il cartographie une zone d'étude de 30 km autour de la rivière Côa, au Portugal, avec les espèces citées par le rapport annuel 2025 de Rewilding Portugal et les observations affichées sur les panneaux de quatre sites.

## Fichiers de ce dossier

| Fichier | Contenu |
| --- | --- |
| `rewilding_portugal_species_2025.qgs` | Le projet, en XML lisible. C'est la version à lire, à comparer et à citer. |
| `rewilding_portugal_species_2025.qgz` | Le même projet, compressé. Copie de commodité. |
| `rewilding_portugal_species_2025_attachments.zip` | Pièces jointes du projet : une base de styles (`KIObeO_styles.db`). |
| `codemeta.json` | Description du projet **comme logiciel** (CodeMeta 2.0). |
| `dataset.jsonld` | Description des données cartographiées **comme jeu de données** (schema.org `Dataset`). |
| `README.md` | Ce fichier. |

## Ouvrir le projet

1. Installer QGIS 3.34 LTR ou une version 3.x plus récente.
2. Cloner ou forker le dépôt, puis ouvrir `qgis/rewilding_portugal_species_2025.qgz`.
3. Les sept couches s'affichent sans configuration : les chemins vers `../data/` sont relatifs. Seul le fond OpenStreetMap demande une connexion.

## Couches

| Couche | Source | Type | Système de coordonnées |
| --- | --- | --- | --- |
| Greater Côa Valley study area (30km) | `data/study_area.gpkg`, couche `study_area` | Polygone (1) | EPSG:3035 |
| Côa river | `data/study_area.gpkg`, couche `coa_river` | Lignes (31) | EPSG:4326 |
| Species — Faia Brava, Vale Carapito, Ermo das Águias, Ribeira do Mosteiro | `data/visitor_board_species_2026.csv`, colonnes `x`/`y` | Points (41) | EPSG:4326 |
| Named species present (Greater Côa Valley) | `data/annual_review_2025_species.csv` | Table (7 lignes) | aucun |
| Aggregate species counts (not itemised in report) | `data/annual_review_2025_aggregate_counts.csv` | Table (4 lignes) | aucun |
| OpenStreetMap | Tuiles XYZ distantes | Raster | EPSG:3857 |
| Carte du monde | Données d'exemple fournies avec QGIS | Polygones | EPSG:4326 |

Système de coordonnées du projet : **EPSG:3035, ETRS89-extended / LAEA Europe**. Emprise approximative en WGS 84 : longitude -7,59 à -6,54, latitude 40,00 à 41,36.

## Trois niveaux de métadonnées

Ce dossier décrit le même projet de trois façons, et c'est voulu :

- (i) **Les métadonnées QGIS**, dans le projet lui-même : Propriétés du projet, onglet Métadonnées (titre, résumé, mots-clés, auteur, date), et la même chose pour chaque couche. Elles décrivent les données, dans QGIS.
- (ii) **`codemeta.json`** décrit le projet comme un logiciel. Le fichier `.qgs` contient la méthode : les sources, la projection, les styles. Il dépend de QGIS (`runtimePlatform`, `softwareRequirements`).
- (iii) **`dataset.jsonld`** décrit les données cartographiées comme un jeu de données schema.org : couverture spatiale et temporelle, variables, fichiers, sources.

CodeMeta n'a pas de champ pour « un projet SIG livré avec le logiciel ». Le `codemeta.json` à la racine du dépôt utilise `runtimePlatform: "QGIS 3.34"`. Ce dossier montre l'autre réponse possible : décrire à part le projet (logiciel) et ses données (jeu de données). C'est le point de discussion de la diapositive 14.

## Provenance et limites

- Les données viennent d'un projet de recherche privé d'illustration naturaliste sur la Grande Vallée du Côa. Elles sont reprises ici comme exemple pédagogique et ne sont pas la copie de référence. Voir `../data/README.md`.
- Les sources sont citées ligne par ligne dans les CSV : pages du rapport annuel 2025 de Rewilding Portugal, panneaux d'information, sites touristiques.
- La licence MIT du dépôt couvre le projet QGIS. **La licence des données reprises de Rewilding Portugal reste à confirmer** avant toute réutilisation hors de ce dépôt.
- `data/study_area.gpkg` contient aussi une couche `coa_catchment_rivers` (39 lignes) qui n'est pas chargée dans le projet.

## Citer ce projet

Archiver le dépôt avec Save code now (https://archive.softwareheritage.org/save/), puis, dans l'archive, ouvrir le dossier `qgis/` et copier le SWHID de type répertoire dans l'onglet « Permalinks ». Pour citer le projet seul, utiliser la forme qualifiée avec `path=/qgis/`.

*Linda Angulo Lopez, 14 octobre 2026*
