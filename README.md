# Mar del Plata North - Nourishment project 1998 

## Overview


CoastSat 2.0 toolkit (https://github.com/kvos/CoastSat), an open-source Python software for shoreline detection, was utilized to evaluate the performance of a beach nourishment project to characterize the pre- and post-state of three beaches in Mar del Plata, Buenos Aires Province, Argentina. The toolkit allows users to acquire time series of shoreline positions for any coastal area using available satellite imagery from the Google Earth Engine platform. In this case, it was used with data from the Landsat missions L5 (1986–2012), L7 (1999–2021), L8 (2013–2021), and the Sentinel mission S2 (2015–2021). Top-of-Atmosphere reflectance images from the Landsat missions with a resolution of 30 m and a revisit time of 16 days (Tier 1) were utilized, along with images from the Sentinel 2 mission with a resolution of 10 m and a revisit time of 5 days (Level-1C). Additionally, the toolkit employed spatial resolution enhancement techniques over Landsat images to map the position of the shoreline with an accuracy of ~10 m. In this repository, CoastSat-detected shorelines can be accessed along with the normal to shore transects from which the beach width time series were obtained to analyze beach response to nourishment. Tide-corrected beach width time series are also provided.

## Methodology

A 13.4 km2 polygon was used for the period 1986-2021. To ensure data quality, images with a pixel cloud cover exceeding 50% were discarded. The shoreline detection process consists of two main steps: image classification and sub-pixel resolution border segmentation. To enhance the detection of the sand/water interface, a neural network classifier was trained within the area of interest using S2 and L8 images between January 2019 and May 2019. The pixels in these images were manually labeled into categories such as sand, water, white water, and others. The "Modified Normalized Difference Water Index" (MNDWI) was employed for water detection. Automatic shoreline detection resulted in a total of 1604 shoreline detections (L5: 376, L7: 591, L8: 308, S2: 325). Subsequently, erroneous, misreference, and duplicate detections were eliminated, resulting in a total of 1054 usable images for the period 1986-2021. 

Shore-normal transects were established across the study area to estimate beach width from the coastline position.  In general, the transects are equidistant and 8 transects correspond to Playa Grande (PG1 to PG8), 9 to Varese (V1 to V9) and 15 transects correspond to Bristol. The starting point (zero) of each transect was set at the uppermost point of the beach, so the coastline position on the transect directly represents beach width at the time of the image acquisition. 

To  inter-compare beach widths, tidal correction was used to refer them to the tidal datum. For this purpose, the horizontal variation of BW along the transect resulting from tidal effects (Δx) was estimated as (Zref − Ztide)/s, where Zref is the tidal datum, Ztide the sea level corresponding to the image time, and s the typical beach slope. In this study, beach slopes from in-situ beach profiles compiled in Bértola (2006) were used (Playa Grande: 0.049; Varese: 0.052; Bristol: 0.033).  These represent characteristic values of different sectors within the study area and were assumed to remain constant over time. Hourly sea-level measurements were from the Mar del Plata tide gauge, operated by the Servicio de Hidrografía Naval (SHN) of Argentina, located in the northern sector of Bristol, at the Fishing Pier. However, the sea-level data series contained some gaps throughout the analyzed period (1986–2021). Consequently, in these cases, the corresponding satellite images were not considered (93 images of 1054). Beach-width estimations, ranging between 348 and 705 values, were obtained for each transect by applying the methodology described above for the period 1986–2021.

## File description

**Polygon.kml**: Polygon used to recover the satellite image of the GEE server.

**Shorelines**: Folder containing the shorelines obtained for the L5,L7,L8 and S2 satellites in geojson files.

**Transects.geojson**: Shore-normal transects used to obtain beach width time series.

**BW_time_series_tidaly_corrected.csv**: Tide-corrected beach width time series
