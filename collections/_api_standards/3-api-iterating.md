---
layout: default
title:  "Iterating your API"
category: api_standards
---

## Iterating your API

In all but the simplest of domains, future changes to your API are inevitable.  Right from the point we deploy our new bright and shiny API, we know before too long we will need to change it.  We will then be faced with all the usual issues about how we manage that change without striking terror into the hearts of our API consumers.  In short, we need to think about how we  manage this change up-front, before we get into problems.  Some standards are provided below (these apply to both inner and outer APIs).

### Don't break it in the first place

Consider applying [Postel's Law](https://michaelfeathers.silvrback.com/the-universality-of-postel-s-law), and...

> Be liberal in what you accept, and conservative in what you send.

By adopting this philosophy (and encouraging consumers to adopt it), you will be more resilient to breaking changes in the first place.  

**As the API provider**, think through your resource definitions.  As previously stated, use domain language and be consistent.  Whilst you want the API to be rich and fully featured, avoid the temptation to publish any resources (or properties of resources) pertaining to concepts which are not 100% concrete (which may later change / be removed).  As soon as you publish a resource definition clients will become dependant on it.  If a published resource contains data which is transient or not thought through, when you decide to remove / change it, it will make a breaking change.  So try and avoid doing it, as _Postel says, be conservative in what you send_.

**As an API consumer**, think about what dependencies you take upon the API, and ensure your code is only dependant on those aspects of the API it actually cares about.  For example, if you consume an API which returns information on locations of courses, and all you need is the post code and course name, then only take a dependency on those items.  If anything gets added or removed outside of those two items, you should continue to work without issue.  Avoid solutions which serialise entire resources into strongly typed classes, when you do not care about the majority of the properties.  As Postel says, _be liberal in what you accept_.

## Versioning your API

Inevitably, at some point you will need to make a change to an API resource which potentially breaks API consumers.  To cope with this, you will need a clear versioning approach.  The versioning approach must be clear from initial launch of the API, and even the first release should have a clear version number, and consumers should specify that version when consuming the API.  If a client does NOT specify a version, you should return `400 - Bad Request` and specify in the response that the version is mandatory in all requests.  If we were to allow consumers to call an API without specifying a version (and thus defaulted to the latest version if one was not specified), we would risk consumers unexpectedly breaking when we deploy a new major version (as they would automatically move to the new version, even though their client code was expecting the previous version).

### Specifying a version

There are multiple ways of specifying versioning, and there is no right or wrong answer.  Common approaches of versioning APIs are given in the table below.

|Versioning approach|Example|Notes|
|---|---|---|
|URI path|`GET /api/v2/users`|Easy to implement, but... implies different resources (as opposed to version of a resource), is more work for client to upgrade, and versions the entire API in one go (rather than offering a more nuanced approach)|
|URI query string|`GET /api/users?v=2`|Does not seem a natural or RESTful way of versioning|
|Custom header|`GET /api/users`<br />`Content-Type: application/json`<br />`X-Version: 2`|Introducing a new header (which is not part of core the HTTP standard) does not seem logical.|
|Media Type|`GET /api/users`<br />`Accept: application/json;version=2`<br /><br />`POST /api/users`<br />`Content-Type: application/json;version=2`<br />`Content-Length:12`<br />`Hello there!`|A core part the HTTP approach, and RESTful in its nature.  This is our preferred approach.  This strategy can make the API harder to consume for simple script clients, but most AS APIs are NOT consumed from simple scripting languages (thus, this is less of an issue).|

### Media Type versioning in .netcore

.netcore provides API versioning out of the box.  Simply add the the [Microsoft.AspNetCore.Mvc.Versioning]( https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Versioning/) package to your API project.  The package supports a variety of versioning strategies, [and support is provided for versioning by media-type](https://github.com/microsoft/aspnet-api-versioning/wiki/Versioning-by-Media-Type).  The .netcore versioning approach can be used to version individual actions or entire controllers.  The approach is suitable for scenarios where version changes are of simple to medium complexity.

In some cases, a new API version will be significantly different to its predecessor, and maintaining the two side-by-side in the same deployed code base may be an issue.  In these cases, it will be necessary to implement an alternative approach, potentially using a policy within APIM to route requests to different deployed versions of the API.  In such cases, the delivery team are advised to liaise with the Architect associated with the project, (or the central Architect group if one is not specifically allocated to the project).  The Architect will help you explore options and will liaise with DevOps and the Quality Guild as appropriate in order to agree an approach.

### Making non-breaking changes to your API

When making changes that do not break existing consumers (e.g. adding a new resource, a new HTTP VERB to a resource, or adding new properties to a resource), it is NOT necessary to increment the version number.  However, for external APIs, it would be useful to add a change log to the developer portal information for the API.

### Consider consumer tests in your pipeline

You should consider engaging with internal API consumers and asking them to write a test to run in your build pipeline.  The focus of the test will be to express their dependency upon your API.  This can act as an early warning system, ensuring that any potential breaking changes are understood early.

### Clear API version deprecation policy

When introducing new API versions, it is important to limit complexity and costs.  To this end we have defined an API version deprecation policy, which defines how long an API version will be available after the release of a new one.  The API deprecation policy for the AS can be described as follows:

> N-1 for 6 months (where N is the current version)

This means that all APIs will support the current API version ongoing, and the previous API version for a period of 6 months following the release of the new API version.

When a new version is released, all existing clients should be notified regarding the availability of the new version, and the deprecation of the previous version.  This should be repeated 4 weeks from the point of decommissioning the older version.