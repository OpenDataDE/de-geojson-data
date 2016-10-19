# de-geojson-data
A collection of GeoJSON files for Delaware!

GeoJSON is great for open source mapping libraries like [Leaflet](http://leafletjs.com/), 
but sometimes you can only get a KML or Shapefile. Open Data Delaware
to the rescue! We've converted these formats for you. And here's [Leaflet example showing state Representative 
districts](http://bl.ocks.org/enactdev/4553334882f8d9f66787330639d90f87). (Click the id 45533.... to view it on
Github's Gists site).

Everything in the "firstmap" directory was converted from 
[opendata.firstmap.delaware.gov](http://opendata.firstmap.delaware.gov/) 

The nine datasets in the "firstmap/boundaries" were converted on Oct. 19, 2016. Here's an example of what we did to convert the 
KML file of state representative districts:

A KML file of the representative districts was downloaded from 
[opendata.firstmap.delaware.gov](http://opendata.firstmap.delaware.gov/datasets/c7eb6e2ee15d4c27be2a2a67c3d88c6d_0) 

And then converted to GeoJSON with the node project 
[toGeoJSON](https://github.com/mapbox/togeojson).

```
togeojson Districts_Representative.kml  > de_districts_representative.json
```

Then minified with the node project 
[json-minify](https://www.npmjs.com/package/json-minify).

```
json-minify de_districts_representative.json > de_districts_representative.min.json
```

Then the file 'de_districts_representative.min.json' was added to the project. 


Data in the "census" directory came from the US Census. Currently just a zip code boundaries file. Thanks to Github user
[jgoodall for his us-maps example](https://github.com/jgoodall/us-maps)! Below is an edited version of his 
national example showing how to generate the file for Delaware.


#### Zip codes
* In a browser, visit: https://www.census.gov/cgi-bin/geo/shapefiles2010/main
* Choose 'Zip Code Tabulation Areas' and 'Submit'
* Choose 'Delware' for '5-Digit ZIP Code Tabulation Area (2010)' and click 'Download'

Then unzip the files, and run 
[ogr2ogr](http://www.gdal.org/)! 


```
ogr2ogr -f "GeoJSON" de_zipcode_boundaries.json tl_2010_10_zcta510.shp
```

The file was minified like above, then the file 'de_zipcode_boundaries.min.json' was added to the project. 

