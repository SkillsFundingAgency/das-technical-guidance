---
layout: default
title:  "Aims and Objectives"
category: api_standards
---

## Aims and Objectives

This section sets of the key aims and objectives of the AS in defining API standards.

|Objective   | Solution  | Notes |
|---|---|---|
| Achieve a standard way of designing, building and operating APIs | Define a set of principles, building blocks and standards to ensure new APIs have a standard approach | Thought to be given to updating existing APIs to the new standard |
|Enable the rapid delivery of new _Digital Products_ and services|Use architectural patterns inspired by  [Backends For Frontends](https://samnewman.io/patterns/architectural/bff/), and MASA (Mesh Apps and Services architecture [ref1](https://www.gartner.com/en/documents/3805663), [ref2](https://medium.com/@sreelathas/why-masa-is-the-future-897f470dc399)) to deliver services which can be quickly composed into new _Digital Products_|_Note._ In the AS, the concern is less about different client device types (mobile vs web), and more about different _Digital Products_ sharing common services.|
|Reduce complexity of AS component interoperability |By providing common standards and approaches, there will be a uniform approach to APIs across the AS, making consuming APIs easier||
|Loose coupling / separation of concerns |Domain oriented services will be reusable, composable and resilient to implementation changes.||
|Remove the burden of implementing common cross cutting concerns (e.g. caching, rate limiting, security) in each individual API|Use of the API Gateway pattern and utilisation of an APIM product||
|Ensure APIs are discoverable and documented|Use of a developer portal and standardised documentation using [Open API Specification 3.0](http://spec.openapis.org/oas/v3.0.3).||
|Build APIs design around user needs|Promote a process where APIs are designed as _digital products_, considering the needs of user (_developers_), helping them meet the needs of their end-users||||