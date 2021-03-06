# Greenland Ice Mapping Project
Example notebooks for working with data from the [Greenland Ice Sheet Mapping Project](https://nsidc.org/data/measures/gimp), which provides benchmark data sets for observing ice sheet change and stability.

These datasets cover the entire landmass of Greenland and consequently images can be quite large. Often researchers are just interested in data covering a specific glacier. *The goal of these notebooks is to illustrate how to efficiently work with data using modern Python libraries that can read imagery directly on a server without downloading entire files first.* 

We'll work with Sentinel-1 backscatter mosasics stored as [Cloud-Optimized Geotiffs (COG)](https://nsidc.org/data/nsidc-0723). This imagery is publically-available and hosted by NASA's [National Snow and Ice Data Center](https://nsidc.org/data/nsidc-0723).


## Run these notebooks on the Cloud:
Clicking the following button will transport you into a temporary server running on [mybinder.org](https://mybinder.org/)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/scottyhq/greenland-ice-mapping-project/main?urlpath=lab)


## Run these notebooks on your own computer:
This requires that you have [conda](https://docs.conda.io/en/latest/miniconda.html) installed.
```
git clone https://github.com/scottyhq/greenland-ice-mapping-project.git
cd greenland-ice-mapping-project
conda env create -f binder/environment.yml
conda activate greenland-ice-mapping
jupyter lab
```

### prototype panel app
Clicking the following button will transport you into a temporary server a [Panel App](https://panel.holoviz.org):

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/scottyhq/greenland-ice-mapping-project/main?urlpath=%2Fpanel%2F3-subsetter-app)

Or you can run the app locally with the following commands (open URL reported by panel in your browser)
```
conda activate greenland-ice-mapping
panel serve 3-subsetter-app.ipynb 
```


#### troubleshooting

1. If you are trying to work with urls pointing to data at NSIDC or a nsidic0723-subset.vrt downloaded from the app linked above with GDAL, you need to specific a few environment variables:
```
GDAL_HTTP_COOKIEFILE=.urs_cookies GDAL_HTTP_COOKIEJAR=.urs_cookies gdalinfo nsidc0723-subset.vrt 
```
Because QGIS uses GDAL behind the scenes, you also need to set these environment variables within QGIS preferences, see [QGIS instructions](QGIS.md).