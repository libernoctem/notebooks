# Project Centinela

Project Centinela is a biodiversity conservation programme that pairs Planet
imagery with the work of conservation organisations monitoring high-value
ecosystems. Partner organisations each steward one or more field sites, and
Planet data is used to observe those sites consistently over time — tracking
habitat condition and change at a cadence that field survey alone cannot reach.

This folder collects the notebooks behind that work: reproducible workflows that
turn Planet basemaps into the land cover and change information conservation
teams use in the field.

## What you can expect here

The notebooks are written to be run against your own area of interest, not just
ours. Two workflows are covered so far:

* **Land cover mapping** — a three-stage tool that trains a classifier on your
  own knowledge of a site, then applies it across the whole area.
* **Burn area mapping** — computing a Burn Area Index over a site to locate and
  assess fire damage.

Further programme notebooks will be added here over time.

## Getting started

These notebooks need a Planet account with access to PlanetScope surface
reflectance basemaps. If you don't have one, you can
[create a 30-day trial](https://insights.planet.com/sign-up/).

Setup instructions, including how to provide your API key, are in the
[repository README](../../../README.md). Both workflows are built on Planet
basemaps and the Orders API — see the
[Orders API](../../api_guides/orders_api) and
[Basemaps API](../../api_guides/basemaps_api) guides for an introduction.

## Notebooks

### Land cover mapping

A three-stage workflow that turns 4.7 m PlanetScope surface reflectance basemaps
into a land cover map for a site. You order the imagery, train a classifier using
your own local knowledge of the ground, and then run that model across the whole
site.

Run the notebooks in order — each one consumes what the previous produced.

| Notebook | Description |
| -------- | ----------- |
| [1. Planet Basemap Downloader](1_planet_basemap_downloader.ipynb) | Explore and download Planet surface reflectance basemaps for an area of interest using the Orders API. |
| [2. Land Cover Classification with Random Forest](2_land_cover_classification_random_forest.ipynb) | Build a training dataset from labelled polygons, sample representative pixels, and train a Random Forest classifier. |
| [3. Inference Workflow](3_land_cover_classification_inference.ipynb) | Apply the trained model across the full basemap AOI to produce a classified land cover map. |

Notebook 2 writes out `rf_model.pkl` and `rf_model_metadata.json`, which notebook
3 expects as inputs.

The notebooks use BioMA as their worked example — the area the tool was developed
and tested against. Point them at your own area of interest to run the workflow
over your site.

Planet runs a free workshop that walks through this tool end to end:
[Project Centinela — Land Cover Mapping Workshop](https://university.planet.com/project-centinela-land-cover-mapping-workshop).
Registration is required but the course is free.

### Burn area mapping

| Notebook | Description |
| -------- | ----------- |
| [Burn area index](burn_area_index.ipynb) | Order basemap quads for an area of interest with a Burn Area Index band computed server-side by the Orders API band math tool, then download and visualise the result over true colour. |

This notebook reads its area of interest from a GeoJSON file. Set the `aoi`
variable in the ordering cell to point at your own geometry before running it.
