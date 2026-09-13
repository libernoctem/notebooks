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

_No notebooks have been added yet. As they land, list them here in the order
they are meant to be run, with a one-line description of what each covers._

| Notebook | Description |
| -------- | ----------- |
| _TBD_ | _TBD_ |
