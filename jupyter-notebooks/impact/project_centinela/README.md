# Project Centinela

Project Centinela is a biodiversity conservation programme that pairs Planet
imagery with the work of conservation organisations monitoring high-value
ecosystems. Partner organisations each steward one or more field sites, and
Planet data is used to observe those sites consistently over time — tracking
habitat condition and change at a cadence that field survey alone cannot reach.

This folder collects the notebooks behind that work: reproducible examples of
how satellite imagery and Planetary Variables are turned into the indicators
conservation teams actually use.

## What you can expect here

The notebooks in this folder are written to be run against your own area of
interest, not just ours. Each one is standalone, though some build on data
prepared in an earlier notebook.

Broadly, they cover:

* **Defining and managing sites** — turning a protected-area boundary or
  concession polygon into an AOI you can reuse across Planet APIs.
* **Setting up recurring monitoring** — using the Subscriptions API to deliver
  imagery and Planetary Variables for a site on an ongoing basis, rather than
  ordering scene by scene.
* **Deriving biodiversity-relevant indicators** — vegetation condition, canopy
  and land cover change, water extent, and other measures that act as proxies
  for habitat health.
* **Detecting and reviewing change** — comparing a site against its own history
  to surface where something has changed and how much.
* **Reporting results** — summarising site-level change into the tables, charts
  and exports that go back to partners and funders.

## Getting started

These notebooks need a Planet account with access to the relevant imagery and
Planetary Variables. If you don't have one, you can
[create a 30-day trial](https://insights.planet.com/sign-up/).

Setup instructions, including how to provide your API key, are in the
[repository README](../../../README.md). For an introduction to the APIs used
throughout this folder, see [`api_guides`](../../api_guides) — in particular the
[Subscriptions API](../../api_guides/subscriptions_api) and
[Features API](../../api_guides/features_api) guides.

## Notebooks

### Land cover classification (BioMA)

A three-part workflow that turns PlanetScope surface reflectance basemaps into a
land use / land cover map for a site. Run them in order — each notebook consumes
what the previous one produced.

| Notebook | Description |
| -------- | ----------- |
| [1. Basemaps download](1_bioma_basemaps_download.ipynb) | Explore and download Planet surface reflectance basemaps for an area of interest using the Orders API. |
| [2. Train classifier](2_bioma_train_classifier.ipynb) | Build a training dataset from labelled polygons, sample representative pixels, and train a Random Forest land cover classifier. |
| [3. Basemaps inference](3_bioma_basemaps_inference.ipynb) | Apply the trained model across a full basemap AOI to produce a classified land cover map. |

Notebook 2 writes out `rf_model.pkl` and `rf_model_metadata.json`, which
notebook 3 expects as inputs.

### Burn area mapping

| Notebook | Description |
| -------- | ----------- |
| [Burn area index](project_centinela_burn_area_index.ipynb) | Order basemap quads for an area of interest with a Burn Area Index band computed server-side by the Orders API band math tool, then download and visualise the result over true colour. |

This notebook reads its area of interest from a GeoJSON file. Set the `aoi`
variable in the ordering cell to point at your own geometry before running it.
