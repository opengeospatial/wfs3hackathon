## Overview 

This session was the last of the WFS 3 hackathon, with participants showing off all that they worked on. For those interested in diving in to all the details check out the [video](https://www.youtube.com/watch?v=FbH6TOwst7o) of the session.

#### Golang

Go proved to a popular language at the sprint, with two servers and one client. Jivan worked on [go-wfs](https://github.com/go-spatial/go-wfs/), getting most of the spec working and also making some issues to improve the WFS specification. Next steps are to explore a 'search' extension to do cross-collection searching. The Boundless team built a [go server](https://github.com/boundlessgeo/wfs3) focused on transactions. It targets AWS serverless deployment, running on Lambda, API Gateway and Aurora. On the client side Ian worked on a [go-wfs3-client](https://github.com/ischneider/go-wfs3-client) that could query servers and validate that they are working correctly. It works as a go library, but also a command line client.

#### C

Even built a [WFS 3.0 experimental driver](http://gdal.org/drv_wfs3.html) in GDAL, and got it working against a number of the services. The code is available [on github](https://github.com/OSGeo/gdal/blob/trunk/gdal/ogr/ogrsf_frmts/wfs/ogrwfs3driver.cpp). Peter evolved the Cubewerx server for several spec improvements, including some schema support.
* [WFS 3.0 driver integration tests (Python)](https://github.com/OSGeo/gdal/blob/trunk/autotest/ogr/ogr_wfs3.py) (against a stubbed implemenation). And Ryan was able to implement WFS 3 on top of Pixia's catalog.

#### Python

The [pygeoapi](https://github.com/geopython/pygeoapi) team of Tom, Angelos, Norman, Matt and Jorge built a python WFS server from scratch, leveraging the swagger specification to generate bindings. It works with different providers - initially just csv and geojson, but is built to easily add other data sources. The team got the core working, and also explored transaction extensions, doing simple post / put. Samweli also worked on a QGIS plugin. 

#### Java

Andrea built a [WFS3 community module](https://github.com/geoserver/geoserver/tree/master/src/community/wfs3) for GeoServer, getting the basics working. He found the spec more manageable than previous WFS versions. Work on that will continue for OGC Testbed 14, and likely will push on extensions as many GeoServer users need things like different coordinate systems and transactions. Janne also worked on his Java server, refactoring it for the latest improvements in the specification.

Clemens and his colleague also advanced [ldproxy](https://github.com/interactive-instruments/ldproxy) to implement the latest improvements to the specification.

#### Javascript

The Harris team evolved their node.js STAC implementation to also serve up satellite imagery as WFS 3, reaching a decent implementation in just hours. Tim S wrote a [wfs service](https://github.com/tschaub/wfs) to proxy other services and add
CORS, since not all had it turned on, so that javascript clients could work with it. He then turned his attention to the server side, and built a prototype [node.js wfs](https://github.com/tschaub/pgfs) built on PostGIS. Ahmed also worked on a [WFS test client in node.js](https://github.com/ahmedOpeyemi/wfs3-test-client), that worked against the spec assertions, which proved to be a useful testing engine. 

On the client side, Tim H wrote an [An OpenLayers-based client](https://geekdenz.github.io/wfs-3-hackathon/), and Philippe added WFS3 support to OpenLayers integrated in a [linked data portal](http://demo.highlatitud.es). Can see some cool demos of it working with servers worked on during the hackathon:

* [Example with www.ldproxy.nrw.de](http://demo.highlatitud.es/#/preview?url=https:~2F~2Fwww.ldproxy.nrw.de~2Fkataster~2Fapi~2F%3Ff%3Djson&ann=moz:13c69c6b-d813-407e-8f5b-3489ca0353b4&format=application~2Fvnd.ogc.wfs3)
* [Example with cloudsdi.geo-solutions.it](http://demo.highlatitud.es/#/preview?url=http:~2F~2Fcloudsdi.geo-solutions.it~2Fgeoserver~2Fwfs3~2Fapi&ann=moz:f06b0eac-f5ca-44a9-8a88-b45912258c29&format=application~2Fvnd.ogc.wfs3)
* [Example with wfs3hackathon.ldproxy.net](http://demo.highlatitud.es/#/mosaics/moz:e4c38da6-1b60-4e3e-a8cf-d207322dcd45/annot/moz:ab29e224-4e7b-4667-8fbe-ed63aeb57189?open=true) 

#### STAC

A number of people worked more on STAC topics. Simon, David and Jeff were all working on static catalog topics. Michael and Tim from Harris worked with Josh from Boundless, Kasey and others on figuring out how to align STAC with WFS. And Matt Hanson, Michael, Chris, Simon, Alex and others also pushed forward on the EO profile for STAC.

#### Testing

Chuck investigated abstract tests for WFS, and how to test against OpenAPI, surveying other tools out there. And a few other tools also proved useful for testing, like Ahmed's node.js client, Ian's golang client, and Samweli's qgis work.

### Conclusion

Overall the event was a big success. There were more implementations created in a shorter time frame than imagined, which 
speaks to the simplicity of the spec. Most everyone found it to be a refreshing improvement to the previous OGC specs they'd 
worked with. Various links to the implementations are [listed here](../implementations.md). The specification also improved 
substantially, with over 25 [issues](https://github.com/opengeospatial/WFS_FES/issues/) and pull requests filed, from the 
minor tweaks that make a spec really consistent and usable to 
[one major restructuring](https://github.com/opengeospatial/WFS_FES/issues/64) which will help with name collision 
and just makes things more clear. Since then Clemens and Peter have done a great job closing those out and getting them 
incorporated to the spec. Everyone also was quite excited to be involved early in the specification, giving feedback as its 
being worked on instead of only getting to see it after the final release. Having everything on github makes it much easier
for developers to get involved. And the in person interactions really helped to build a community of collaborators who will
push things forward.

## Raw Notes

This is raw notes dumped from http://board.net/p/wfs3-wrapup

go-wfs / Jivan - go wfs connected with a few different clients, revealed some things about, cleaning those up. Restructuring from previous discussion. Next steps - finish up cleanup revealed by client. Help with one of those clients as a validator (since there are no tests), do some sort of validation. Want to implement the 'search' extension that we talked about with STAC group. Supporting geopackage now, want to support geopackage in the future. Also talking with static stac repos, that a static provider might be interesting to implement. 

Search - a WFS / search. And a /search/stac which would make assumptions about what values you can query. How to report to user what parameters you can query on. Was talk about particular query formats, connect with others. 

**Ian** - WFSCLI - a golang client, driver for it is a WFSCLI, a command line interface to WFS. Client should be able to drive a set of validation operations. Right now using an openapi3 marshall / unmarshall model that works well. Can call 'info' to connet to service and parse the openapi documentation. A rehashing / summary of the operations that are supported. Coll to query feature collections, and can support '-e' for encoding, can do XML. Can get all features. Found a nice http caching library that will cache everything. Uses all http cache controls. But the WFS server testing against doesn't support the cache controls since it's sitting on top a 2.0 wfs that doesn't know the cache. Testing against cubewerx server. Doesn't have all the openapi schemas, but Ian could patch in some of the schemas that weren't there and get it to all work. Solid foundation. CLI feels like a curl wrapper - actually does a bit more, spec validation, crawling validation. Library could be used to do command completion. 

**Peter** - Implemented new paths for WFS. And verified post to collection URI. 

**Tim (NZ)** - Basic OpenLayers client. Showing map of ft. collins. Get feature information, made dynamically from the capabilities document of WFS 3. Link to the data, can click on one of those and it will render features on the client. Accessing the cubewerx serving. Parsing XML on the client. Decided not to use native xml parsing, but using XMLQuery, simliar to Jquery. Not fully featured but works. Had good learning experience, good catching up with people. 

**Matt Perry & python group** - Tom Kralidis and Angelos have been doing lots of code remotely, not just people here. Swagger generated API with GET calls. Has an observations features. API has information. Different data providers - CSV files just to show it, GeoJSON. Are some technical problems on ID's - on the WFS vs data uploaded / queried. Has startIndex and count, result type to manipulate it. Discussion on updates. Could someone update just a segment of the coastline. Create a placeholder transactional issue. There are links to codebase and live server in the 'implementation' folder.

**Ryan** - Nothing too exciting to show. Able to stand up a simple WFS server on top of an existing Asset catalog. Minor exception it's not up to spec with changes from yesterday. Want to flesh out search capability, right now it's just minimal binding box. Maybe time based queries. 

**Simon** - Was working on STAC stuff, getting static catalogs going.

**Jeff** - WOrking on DG stac definition, working on visualizations for static catalogs.

**Michael** - SHowing a STAC search, with bbox and a speculative metadata filter. Get back a GeoJSON feature collection. It is STAC compliant, includes core properties plus some extended properties, and links / assets. And can look at the same thing deployed as WFS 3. Overview of discussion of making STAC a profile of WFS. Started with WFS with the new 'collections' stuff. Added a STAC/ endpoint on top of a search/ endpoint. Talked through details on parameters of dynamic queries. Discussion - one thing that would impact is changing 'count' to 'limit'. Limit is semantically a bit closer to the behaviour. Will be a new issue opened up, and likely will change that. startIndex, resultType and f are already gone. And there are issues for time. 'sort' would be a good eventually WFS extension.

**Tim Schaub** - Started out implementing a little client, normalizing some of the differences between server implementations out there. Have a commandline utility that can provide a little proxy for remote sources that don't support cors. Can list collections and render the services. Taking a bit of time to get features - 25 second response times. Noticed differences  - collectionId vs name. Sometimes extent is a different state. Instead of papering over all the differences decided to shift gears and work on another server implementation. Postgresql backed WFS3 instance. Can start it up with any postgres connection string. Makes a service on port 5000. Ability to create a new collection. Implementation does not yet have links or extent. Can post data to Items. Want to start building clients that work with new path structure. Post data in test directory and then query that data. Not yet query or pagination, but have something to quickly iterate on. Will add links in 'implementations'

**Matt Hanson** - Today primary on STAC discussions. Sorted out earth observation extension. Have been working on something called sat-api, under sat-utils github organization. Completely AWS infrastructure using elastic search / lambda / api gateway. Ingest from S3 files, eventually SNS or stac static files. Can ingest 120k records per hour. Will be updating it with stuff we talked about today, can check out soon. Will post on stac gitter.

**Wes** - at github.com/boundlessgeo/wt - focusing on transactional API based on discussion from yesterday for the endpoints. Short term goal is to put it up on lambda, with api gateway to front it, back with aurora or RDS. Docker to file postgresql and pgweb. Basic collection metadata table. Contents table to point at others, like geopackage. Needs to be sql compliant. Haven't yet been doing links. Creating a new collection will create a new table. Through geojson properties in a json column, and geom column gets the geometry. Go json geometry serialization is finnicky, just got polygons working. Hit the items endpoint and spit out values as feature collection - no pagination yet. Did /collections to pull all collections. /schema gives collectionInfo yaml. Is put and delete on collection.

**Janne** - Spent most time refactoring code for java implementation to server. Made adjustments with changes. 

**Konrad** - Day one was less successful, working on a live internal implementation, didn't manage to get it working but learned a lot. But lead to good stuff. No WFS background, not web api background, but were able to make crude WFS server with basic searches, bounding boxes, count. Would like to have a look at the geopython api. Had a look to compare with them, learned from them. Learned a lot. Because we have no background, found it easy to read, easy to work with. Tried to 2.0, wanted to cry. Next steps - will try to continue and learn more about it and web api's generally. Great interest from OS around this, taking part in testbed 14, etc. Hackathon was a great way to make the WFS 3.0 specification. Made a new one so they could learn. But they will try to take it on. Also interested in taking different providers and handle them. 

**Ahmed** - Continued from yesterday, on a client. Goal was to build a node.js client to test conformance to the draft. Write a test case for each requirement for each assertion. Show each assertion and if it passes it or not. Was interesting to see how servers did different exceptions. Can compare against schema. Saw some that did swagger instead of OpenAPI. Was interesting to see how different requirements passed or failed. Thoughts on WFS - flexibility means there are more tests to cover when checking for conformance. Have to check html + json, etc. But compared to 2.0 it was much faster to build out clients. Need more work on the 4xx codes - invalid parameters, etc. But excited about the new spec. Code is in a repo, will share after cleaning up a bit. Runs from commandline. Wrote ffor 4 requirements, and on recommendation. -- there is an issue on http error codes, is still a work in progress. Trying to map exception codes from old spec. And then how to deal with security. And open question with openapi - do you cover security workflow in the openapi. 

**Chuck** - Is half of an abstract test suite out there, time to start spinning some code. 

**Samweli** - Continued from yesterday, working on qgis plugin. Approach of using a server to test requirements, and QGIS is interface that hits that server. Showed server code, with QGIS. Form to put in server URL, and then form to put in results. Testing the requirements, things missing links. Need synchronization between document and server content. Many servers are failing. 

**Peter** - Smorgasboard of stuff. Have a server that implements every version of WFS from 0.0.13, including 2.5 which is dead. Now have a frankenstein implementation doing most of new stuff but not all of it. Has API document, using some vmap data, loaded in to oracle database. Changed to much of the new collection / link structure. Created transaction, post it to the server. Mostly working in XML. Showed various transaction responses. Got the new structure mostly working, but with xml, not json yet. But that will come soon.

**Clemens** - Quick update, colleague Andreas did some changes, added the links that Samweli was missing. Has it on the two different levels, can go to individual features and see the links. Several issues have been fixed that people noticed hitting the server. Also got the conformance endpoint, which is new in the draft. Included in the implementation pages. 

**Even** - GDAL / OGR. Support WFS 3, driver is working as a standalone. Is documentation in html on the GDAL website. Good progress supporting many of the capabilities. Tested with cubewerx, interactive instruments and the python one. Nice break from previous spec. Is nice and easily implementable - 1143 lines of new code. Concerned about the openness for a universal client. Is a tension between universal and specific implementations. 



TODO's: Open issue on transactions - Matt Perry / python, Michael Smith, Peter V and Josh Fix to all post their openapi and services there. 


