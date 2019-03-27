---
title: 'Cognition-Datasources'
subtitle: ''
date: 2019-03-01 00:00:00
description: STAC-compliant, cloud-native, standardized interface for searching geospatial assets.
featured_image: '/images/cognition-datasources/cover.png'
---

I learned early on that data acquisition is often the hardest and most time consuming component of any geospatial project.  In my undergraduate introductory GIS class, we learned how to navigate several online geospatial data repositories, namely [PASDA](https://www.pasda.psu.edu/) for state-wide data (my college is located in Pennsylvania), [USGS Earth Explorer](https://earthexplorer.usgs.gov/) for raster data, and [The National Map](https://viewer.nationalmap.gov/advanced-viewer/) for vector data.


![earth-explorer](/images/cognition-datasources/earth-explorer.png)
**<center>Figure 1: USGS Earth Explorer interface.</center>**

My first real experience with big geospatial data came during my undergraduate senior thesis, where I developed a climate projection model with ArcGIS which predicts the impact of climate change on a species' habitat by modeling reductions in range and suitability due to negative externalities created by the shifting climate.  The model took a wide variety of species-specific inputs (described in the table below) to generate a "current-day" habitat range and leveraged interpolated climate change data along with the [species survivorship curve](https://en.wikipedia.org/wiki/Survivorship_curve) to estimate a "future" habitat range which were compared to assess the impact of climate change on species habitat over the given time period.  I set the lofty goal of performing model runs for three separate species across two areas of interest: the state of Pennsyania and the combined states of California, Arizona, Utah, and New Mexico.  


![data-dict](/images/cognition-datasources/comp-data-dict.png)
**<center>Figure 2: Data dictionary describing non-climate geospatial datasets used in thesis.</center>**

The model was run at a 30 meter spatial resolution which amounted to ~200 million pixels in the combined AOIs for each data layer.  The data collection strategy was simple and low-tech.  This was long before my programming days so instead of writing some fancy multi-threaded application to quickly download the data in parallel, I logged into 7 separate computers in the GIS lab and started downloading.  I'd run back to the GIS lab a couple times a day to check the progress of the downloads, restart any that failed, and initiate a new download once one finished.  It was quite the operation.  After about 2 weeks of this process I had successfully downloaded and organized all of my project's required data on the shared server.  It took another 2 weeks of various geoprocessing (mosaicing, reprojecting etc.) to prepare all of the input data for analysis.  The entire data collection process, from identification of datasources to analysis ready data took close to a month.

I started work on my thesis almost 5 years ago; if I had to repeat the data acquisition process today I would do it much differently.  Partially because I've become a better developer, but mostly because the rise of cloud-native applications has fundamentally changed the way geospatial datasets are stored and accessed.  Cloud-native applications almost entirely solve the problem of ***quickly*** accessing geospatial data, because the data never actually leaves the server.  There is no need to download large geospatial datasets from a remote server to a local one, as was this case during my senior thesis.  Cloud-native processing also provides interesting interoperability with our numerous devices.  As long as I have enough bandwidth to connect to an API, I can quickly move terrabytes of geospatial data from a smart phone, or maybe even a refridgerator.  The result is less time spent moving our data and more time analyzing it!

## STAC
Cloud-computing may have solved the problem of how quickly we can access geospatial data, but there is still the problem of a lack of interoperability between available datastores.  Over the years, as new sources of geospatial data have come online, there has been little coordination between data providers to expose standard APIs for accessing their data.  This is a natural consequence for a use-case driven industry with very few agreed upon standards, explosive growth, and a wide range of customer requirements across multiple verticals.  Suddenly there are 100 different data sources from 100 different data providers accessed by 100 slightly different REST APIs to meet 100 different customer requirements.  ***Yikes***.  It isn't really anyone's fault, its just the way it is, and becomes especially frustrating on projects with data fusion requirements.

This is where [STAC](https://github.com/radiantearth/stac-spec) comes in.  From the documentation, the STAC spec "aims to standardize the way geospatial assets are exposed online and queried, with the goal for all major providers of imagery and other earth observation data to expose their data as SpatioTemporal Asset Catalogs so that new code doesn't need to be written whenever a new JSON-based REST API comes out that makes its data available in a slightly different way."  STAC promotes interoperability by defining a common flat file structure ([STAC Catalog](https://github.com/radiantearth/stac-spec/tree/master/catalog-spec)) and standard metadata schema ([STAC Item](https://github.com/radiantearth/stac-spec/tree/master/item-spec)) along with a dynamic API ([STAC API](https://github.com/radiantearth/stac-spec/tree/master/api-spec)) for indexing and querying the catalog.  STAC is a great solution to the interoperability problem, and I suspect that adoption of STAC will become widespread as the spec becomes more mature (v0.6 at the time of writing).  

## Cognition-Datasources
The goal of cognition-datasources is to define a STAC-compliant, cloud-native, standardized interface for searching geospatial datasets.  The standardized interface used by the library is based on the STAC spec and decomposes the search space into three dimensions: spatial, temporal, and properties. Spatial and temporal searches are standardized across all datasources exposed by the library while the available properties change from source to source (see the [docs](https://github.com/geospatial-jeff/cognition-datasources/tree/master/docs)).  This allows for multiple datasources to be queried with the same spatio-temporal query, similar to the interface exposed by Earth Explorer!

The library exposes access to both STAC-conformant and non-conformant APIs.  In the case of non-conformant APIs, the library implements server-side logic to translate the request from the standard STAC format to that compatible with the underlying API.  The API response is then translated back into a standard STAC Item and returned to the user.  This allows a STAC-like interface to be loosely implemented around data sources which aren't currently STAC-compliant.  STAC-conformant APIs are easier to implement because the request and response are already STAC-compliant!  As such, the library aims to provide access to currently existing STAC catalogs where available (ex. [sat-api](https://github.com/sat-utils/sat-api)).  The library also features a [dynamic STAC-API](https://github.com/geospatial-jeff/cognition-datasources-api) deployed with Flask and AWS Elasticbeanstalk which implements the minimum requirements to be considered STAC-compliant, the `stac/search/` POST endpoint.  The project's architecture looks something like:

![architecture-diagram](/images/cognition-datasources/architecture-diagram.png)
**<center>Figure 3: Architecture diagram of cognition-datasources.</center>**

### Usage
Cognition-datasources manages the searching of geospatial assets through the `datasources.Manifest` object, which provides methods for loading and searching the supported datasources.  Once a datasource is loaded, searches may be added to the manifest and executed in parallel via the `multiprocessing` module.  

```python
from datasources import Manifest
from datasources.sources import Landsast8, Sentinel2

# Create manifest
manifest = Manifest()

# Load sources
manifest.load_sources(Landsat8, Sentinel2)

# Search arguments
spatial = {"type": "Polygon", "coordinates": [[...]]}
temporal = ("2018-10-30", "2018-12-31")

# Create searches in manifest
for source in manifest:
    manifest[source].search(spatial, temporal=temporal)

# Execute searches in parallel
response  = manifest.execute()
```

The library also has a CLI which supports bounding box queries:

```bash
cognition-datasources search xmin ymin xmax ymax --start-date "2018-10-30" --end-date "2018-12-31" -d Landsat8 -d Sentinel2 --output response.json
```

The response returned by cognition-datasources is a dictionary of GeoJSON Feature Collections, with each feature in the collection being a STAC-compliant item representing a single asset returned by the query.  View examples of individual STAC Items returned by each datasource in the [documentation](https://github.com/geospatial-jeff/cognition-datasources/tree/master/docs/examples).


## Conclusion
Since STAC is still in development, its hard to expect perfect interoperability between each implementation due to the nuances involved with different use-cases.  In fact, the STAC community even encourages current implementations to go beyond the STAC spec to meet their use-cases in order to build up a robust collection of user stories.  Cognition-datasources, at its core, is a short-term solution to create interoperability between various STAC and non-STAC datasources as the spec matures.  My hope is that the library is ultimately replaced by the widespread adoption of STAC by users, developers, and data-providers alike at which point cognition-datasources is not needed.  Until that point, there is an immediate advantage to developing tools which extend the current STAC spec to promote interoperability.  Such tools not only enable data acquisition but also provide powerful examples of what a fully STAC-compliant ecosystem looks like, how it functions, and how it is beneficial to the entire geospatial community, from end-users to data providers.
