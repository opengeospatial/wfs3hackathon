# Implementations

## Servers

### [ldproxy](http://interactive-instruments.github.io/ldproxy/)-based

Server for the hackathon - landing page for several services:
* http://wfs3hackathon.ldproxy.net/rest/services/
* We can update these services and add additional datasets (as long as there is a public WFS 2.0 is available)

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

### (add your own implementations)


...

## Clients

### (add your own implementations)

...
