# Implementations

## Servers

### [ldproxy](http://interactive-instruments.github.io/ldproxy/)-based

Server for the hackathon - landing page for several services:
* http://wfs3hackathon.ldproxy.net/rest/services/
* We can update these services and add additional datasets (as long as there is a public WFS 2.0 is available)

New capabilities added / bugs fixed:
* [added the /api/conformance endpoint](https://github.com/interactive-instruments/ldproxy/issues/99), example: http://wfs3hackathon.ldproxy.net/rest/services/test/api/conformance
* [added links in the collection response in JSON, including XML schema links](https://github.com/interactive-instruments/ldproxy/issues/97), example: http://wfs3hackathon.ldproxy.net/rest/services/test/?f=json
* [media type bugfixes](https://github.com/interactive-instruments/ldproxy/issues/100)
* [activated CORS for every JSON endpoint](https://github.com/interactive-instruments/ldproxy/issues/103)
* [moved minItems/maxItems in OpenAPI definition](https://github.com/interactive-instruments/ldproxy/issues/105)

Other servers (OpenAPI documents):
* https://www.ldproxy.nrw.de/kataster/api/
* https://www.ldproxy.nrw.de/topographie/api/

### [CubeWerx](http://www.cubewerx.com)
* http://www.pvretano.com/cubewerx/cubeserv/default/wfs/3.0.0/foundation (still a bit rough tough!)

### [go-wfs](https://github.com/go-spatial/go-wfs/)

Golang server implementing core wfs3 w/ zero-config GeoPackage data source support & geojson encoding plus filtering.  Looking for other golang developers to fill it out & solidify it for production use.  Examples of good places to contribute:
* Add support for PostGIS backends
* Add html encoding support
* Now that its starting to settle, tests would be good.
* Clean up endpoints; filtering params may be better suited for PUT requests than GET params.
* More detalied configuration to limit features / add metadata to data sources.
* Migrate OpenAPI spec from v2 -> v3

Running at:
* http://192.168.111.154:80 (JWP network)
* ~~http://wfs.jivanamara.net:9000~~ (out of date)
* http://geo.kralidis.ca/go-wfs/


### [pygeoapi](https://github.com/geopython/pygeoapi)

Running at:
* http://geo.kralidis.ca/pygeoapi/

### GeoServer

An incomplete implementation of the WFS3 specification is available at http://cloudsdi.geo-solutions.it/geoserver/wfs3/ 
It is a community module developed from scratch during the WFS 3 hackaton. 
At the time of writing, still misses HTML outputs, conformance call, paging links (supports random paging with startIndex), 
single feature outputs and attribute filtering.

### (add your own implementations)


...

## Clients

### [GDAL/OGR](http://gdal.org)
* [WFS 3.0 experimental driver documentation page](http://gdal.org/drv_wfs3.html)
* [WFS 3.0 client code (C++)](https://github.com/OSGeo/gdal/blob/trunk/gdal/ogr/ogrsf_frmts/wfs/ogrwfs3driver.cpp)
* [WFS 3.0 driver integration tests (Python)](https://github.com/OSGeo/gdal/blob/trunk/autotest/ogr/ogr_wfs3.py) (against a stubbed implemenation)

### [An OpenLayers-based client](https://geekdenz.github.io/wfs-3-hackathon/)

### WFS3 extension for OpenLayers integrated in a [linked data portal](http://demo.highlatitud.es)
* [Example with www.ldproxy.nrw.de](http://demo.highlatitud.es/#/preview?url=https:~2F~2Fwww.ldproxy.nrw.de~2Fkataster~2Fapi~2F%3Ff%3Djson&ann=moz:13c69c6b-d813-407e-8f5b-3489ca0353b4&format=application~2Fvnd.ogc.wfs3)
* [Example with cloudsdi.geo-solutions.it](http://demo.highlatitud.es/#/preview?url=http:~2F~2Fcloudsdi.geo-solutions.it~2Fgeoserver~2Fwfs3~2Fapi&ann=moz:f06b0eac-f5ca-44a9-8a88-b45912258c29&format=application~2Fvnd.ogc.wfs3)
* [Example with wfs3hackathon.ldproxy.net](http://demo.highlatitud.es/#/mosaics/moz:e4c38da6-1b60-4e3e-a8cf-d207322dcd45/annot/moz:ab29e224-4e7b-4667-8fbe-ed63aeb57189?open=true)

Extension code to be externalized as a reusable lib.

### (add your own implementations)

...
