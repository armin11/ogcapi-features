# Web Feature Service 3.0 

This GitHub repository contains the new revision of the [OGC](http://opengeospatial.org)'s
Web Feature Service standard for querying geospatial information on the web. It is a complete
rewrite of previous versions, focusing on a simple RESTful core with JSON and HTML specified
as reusable [OpenAPI](http://openapis.org) components.

## Overview

A Web Feature Service is a standard API that represents collections of geospatial data. 

```
GET /collections
```

Lists the collections of data on the server that can be queried ([7.11](https://rawgit.com/opengeospatial/WFS_FES/master/docs/17-069.html#_feature_collections_metadata)), 
and each describes basic information about the geospatial data collection, like its name and description, as well as the 
spatial and temporal extents of all the data contained

```
GET /collections/{name}/items?bbox=160.6,-55.95,-170,-25.89
```

Requests all the data in the collection that is in New Zealand. The response format (typically HTML or a 
[GeoJSON](http://geojson.org/) feature collection, but extensions can easily supply others) is determined using 
[http content negotiation](https://restfulapi.net/content-negotiation/). Data is returned in pageable chunks, with each 
response containing a `next` link as many collections are quite large. The core spec supports a few basic filters, in 
addition to the `bbox` filter above, with extensions providing more advanced options. 
([7.13](https://rawgit.com/opengeospatial/WFS_FES/master/docs/17-069.html#_feature_collections))

```
GET /collections/{name}/items/{id} 
```

Returns a single geographic 'feature' - a geometry plus attributes representing something in the world - a building, a stream, a county, etc. This provides
a stable, canonical URL to link to.

## Using the standard

A draft of WFS 3.0 is available. It is basically a complete draft:

* [OGC Web Feature Service 3.0 - Part 1: Core](https://rawgit.com/opengeospatial/WFS_FES/master/docs/17-069.html)

Those who want to just see the endpoints and responses can explore the openapi spec on swaggerhub:

* [WFS3 Milestone 1 openapi.yaml](https://app.swaggerhub.com/apis/cholmesgeo/WFS3/M1)

There have been several implementations of the standard, though many are still getting up to compliance with the 
milestone 1 release:

* [Implementations of the draft specification / demo services](implementations.md)


## Communication

Join the [mailing list](https://lists.opengeospatial.org/mailman/listinfo/wfs-fes.swg) or [![chat at https://gitter.im/opengeospatial/WFS_FES](https://badges.gitter.im/opengeospatial/WFS_FES.svg)](https://gitter.im/opengeospatial/WFS_FES?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Most all work on the specification takes place on the repo's [github issues](https://github.com/opengeospatial/WFS_FES/issues), so browse there to get
a good idea of what is happening, as well as past decisions.

## Additional Information

* [Checklist for implementers](guide/conformance_checklist.md)

Also a non-normative document, the "WFS 3.0 Users Guide", is planned.

In addition to feedback from the initial implementations as well as discussions on GitHub and in the OGC/ISO working group, 
the current draft of the Core specification has been tested in a [WFS 3.0 Hackathon](https://github.com/opengeospatial/wfs3hackathon).
The release of a first draft version is planned for April and will be used as input for the [OGC Testbed-14](http://www.opengeospatial.org/projects/initiatives/testbed14) 
and for the next steps in the standardization process in OGC and ISO/TC 211. The open issues that we plan to address in this version
can be seen in the [milestone information](https://github.com/opengeospatial/WFS_FES/milestone/1).

The current expectation is to have a stable version of the Core specification in early 2019. We want to wait for sufficient 
implementation feedback, mature implementations including a test suite, the results of OGC Testbed-14 and experience with 
draft extensions first. 

* [Background of this activity](background.md)
* [The next version of WFS - an overview](overview.md)

## Contributing

The contributor understands that any contributions, if accepted by the OGC Membership and ISO/TC 211, shall be incorporated into 
OGC and ISO/TC 211 Web Feature Service standards documents and that all copyright and intellectual property shall be vested to the OGC.

The WFS/FES Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is
working to do as much work in public as possible.

* [Open issues](https://github.com/opengeospatial/WFS_FES/issues)
* [Proposing changes](https://github.com/opengeospatial/WFS_FES/wiki/Propose-a-change-to-a-draft-of-a-WFS-specification-document)