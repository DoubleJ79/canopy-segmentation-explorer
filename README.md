# Canopy Segmentation Explorer

A Shiny app for segmenting crop canopy from a drone RGB orthomosaic and
reporting vegetation cover per plot.

Upload a drone orthomosaic (GeoTIFF) and a plot-boundary file, pick a
vegetation index, drag a threshold slider while watching a live segmentation
preview, then process at full resolution to get a vegetation mask, a
soil-masked RGB image, and percent vegetation cover per plot as a CSV.

## Indices available

- **Normalized ExGR**: `ExG - ExR` computed from each band normalized to its
  share of total brightness (`r = R/(R+G+B)`, etc.).
- **Raw ExGR**: `ExG - ExR = 3G - 2.4R - B`, unnormalized.
- **GRVI**: `(G - R) / (G + R)`, the same normalized-difference form as NDVI
  built from visible bands only.
- **ExG**: `2G - R - B`.
- **NDVI**: `(NIR - Red) / (NIR + Red)`, available once a near-infrared band
  is specified.

## Running locally

Requires R with the `shiny` and `terra` packages. Either:

- Open `app.R` in RStudio and click **Run App**, or
- From a terminal: `Rscript -e "shiny::runApp()"`

This project uses [renv](https://rstudio.github.io/renv/) to lock package
versions; run `renv::restore()` after cloning to install the exact versions
recorded in `renv.lock`.
