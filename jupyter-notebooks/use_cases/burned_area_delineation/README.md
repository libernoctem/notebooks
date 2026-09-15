# Burned Area Delineation

Two notebooks for mapping burn scars from PlanetScope data. Both use the Burned
Area Index (BAI), which measures how close a pixel's red and near-infrared
response is to that of strongly burned ground, but they apply it differently and
suit different situations.

| Notebook | Description |
| -------- | ----------- |
| [Park Fire](park_fire.ipynb) | Maps the extent of the Park Fire (2024) by streaming PlanetScope mosaics and differencing NDVI and BAI between a before and an after date. Thresholds and cleans the result, then vectorises the burn scar to GeoJSON. |
| [Burn Area Index](burn_area_index.ipynb) | Computes BAI for a single date server-side via the Orders API band math tool, so only the clipped area of interest is downloaded. Visualises the index over true colour imagery. |

## Which to use

**[Park Fire](park_fire.ipynb)** is the fuller treatment of delineation. Because
it compares two dates, it separates ground that *became* burned from ground that
was simply bare to begin with — non-vegetated terrain scores high on BAI whether
or not it has burned. It also masks water, which BAI differencing is sensitive
to, and produces a vector boundary you can measure and share. Use it when you
need a defensible burn extent.

**[Burn Area Index](burn_area_index.ipynb)** is the lighter-weight option, and
demonstrates a different capability: pushing the band math to Planet's servers
rather than computing locally. Only the clipped result crosses the network, which
matters over large areas or slow connections. Because it works from a single
date, its output is best read as a visual indicator rather than a classified
burn extent.

A sample area of interest, [`fire_demo_aoi.geojson`](fire_demo_aoi.geojson), is
included for the Burn Area Index notebook.
