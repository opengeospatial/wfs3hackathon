This is raw notes dumped from http://board.net/p/wfs3-intros

**TODO: Summarize and clean up formatting**


Scott: Overview of logistics. Different event for OGC, not requiring anyone to sign anything. But if you want to make substantial contributions to the spec get in touch with him.

Peter: Welcome to everyone. Developer focused event, we want people to code.

Chris: STAC overview, how it came to be 

Clemens: Overview of agenda, will do a deeper dive of the spec, then participant introductions. Then forming of groups. Dedicated time to work after lunch. .

Gitter used for chat & communication

### Overview of specification

WFS group has been working for some time on the revision. 1 year ago decided to look in to running things differently. Github repo at https://github.com/opengeospatial/WFS_FES

Trying to document everything there.

Behind the change: Move to more developer driven process. A more open and transparent process (public github), has been working great. Have been getting more comments from non-ogc members than OGC members. Was important for advancing discussion within ogc. There is activity of joint group between OGC and W3C, with 'spatial data on the web best practices group'. From technical point of view is mostly translating best practices - https://www.w3.org/TR/sdw-bp/ 

There is also a more general 'data on the web' best practices from w3c, which has been driving (link?)

OpenAPI 3.0 has also been driving things, was released last year, first truly open version of specification. Was driving point for WFS 3, to move away from legacy. Have a fresh start. Overview section on github, with key changes from previous WFS. One is clear and obvious - be consistent with web architecture - http / https, don't just use them as tunnels. 

Removed dependencies, mandatory dependencies of things that changed more quickly. In older version there was a strong connection to XML. Moving away means changing on all fronts. So no required encodings. Have recommendations for HTML and JSON. But in 5 years it may be new preferences, so are isolating that.

Same thing is true with OpenAPI. Draft version we have now says you have to have an API definition. It has rules for using OpenAPI, but doesn't force it - we don't want to stay tied to 3.0 when in 2 years everyone is on 5.0 (or graphql, etc). Minimize the things created in OGC and that are OGC specific. Move away from 'GetCapabilities' as we have a general IT standard with OpenAPI. Minimize the things we 'invent' in the OGC specs.

*Modularization* - 2 aspects: If someone wants to implement something with WFS 2.0 right now you have to read a lot of stuff. Filter plus hundreds of pages of WFS. So we've started with a core, the really useful core. Move more towards building blocks that you can use in your geospatial data API. Idea is that in the end there will be data API <missed...>

*Schemas* - current version requires that you have schemas, you need to have them. Communities will still do this, but in the core we don't really want to do that. But no need to define a schema for the data. 

*Security* - Was a practical issue with WFS and other standards - security has been an afterthought. We've not yet spent a lot of time thinking about it. Hoping that OpenAPI will give us that. But we need to spend more time and experimentation on.

These are main drivers. But we keep the name WFS 3.0 for now because we want to support the same use cases. Make it easier for others to work with it. Hope is you can develop a generic WFS client that can talk to multiple of the WFS's that implement that spec. But also hope (and a question) of how can someone hit a data api that implements this but doesn't have to read the WFS spec just to get data. May read user guide, but it shouldn't be big hurdle in the beginning. Make it work in a development environment. Make it work in the OGC development process. Have been active in the last month, november to now, in improving the core spec. Hope to get something more or less 'good' out this month, with input from work at wfs hackathon. Do have some experience, some implementations - have been working for more than a year. Once we have that draft will go through the regular OGC standardization process, with internal reviews by architecture board, public request for comments. Sufficient implementation & evidence feedback. Will try to do test engines before final stamp. Goal is to have the tooling available before we put the stamp on it. Includes test engines, and other tools with a broader perspective. Is a slight change in the OGC process. It's been that when the group has worked for awhile they'd move as quickly as possible through the standardization process. 

Not just the OGC process. ISO also wants to make the next version an ISO standard. 

Other thing to bring up is the OGC testbed. Testbeds are part of the 'innovation program', where OGC members come together and develop solutions, work in collaborative way. Has 3 aspects on WFS 3.0. One is testing implementations, in conjunction with security & oauth 2. Will start in April. Another activity is complex feature handling, 3d solids, complex property structure, complex queries on those features - using building models and similar data. And there is WFS 3.0 compliance tests. People can get involved in Testbed 14 as an in-kind participant. Scott can help.

Extensions - there's a lot in WFS 2.x that can be forward ported. And hope is that lots of people can make extensions in their own environment. Those don't need to become official extensions, but should ideally inform the core specification. 

Latest version is up, with some fixes from Tim Schuab, made over the week. There is also links to draft implementations. 

Question - the spec is in draft, it's going to change in time. In these 2 days we will make clients. How do we know what changes happen? Is there a change log? Way to get notified? Github releases? Wanted to make a version this week. The document has a changelog, but it's at the end of the document. Can see all the changes, links to github issues / pull requests. 

=== Participant introductions

*Scott Simmons* - Standards lead of OGC, took over job in 2015, first thing took to board of directors is having implementor friendly standards. OGC procedures have ruled things. Very linear process to accept new standards. The rules are actually open, not as set as people thought. Have tried to do things as new as possible. WFS 3 is most out there attempt, not make a legal document, make something in api that people can code against it. Bring to Scott all opinions good / bad about the process - he has thick skin. Give Scott ideas. Scott will be in and out, but 

* Peter Vretanos* - CTO at cubewerx, but writes code every day. 

*Jivan* - Been working with a couple geospatial projects in django / pyhton. But now go. Tegola - tile server, with data for geopackage. Brought to this a basic golang implemenation of a WFS 3 server with filters. Rough around the edges. Pitch to golang devs, please help out. Spec - would help if there are spec clients. Right now the spec is open, maybe a little too open. Is not clear if what has happened in implementation if what has been done is acceptable to the spec or not. WOuld like to see spec clients, other ways of testing. 

*Samweli* - From Dar es Salaam, Tanzania. Consultant to worldbank. Been a QGIS developer, new to WFS 3. Hope to help others and possibly adapt a client in the hackathon.

* Jorge* - From Geocat in the netherlands. Came here since we have GeoNetwork, are interested in the STAC. Background is mainly python, working in the geopython group Pywps. Background is rest / flask / python code. Working remotely with Tom Kralidis, releasing a pygeo. 

* Mark Romero* WOrk for esri, local. Background in imagery, managing collections of image services, anything that comes off a sensor, help customers use and integrate with GIS. Background is imagery + GIS, helping customers deploy an image server. Thrown in lap recently, mostly interested in STAC. 

* David Hemphill* - Company with a network of independent consultatns. Work right now using STAC with a serverless / lambda architecture. Exercising stac to discover what's on S3 with a web client. Is a huge part of my interest. Published a javascript library / stac browser to look. Using it on a project. If anyone interested in doing javascript work help out, don't be intimidated.

*Michael Smith* Chief architecture for commercial geoproducts for Harris. Excited about modernization of OGC specs and standards, could be a pivitol event. Exctied about STAC, have implemented a STAC server. I think WFS + STAC core is pretty close. Was able to convert STAC to WFS in 3 hours of work.

*Chuck Heazal* - WISC enterprises. Support government agencies + OGC. Done firmware. Big interests today - testing, support for CITE, making compliance tests. Presentation has some thoughts, would like feedback. There is a branch of CITE for openapi. Also a security geek. What openapi allows for security is insufficient. Is discussion in OpenAPI group. If we make code that can work. And we can give feedback to openapi group.

*Matt Perry* - Work for mapbox, live in ft. collins. Doing imagery now, but ten plus years on features. Have always avoided WFS 2 as we needed status codes, http. But psyched on WFS 3. Interested in seeing spec, python.

*Norman Barker* - Mapbox, observing

*Tim Schaub* - Haven't been working with OGC specs since joining planet. But have been pleasantly surprised on the core of WFS. Have done work against WFS servers through various versions, implemented clients, primarily in openlayers. Have been involved in GeoJSON as community standard and IETF standard process. Looking forward to working on browser based clients. Particular interest in filtering and transactions / editing. How those might be specified in wfs 3.

*Ahmed* Ehealth africa. Making GIS clients supporting health in central africa region. How can we use our clients with new specification. We pride ourselves on rate we get clients out fast. Helping in the field requires fast response. Looking at WFS 3 see how spec helps us get products out - clients running in browser and mobile. Looking to make test clients.

*Wes* - Work at boundless geo. Have done WFS ios clients. Do Go, Closure, done java / android development. Looking to do some web server stuff, cloud hosted in Go. 

*Ryan* - Pixia corp. Interest is from a server standpoint. Work with OGC services we develop on our data. Relatively new to geospatial realm. Looking to learn. We are invested in STAC, take in some of that. Potentially work on a server on top of our STAC implementation.

*Tim* - From germany, now in new zealand. Landcare research. Been in geospatial world since 2010. Interest in WFS is trying to follow standards at landcare, so we can federate data around the world, have better science collaboration with everyone. Particularly with soil science. Interested in client side development - js + typescript. But also serverside, learned about postgis / postgres, can help out with that, or developing clients for the browser.

*Paul* - With USGS, national geospatial program. We're a sponsor, tapped locally. We publish lots of data and consume a lot of data. Use OGC standards and support concepts of interoperability. 

*Ian Schnieder* - From ft. collins. Used to work in building C in USGS. Worked on geoserver and WFS parsing. Have taken an arc away from all those standards. But want to contribute to the process what was painful in early implementation. And what was in WFS 3 is intriguiing. Also golang, interested in clients and test suites alongside that.

*Clemens* - Interactive instruments. Not as long involved in OGC as Peter, but almost. Have a reference implementation of current WFS version. Have been driving that in another direction. 2+ years working on software that is open source - ldproxy, link in implementation page. Is a proxy on top of classic WFS's. Colleague is doing remote participation from Bonn

*Keiren* - From ordanance survey, they've been shifting to web more. Have done a loose implementation, will look in to getting it up to date.

*Konrad* - Background is ETL / data transformation. Haven't touched web much at all, but are looking for more exposure. May not contribute that much as a developer but I ask awkward questions. How can we implement server or servless in azure. Also interested in test suite.

*Tom Ingold* - WOrk at Boundless. CTO is title but try to write code everyday. Had an OGC portal login for 11 or 12 years, which kinda scares me. Got started through sensor web enablement, working with wisc. Have lot of different interests. Struggle internally to get developers to use OGC specs. Nobody wants to deal with pox bindings. People just do easier GeoJSON. Been tracking WFS3 + STAC. Planet and boundless have a joint customer, have implemented STAC in azure. That GeoServer reads. Going in to production soon. Lots of moving parts, lots of interest. Excited to see interest in modernizing, have OGC move close to as quickly as technology. On OAB at OGC, will try to be the guy on the inside. For this week working on Go WFS3 server. Probably put on to lambda, have http version. Have another boundless dev coming tonight, who is leading stac development. Has grpc + kafka bindings, Josh will talk all about it.

*Jan* - Work for national land survey of finland, national mapping agency. Been working with WFS and WMS and other specs for awhile. Produce and consume those services. Interested in movement towards simpler way to serve our data. Work with java mainly, mainly on the backend side. Have an implementation, it's working, it's fast, but has many features.

*Chris Holmes*, cholmes, background OpenGeo, Planet product stuff, thinking standards at Planet, OGC std denied at Planet that would not like that, so reshaping standards instead. Started STAC, standardized JSON RESTful API. Slide deck on extensions. Make a sample extension would be nice. Static catalog, sticking stuff and links in S3, fast, what would be the equivalent for WFS? Make sure everything going smoothly. Back to coding! (javascript)

*Alex* - At azavea, on raster foundry team. Let people publish satellite data. Did lots of works with WMS / WFS to help local governments publish their local data - zoning, parcel districts. Lots of experience with javascript and front end, can do java / scala.

*Kasey* - Work at Planet. Work on database side of things. Before worked on companies doing search and other things. Worked in Go for 5 years, psyched to help out. Internally we have a feature service. Very STAC-y. Use JSON schema + swagger, with a flat file node that can consume what we think a stac catalog looks. Looking to stay in line with that + WFS go implementations.

*Andrea Aime* - WOrking on geoserver + geotools for past 10 years. Building a geoserver community module of WFS 3. Stand up so people can laugh at lack of knowledge of OpenAPI. I hope that we will get some standard that is easier to explain to people in training materials. Ideal to not explain axis order 3 times a day, but WFS will probably not solve it.

*Angelos* - Vice president of OSGeo. Working on specs, core developer of pycsw. Implemented CSW spec. Working with python, C, C++, Go. Would like to help geopython group to get a WFS implementation. And try to help with golang stuff if I can. Also interested in STAC part of the meeting, will try to help with WFS.

*Samuel?* - Work in africa. Interest in WFS 3 for interoperability. Working on implementation, how to index geospatial datasets.

*Even* - From France, working on GDAL and related (mapserver, qgis). Been involved in GDAL for 10 years. Have implemented WFS clients in gdal, and upgraded QGIS client to work with WFS 1.1 and 2.0, and also MapServer to support WFS 2.0. Topic of interest is to develop a WFS 3 client in GDAL. Also interested in STAC part. WFS3 - would be interested in extension to expose a schema. OGR requires a schema to operate on a layer. So for now will have to hack things a bit. If anyone is interested an extension for schema that would be great.

*Sam* - Work at ehealth africa. Develop WFS 3.0 clients, and technically review the specification. First time working directly with specifications for geospatial components. Keep an eye out for projects to use it. And try out test cases I have.

*Scott Serich* - On OGC staff, in innovation program. Been initiative director for testbed 12 and 13, and will be for 14. And will be thread architect for WFS work. Soon will gather requirements for testbed 15 work - send ideas on what to work on in WFS in the future to him. If interested in inkind contributions to testbed 14 can get in touch with him. Am pleasantly surprised - stunned - on the response to this hackathon. 

*Tom Kralidis* - Only on gitter. 

Cholmes kicks-off Day 1 closing; please have each group post notes


