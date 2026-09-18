# Guided demo: from a code repository to a citable, preserved piece of software

This is the full walkthrough behind the 15 October 2026 webinar, "Citer et préserver des
codes et logiciels avec SWHID et CodeMeta." It follows one continuous thread — this
repository and its [QGIS project](../qgis/) — through four stages:

```
Dépôt de code  →  codemeta.json  →  Archive Software Heritage  →  SWHID  →  Zenodo / HAL  →  Citation
```

The point isn't to run four disconnected tools. It's to see how **describing** (CodeMeta),
**preserving and identifying** (Software Heritage, SWHID), and **citing** (Zenodo, HAL) are
three complementary pieces of the same research-software lifecycle.

---

## Part 2 (continued) — Describing: CodeMeta

See [`exercises/generate-codemeta.md`](../exercises/generate-codemeta.md) for the hands-on
steps (generate with SOMEF, compare against [`codemeta.json`](../codemeta.json), fix pitfalls).

**A genuine modeling ambiguity worth discussing live:** this repository bundles a QGIS
*project* — itself a small file that references *data* — alongside the *software* (the
site/tooling). CodeMeta has no dedicated field for "a GIS project shipped as part of a
software repository." The worked example uses `runtimePlatform: "QGIS 3.34"` as the closest
fit, but that's a judgment call, not a clean answer — a good moment to point out that metadata
standards always involve some interpretation, and that the QGIS project *also* carries its own
native metadata (`data/README.md`), which describes the **data**, not the **software** — two
complementary layers, not a duplicate of `codemeta.json`.

---

## Part 3 — Preserving and identifying: Software Heritage & SWHID

### Archiving a repository

1. Go to [Software Heritage — Save code now](https://archive.softwareheritage.org/save/).
2. Enter your fork's GitHub URL (e.g. `https://github.com/<you>/citer-preserver-logiciels`).
3. Submit — Software Heritage will clone and archive it. This can take from seconds to a few
   minutes depending on load.

### What archiving preserves — and what CodeMeta describes

These are **complementary**, not overlapping:

| | Software Heritage archiving | CodeMeta (`codemeta.json`) |
| --- | --- | --- |
| Preserves | The full git history: every commit, branch, and tag — the actual source code, byte for byte. | Nothing about the code itself — structured *descriptive* metadata (name, authors, license, dependencies…). |
| Identifies | Precisely, via a content-addressed hash (the SWHID) — any exact commit, directory, or file. | Loosely — a `codeRepository` URL, which can change, go offline, or point at a moving branch. |
| Answers | "Can I retrieve this exact state of the code, forever, even if GitHub disappears?" | "What is this software, who made it, and how do I re-run it?" |

A `codemeta.json` that survives only on a live GitHub repo can vanish with the repo. A SWHID
that points at preserved code with no description is hard to discover or understand. You need
both.

### Retrieving and reading a SWHID

Once archived, Software Heritage's UI exposes a **permalink** (the small `⚓` / "Permalink"
button) with a SWHID at whichever granularity you're looking at:

- `swh:1:snp:...` — a **snapshot** of the whole repository (all branches/tags at archival time).
- `swh:1:rev:...` — one specific **revision** (commit).
- `swh:1:dir:...` — one specific **directory** tree.
- `swh:1:cnt:...` — one specific **file's content**.

Each identifier is a hash computed from the object's content — two people archiving the exact
same commit get the exact same SWHID, independent of where it's hosted. That's what makes it a
durable, tool-verifiable identifier rather than a URL that can rot.

> **Worked example:** once `lindangulopez/citer-preserver-logiciels` has been archived, its
> SWHID(s) will be recorded here so you have a concrete "this is what you should get" reference:
>
> - Snapshot: _to be filled in after archiving `main`_
> - Revision (seed commit): _to be filled in_

---

## Part 4 — From preservation to citation

### `codemeta.json` → `CITATION.cff`

Most citation workflows (GitHub's own "Cite this repository" button, Zenodo) read a
`CITATION.cff` file, not `codemeta.json` directly. You can derive one from the fields you
already have with [`codemeta2cff`](https://github.com/codemeta/codemeta2cff), or by hand since
the fields largely correspond 1:1 (`name`, `author`, `version`, `license`, `codeRepository` →
`repository-code`).

### Zenodo

Linking a GitHub repository to Zenodo lets you mint a **DOI** for a release. The DOI and the
SWHID are not competing identifiers — they answer different questions: the DOI is what you put
in a paper's reference list and what tracks citation counts; the SWHID is what lets anyone
(including Zenodo itself, and Software Heritage's own cross-referencing) verify *exactly* which
bytes of code that citation refers to, independent of Zenodo staying online.

### HAL

[HAL](https://hal.science/) is the French national open archive. It's mentioned here as **one
example among several** — particularly relevant in the French context and to librarians who
curate metadata there — not as this webinar's focus. If you work with HAL for software
deposits, the same `codemeta.json` fields feed its deposit form.

### Closing the loop

```
Dépôt de code  →  codemeta.json  →  Archive Software Heritage  →  SWHID  →  Zenodo / HAL  →  Citation
```

Each arrow is a real, traceable link: `codemeta.json`'s `codeRepository` points at the repo
that got archived; the SWHID identifies precisely what was archived; the Zenodo/HAL record
cites both the DOI *and* (increasingly, as a best practice) the SWHID, so a reader can verify
the exact code behind a publication's results — not just trust that a link still resolves.

---

## Optional stretch: RSFC & RSMetadataCheck

See the note in [`exercises/generate-codemeta.md`](../exercises/generate-codemeta.md) — these
steps (Steps 4–8) require confirming current tool/action names closer to the webinar date, since
the templates referenced by the original RSECon26 exercise were never actually included in this
repository.

## Crediting AI coding agents

See [`notebooks/tutorial.ipynb`](../notebooks/tutorial.ipynb) (closing section) for a short,
concrete discussion of how to credit AI agent involvement in your own fork's commits and
metadata — the same provenance reasoning this whole webinar applies to software applies to how
that software was produced.
