---
layout: default
title:  "External APIs"
category: api_standards
---

## Special consideration for external APIs

When delivering an external API, some design aspects are worthy of additional consideration vs building a purely internal API.  In the main these are to do with the differences between external and internal API consumers.  Internal consumers are generally well known, trusted consumers.  We can generally speak face to face with internal consumers and as such, we can easily understand their needs, usage scenarios, and talk to them if / when things change.  For external consumers, we have less knowledge and less control.

As such, we should implement the following.

- Authentication (subscription key)
- Quotas and throttling
- Providing a test service (via developer portal)
- providing bulk download of data
- log requests for personal data

_Note._  As discussed earlier in this document, external APIs should be treated as products.  As a result, their delivery should be treated as if it were an assessed GDS delivery.

### Getting a name for your external API

When obtaining a domain name for your new external API, [please follow this guidance](https://www.gov.uk/guidance/get-an-api-domain-on-govuk).
