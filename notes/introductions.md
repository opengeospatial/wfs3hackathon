## About

This document is a record of the participant introduction sessions, both remote and in Colorado. 

Realtime notes gathered at http://board.net/p/wfs3-intros and then transferred to here.

## Participants

### Remote
**Even Rouault**: Core GDAL developer, implemented WFS 1.0, 1.1, 2.0 client in GDAL/OGR, upgraded QGIS WFS client to 
support WFS 1.1 and 2.0, and upgraded MapServer WFS client to support WFS 2.0. Topic of interest for this hackaton will be to 
develop an experimental WFS 3.0 client in GDAL/OGR.

**Philippe Duchesne**: Background is 10+ years spent on the implementation of the OGC specs. Experimentation with REST portage
of CSW. For the hackathon he's working on a WFS3 js client integrated in a linked data portal, using so far 
https://www.ldproxy.nrw.de as a test platform.
Looking forward to integrating further features of the spec, in particular those that allow a true linked data approach :
 - support for content-type negotiation using HTTP headers
 - 'Link' HTTP headers that link a feature URL to its collection/service description
 
**Francesco Bartoli**: Core GeoNode developer, has 10+ years understanding of WxS OGC specs while supporting clients mostly with GeoServer installation. Interested to prototype an experimental WFS3 implementation with python in order to become a valid back-end alternative for vector layers in the future of GeoNode. Goal of this hackathon is to develop with the geopython community a common library to manage wfs3 objects which can then be used by any framework.

**Andrea Aime**: Core GeoServer developer, working on GeoServer + GeoTools for last 10+ years. Participated in various OGC protocol implementations as well as CITE compliance efforts.  Topic of interest for this hackaton will be to develop an experimental WFS 3.0 server plugin for GeoServer, building it as a community module.

**Samuel Okoroafor**: Senior GIS Developer @eHealthAfrica, implemented several WFS clients for different projects over the last 5 years. Topic of interest for this hackathon is to adapt existing clients to include WFS3.0 support, to do a test run for the WFS update feature and to provide support to any project implementing a WFS client.

**Angelos Tzotsos**: Core pycsw developer and core GeoNode developer. Participated in OGC CSW 3.0 efforts with the first reference implementation. Interested in implementing WFS 3.0 for GeoNode and STAC for pycsw. Goal of this hackathon is to develop with the geopython community a common library to manage wfs3 objects which can then be used by any framework

### In Ft. Collins

**Scott Simmons** - Standards lead of OGC, took over job in 2015, first thing took to board of directors is having implementor friendly standards. OGC procedures have ruled things. Very linear process to accept new standards. The rules are actually open, not as set as people thought. Have tried to do things as new as possible. WFS 3 is most out there attempt, not make a legal document, make something in api that people can code against it. Bring to Scott all opinions good / bad about the process - he has thick skin. Give Scott ideas. Scott will be in and out, but 

**Peter Vretanos** - CTO at Cubewerx, but writes code every day. Co-author of every version of the WFS specification, and has 
implemented the Cubewerx server for each of them. Also has implemented CSW, and helped write the latest specification.

**Jivan Amara** - Been working with a couple geospatial projects in django / python. But now working in Go. Latest project is 
[Tegola](https://github.com/go-spatial/tegola) - a tile server serving mapbox vector tiles, with data from geopackages. 
Brought to the hackathon a basic golang implemenation of a WFS 3 server with filters. It is rough around the edges.

**Samweli Twesa Mwakisambwe** - From Dar es Salaam, Tanzania. Consultant to the World Bank. QGIS developer who has built a few 
plugins, new to WFS 3. 

**Jorge Samuel Mendes de Jesus** - From Geocat in the netherlands. Works on GeoNetwork, which is starting to get in to imagery search and so are interested in the STAC. Background is mainly python, working in the geopython group Pywps, with lots of experience in rest / flask / python code. Working remotely with Tom Kralidis, releasing a pygeoapi. 

**Mark Romero** - Works for ESRI in Colorado. Background in imagery, managing collections of image services, anything that comes off a sensor, helping customers use and integrate with GIS. 

**David Hemphill** - Has a company with a network of independent consultants. Is doing a project using STAC with a serverless / lambda architecture. Exercising stac to discover what's on S3 with a web client. Published a javascript library / stac browser to look. Using it on a project.

**Michael Smith** - Chief architecture for commercial geoproducts for Harris. He is excited about modernization of OGC specs and standards, and believes it could be a pivitol event. Have implemented a STAC server, and interested in aligning it with WFS. Was able to convert STAC to WFS in 3 hours of work.

**Chuck Heazal** - WISC enterprises. Support government agencies + OGC. Done firmware. Working on testing, support for CITE, making compliance tests. [Presentation](intro-slides/Hackathon-intro-cheazel.pdf) has some thoughts, would like feedback. There is a branch of CITE for openapi. Also a security geek, and working to figure out how to handle OpenAPI with security.

**Matt Perry** - Works for MapBox, lives in ft. collins. Doing imagery now, but has over ten years of experience with features. Have always avoided WFS 2 in his work as they needed status codes and http. But is excited about WFS 3, and 
trying to implement it with Python.

**Norman Barker** - With MapBox, coming to observe and see how the spec can be used.

**Tim Schaub** - Planet, but haven't been working with OGC specs since joining planet. He has been pleasantly surprised on the core of WFS. Have done work against WFS servers through various versions, implemented clients, primarily in openlayers. Have been involved in GeoJSON as community standard and IETF standard process. Looking forward to working on browser based clients. Particular interest in filtering and transactions / editing. How those might be specified in wfs 3.

**Ahmed Abdul-Majeed Opeyemi** With [ehealth africa](https://www.ehealthafrica.org/). Making GIS clients supporting health in central africa region. What to figure out how they can use their clients with new specification. We pride ourselves on rate we get clients out fast. Helping in the field requires fast response. Looking at WFS 3 see how spec helps us get products out - clients running in browser and mobile. Looking to make test clients.

**Wes Richardet** - Works at Boundless geo. Built a WFS iOS client. Codes in Go and Closure, has done java / android development. Looking to do some web server stuff, cloud hosted in Go. 

**Ryan Kroiss** - Pixia corp. Interest is from a server standpoint. Pixia works with OGC services (primarily WMS / WCS) .Relatively new to geospatial realm. Pixia has built an internal catalog, looking to leverage STAC. 

**Tim Hinnerk Heuer** - From germany, now in new zealand, working at Landcare research. Been in the geospatial world since 2010. His interest is in WFS, as landcare is trying to follow standards, so they can federate data around the world, have better science collaboration with everyone, particularly with soil science. Interested in client side development - js + typescript. But also serverside, learned about postgis / postgres, can help out with that, or developing clients for the browser.

**Paul Wiese** - With USGS, national geospatial program. USGS is the main sponsor, so they wanted to have some local presence. USGS publishes lots of data and consume a lot of data, and uses OGC standards and supports concepts of interoperability. 

**Ian Schnieder** - From ft. collins. Used to work in building C in USGS. He worked on geoserver and WFS parsing, but has taken an arc away from all those standards. He hopes to contribute to the process what was painful in early implementation. And what was in WFS 3 is intriguiing. Will be coding in golang, interested in clients and test suites alongside that.

**Clemens Portele** - Interactive instruments. Not as long involved in OGC as Peter, but almost. Have a reference implementation of current WFS version, and has been working on driving WFS in a more web-focused direction. 2+ years working on software that is open source - ldproxy, link in implementation page. Is a proxy on top of classic WFS's. Colleague is doing remote participation from Bonn

**Kieran Ross** - From ordanance survey, they've been shifting to web more. Have done a loose implementation, will look in to getting it up to date.

**Konrad Korczynski** - Background is ETL / data transformation at Ordnance Survey. Haven't touched web much at all, but are looking for more exposure. May not contribute that much as a developer but he is good at asking awkward questions about new technology. Looking to implement a server or a serverless approach in azure. Also interested in test suite.

**Tom Ingold** - Works at Boundless. CTO is title but try to write code everyday. Has had an OGC portal login for 12 years, got started through sensor web enablement, working with WISC. He struggles internally to get developers to use OGC specs. Nobody wants to deal with pox bindings, they'll just throw something together with JSON. He has been tracking WFS3 + STAC, and Boundless implemented STAC in azure, with GeoServer able to read it. On OAB at OGC, will try to be the guy on the inside. For this week working on Go WFS3 server. 

**Janne Heikkilä** - Work for national land survey of finland, national mapping agency. Been working with WFS and WMS and other specs for awhile, both producing and consuming those services. Interested in movement towards simpler way to serve our data. Work with java mainly, mainly on the backend side. Have an implementation, it's working, it's fast, but does not have many features.

**Chris Holmes** - with Planet and Radiant.Earth, background in OpenGeo, and has been doing Planet product stuff, thinking standards at Planet. Started STAC, standardized JSON RESTful API. He put together a [slide deck on extensions](Extensions_Thoughts_cholmes.pdf). Also thinking about static catalog, sticking stuff and links in S3, fast, what would be the equivalent for WFS? 

**Alex Kaminsky** - At Azavea, on raster foundry team. RasterFoundry lets people publish satellite data. He has done lots of works with WMS / WFS to help local governments publish their local data - zoning, parcel districts. Lots of experience with javascript and front end, can do java / scala.

**Kasey Kirkham** - Works at Planet, on the database side of things. Before worked on companies doing search and other things. Worked in Go for 5 years, psyched to help out. Internally at Planet is working on a feature service which is very STAC-y. It uses JSON schema + swagger, with a flat file node that can consume what we think a stac catalog looks. Looking to stay in line with that + WFS go implementations.

**Scott Serich** - On OGC staff, in innovation program. Testbed 14 Initiative Director: short-term goal is to use the momentum from the hackathon to accelerate the WFS 3.0 work in Testbed 14 and avoid as much duplication of effort as possible; long-term goal is to use lessons learned from this effort to inform future OGC Innovation Program initiatives that might adopt a similar "implementation-first" approach to advancing the OGC standards baseline. If interested in inkind contributions to testbed 14 can get in touch with him. He was pleasantly surprised - stunned - on the response to this hackathon. 

**Tom Kralidis** - Lots of experience with OGC specs, wrote pycsw. Recently has done a go implementation of STAC, and is working on pygeoapi with others.

