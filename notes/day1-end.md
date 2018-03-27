## Overview

The wrap up session at the end of the first day had people go around the room to report what progress they made. There was 
lots of good progress on a number of fronts. A group started a new open source [python server](https://github.com/geopython/pygeoapi), working with people remote and in person. There was a couple Go server efforts, one at https://github.com/go-spatial/go-wfs and the other by Boundless, as well as a Go client started. Others worked in Node.js, tried out QGIS plugins, explored OpenLayers talking to the API, and built a GDAL reader. Overall it was a day of learning, not everyone had visible progress to show, but everyone felt they had a real handle on the specification and had made some progress.

## Raw Notes

This is raw notes dumped from http://board.net/p/wfs3-day1-wrapup


*Peter* - One thing that kept coming up - an extension to get the schemas. Few approaches, one was encode feature schema in openapi document. Clemens looked at and did. Another is hypermedia links to external schemas. Third is external path. Implemented in cubewerx server. Can hit /schema, and /schema/featuretypename. Then had big discussion, clemens pointed issue on github. Slight reorg of path that lets you get schema in a different way, and make all the paths work. Also a github issue for the other topic, of the three sessions. Discussion of how to get schema is still evolving. Bulk of work did today. Didn't touch heterogenous features. Maybe server does synthesized super set. JSON schema can do a one off - union different things. Have dealt before with a super set. Can also just not report the schema, and that's probably ok for heterogeneous questions.

*Tim* - Trying to get insight in to standard and how to deal with it. Basics of getting set up. 

*Jorge* - Team implementing geojson on server. Working WFS 3 server in python. Was originally done against elastic search, working to make it work against GeoJSON. Need to create or update feature ids, when you submit a new feature it may have a different id inside, and an id on the server. Extended code from Tom Kralidis. Could put a ssh to serve it up. There's a mobile hotspot that people can use. 

*David* - Started by looking at two STAC browsers for static catalogs. Adapted to hit dynamic catalogs. In both cases returning an OpenAPI response, just a matter a navigating to that response. Debates on compatibility / merits, why to go down either path. 

Go-WFS WFS Spec - decided we need to be a bit mroe concrete on the core on endpoints where you know you can hit to traverse the data. Talked about an extension that describes how you would hit a WFS 3 service for filtering or querying. 

Kasey - how to pull STAC API work in to WFS. Can we think of STAC as a profile for WFS. What are the core fields, how to do json schema, make things scrapable. 

Ian - Mostly worked on a go-lang client for WFS 3. 2 pieces, a standalone client - give it a url and get collections. Just got listing done. Driver for the client is a command line interface. 

Tim - put together a browser based client, and a command line client that can proxy a service that is not CORS and can work. Opens a browser, shows available collection, loads a page of features and zooms in to those. 

Ahmed - Did some work on WFS client, based on spec document. Way to make sure your server is compliant with the spec. Test servers haven't fully matched results in spec document.

Ryan - good start on WFS server on top of their internal catalog server. Got stuck on an unrelated bug, but made a good start. And good discussion about collections and features and how things fit in to the spec.

Wes - Agreed on WFS 3 canary spec, got metadata query on collections, fetch collections, the schema, and a postgresql table per 
collection (may be good or bad idea). Took a stab at doing a more transactional approach - wanted a way to get data in to it. 
Trying to rework collection -> collectionid -> feature -> featureid so there's not namespace collisions. Way to further 
modularize a second API per collection, pulling that thread seeing how it goes. Changed to items instead of features.

Ordnance Survey (Konrad and Kieran) - Aimed to take on an internal project and try to get it working with WFS. Didn't get 
particularly far in code, but did a lot of interesting discussion and learning about the specs. Lots of learning today, not so 
much coding. Drove good conversations, including the collections. Haven't worked with WFS before, but there was a thing about a 
feature should belong to one collection, which feels like an approach to shape data behind the whole service. Would be good to 
clarifications. Were talking about buildings layer, and then a view of a 'skyscrapers' layer. So a subset of buildings would be 
skyscrapers, and you could expose those as different collections. With filtering could create an adhoc collection, which 
overlaps with other collections. Is there a canonical ID for buildings vs skyscrapers? If you modified through one other url? 
From a feature perspective would say yes. The why? Is it's a hierarchical structure. 

Samweli - Working on QGIS plugin that acts as a client to test any WFS server. Internals QGIS - there is support for testing v 1 and 2. Wanted to make a plugin with a different approach. Make QGIS plugin as a client to a server, working with a Go server. 

