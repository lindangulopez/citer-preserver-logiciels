# Getting started — complete the workflow on your own fork

This checklist is for anyone who saw the 15 October 2026 webinar (or is just finding this
repo) and wants to complete the whole CodeMeta → Software Heritage/SWHID → citation workflow
solo, with no other context. The fastest way to do this is
[`notebooks/tutorial.ipynb`](../notebooks/tutorial.ipynb) — this page is its narrative,
non-Jupyter equivalent.

## 1. Fork and clone

1. Fork [`lindangulopez/citer-preserver-logiciels`](https://github.com/lindangulopez/citer-preserver-logiciels) on GitHub.
2. Clone your fork locally: `git clone https://github.com/<you>/citer-preserver-logiciels.git`

## 2. Open the QGIS project

1. Install [QGIS](https://qgis.org/) — this project was built with **3.34 (LTR)**; any recent
   3.x should work. See [`data/README.md`](../data/README.md) for details.
2. Open `qgis/rewilding_portugal_species_2025.qgz` (or the plain `.qgs`).
3. Confirm the 7 layers render — compare against
   [`docs/img/qgis-study-area-reference.png`](img/qgis-study-area-reference.png). If a layer
   shows as broken/red, your QGIS install may be missing GeoPackage or delimited-text support.
4. Open **Project Properties → Metadata** and a layer's **Properties → Metadata** tab — this is
   the project's native QGIS metadata (title, abstract, keywords, lineage), separate from
   `codemeta.json`.

## 3. Describe the software with CodeMeta

Follow [`exercises/generate-codemeta.md`](../exercises/generate-codemeta.md): generate your
fork's `codemeta.json` with SOMEF via GitHub Actions, and compare it against the worked example
at the repo root.

## 4. Enable the automation

Confirm `.github/workflows/generate-codemeta.yml` and `validate-codemeta.yml` are enabled on
your fork (Settings → Actions), then trigger `generate-codemeta.yml` manually from the Actions
tab (`workflow_dispatch`) and check the resulting `codemeta.generated.json`.

## 5. Archive it and get a SWHID

Follow [`docs/guided-demo.md`](guided-demo.md) Part 3: submit your fork to
[Software Heritage's "Save code now"](https://archive.softwareheritage.org/save/), then find
and record your own SWHID via the archived repo's permalink.

## 6. See how it connects to citation

Read [`docs/guided-demo.md`](guided-demo.md) Part 4 — Zenodo, HAL, and how `codemeta.json`,
the SWHID, and a DOI all point at the same underlying software from different angles.

## You're done when...

- [ ] Your fork's QGIS project opens with all 7 layers rendering correctly.
- [ ] You have a `codemeta.json` you generated and reviewed yourself (not just the copied one).
- [ ] The `generate-codemeta.yml` and `validate-codemeta.yml` workflows have run successfully on your fork.
- [ ] Your fork is archived in Software Heritage and you have its SWHID.
- [ ] You can explain, in one sentence each, what CodeMeta describes, what a SWHID identifies, and what a DOI (Zenodo) or HAL record adds on top.
