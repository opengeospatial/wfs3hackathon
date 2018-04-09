# WFS 3.0 Hackathon

The Open Geospatial Consortium (OGC) has organized a Hackathon on 6 and 7 March 2018 in Fort Collins, CO, USA at the [USGS Powell Center](https://powellcenter.usgs.gov/) to capture developer insight into the draft standard for Web Feature Service (WFS), version 3.0. This draft standard is evolving in a quite unique fashion with respect to typical standard development and features OpenAPI / Swagger definition of the key service elements. This new approach to the development of WFS 3.0 is based on ideas generated from the [OGC/W3C Spatial Data Working Group on the Web Best Practices](https://www.w3.org/TR/sdw-bp/), the [OGC Geospatial API White Paper](http://docs.opengeospatial.org/wp/16-019r4/16-019r4.html), and the FGDC Application Programming Interface (API) assessment. Each of these reports recommended an emphasis on APIs in future OGC standards development including use of tools such as OpenAPI.
 
The WFS 3.0 standard is developed in a public GitHub repository and all drafts and discussions can be found there: [https://github.com/opengeospatial/WFS_FES](https://github.com/opengeospatial/WFS_FES).
 
Scott Simmons, Chair of OGC's Technical Committee, has written a [blog post](http://www.opengeospatial.org/blog/2764) about the event that provides a good summary.

The hackathon was linked to a working meeting of the SpatioTemporal Asset Catalog (STAC) community and many participants attended both events and explored how WFS 3.0 could support STAC and how STAC could build on WFS 3.0. This [blog post](https://medium.com/radiant-earth-insights/progress-on-spatiotemporal-asset-catalogs-in-ft-collins-6298f195bfb2) by Chris Holmes discusses the results of the STAC meeting.
 
The WFS 3.0 Hackathon focussed on the core API that covers the essential characteristics. The goal was to test and improve it based on implementation experience. Several new client and server implementations were created and the existing implementations were improved or adapted to changes discussed at the event.

This repository was used collect and share information during the event. Feel free to browse through the repository. In addition, the [WFS Gitter chat](https://gitter.im/opengeospatial/WFS_FES) was used for discussions, including with the remote participants in Europe, Africa and North America.

Chris Holmes took notes during the plenary sessions:

* [Introduction to the event and WFS 3.0](notes/intro-session-notes.md)
* [Participant introductions](notes/introductions.md)
* [Plenary at the end of day 1](notes/day1-end.md)
* [Wrap-up session on day 2](notes/wrap-up-notes.md)

The wrap-up session was also held as a web-meeting and recorded, the recoding is on YouTube: https://www.youtube.com/watch?v=FbH6TOwst7o

20 new issues were create in the [GitHub repository of the draft standard](https://github.com/opengeospatial/WFS_FES/issues). 13 of these issues have been addressed and resolved in the [draft release of the specification that was published one month later](https://github.com/opengeospatial/WFS_FES/releases/tag/3.0.0-draft.1). The biggest change introduced as a result of the discussion was a change in the [URI path structure of the API](https://github.com/opengeospatial/WFS_FES/issues/64). Most of the remaining open issues will be addressed in extensions to the core API. 

--- 

An OGC Hackathon is a collaborative and inclusive event driven by innovative and rapid programming with minimum process and organization constraints to support the development of new applications and open standards.
