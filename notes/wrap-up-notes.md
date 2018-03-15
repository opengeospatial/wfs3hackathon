This is raw notes dumped from http://board.net/p/wfs3-wrapup

**TODO: Clean up notes and write a summary**


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


--
Collaborate seamlessly on documents! This pad text is synchronized as you type, so that everyone viewing this page sees the same text. 
Create your own board and a (secret) name for it here: http://board.net This service is provided on fair-use with open source technology by fairkom. 
Consider a donation in Euro or FairCoin https://www.fairkom.eu/en/sponsoring#Donations for disk space and new features. Virtual hug guaranteed! 
