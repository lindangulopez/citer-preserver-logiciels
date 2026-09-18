# Citer et préserver des codes et logiciels avec SWHID et CodeMeta

Site pour le webinaire du **15 octobre 2026** « Citer et préserver des codes et logiciels avec SWHID et CodeMeta », destiné aux ingénieur·e·s et chargé·e·s de données / développement (BAP D & E).

Le site est volontairement construit en HTML et CSS simples afin d'être publié directement avec **GitHub Pages** et facilement modifiable.

Ce dépôt est adapté de [oeg-upm/rsecon26-codemeta](https://github.com/oeg-upm/rsecon26-codemeta) (MIT, Ontology Engineering Group – UPM), l'atelier CodeMeta donné récemment à RSECon26, dont il reprend l'approche GitHub Actions pour la production de métadonnées.

## Objectif

Comprendre comment rendre les codes et logiciels de recherche décrits, préservables, identifiables, citables et reproductibles, dans une démarche de science ouverte — en suivant un cas concret : un dépôt GitHub contenant un projet QGIS.

L'objectif n'est pas seulement de générer un `codemeta.json` ou de récupérer un SWHID, mais de comprendre comment ces éléments s'articulent dans un même workflow de recherche.

## Déroulé (2h)

| Durée | Séquence |
| ---: | --- |
| **15–20 min** | **1. Pourquoi préserver et citer les logiciels de recherche ?** — le logiciel comme résultat de recherche, reproductibilité et attribution, la troisième feuille de route française pour la science ouverte, introduction à Software Heritage et au SWHID. |
| **45–50 min** | **2. Décrire son logiciel avec CodeMeta : du dépôt aux métadonnées** — qu'est-ce que CodeMeta, mise en pratique sur ce dépôt et le projet QGIS, création d'un `codemeta.json`, automatisation avec GitHub Actions, bonnes pratiques. |
| **30–35 min** | **3. Préserver et identifier avec Software Heritage et SWHID** — archivage dans Software Heritage, récupération et lecture d'un SWHID, complémentarité entre CodeMeta et l'archivage/identification SWH. |
| **20–25 min** | **4. De la préservation à la citation** — workflows de citation avec Zenodo et HAL, HAL comme exemple pertinent pour le contexte français (curation par les bibliothécaires) sans en faire le focus, lien entre dépôt, métadonnées, identifiants et publication. |

La session est présentée en démonstration guidée, mais ce dépôt est documenté pour que chaque participant·e puisse le forker et refaire l'ensemble du parcours seul·e — voir [docs/getting-started.md](docs/getting-started.md) et [notebooks/tutorial.ipynb](notebooks/tutorial.ipynb).

## Contenu du dépôt

- [`qgis/`](qgis/) — le projet QGIS utilisé comme fil rouge (connectivité écologique, Vallée du Côa), rendu autonome (données incluses).
- [`data/`](data/) — les données référencées par le projet QGIS.
- [`codemeta.json`](codemeta.json) — exemple de métadonnées CodeMeta pour ce dépôt.
- [`.github/workflows/`](.github/workflows/) — automatisation de la génération et de la validation du `codemeta.json`.
- [`exercises/generate-codemeta.md`](exercises/generate-codemeta.md) — l'exercice guidé de génération de CodeMeta, adapté de RSECon26.
- [`docs/guided-demo.md`](docs/guided-demo.md) — le parcours complet : décrire → archiver → identifier → citer.
- [`docs/getting-started.md`](docs/getting-started.md) — check-list pour compléter le parcours seul·e après le webinaire.
- [`notebooks/tutorial.ipynb`](notebooks/tutorial.ipynb) — version exécutable du parcours (PyQGIS, métadonnées QGIS, CodeMeta, SWHID, citation).

## Remerciements

Les sections « Exercise 1 » et l'automatisation GitHub Actions reprennent et adaptent des éléments de l'atelier [Making Research Software FAIR with CodeMeta](https://github.com/oeg-upm/rsecon26-codemeta) donné à RSECon26 par l'Ontology Engineering Group (UPM).
