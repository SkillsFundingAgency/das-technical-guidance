---
layout: default
---

# Apprenticeship Service Technical Guidance

This site documents the technical standards and guidance that we expect teams working
within the Apprenticeship Service to follow when building digital services.

It complements the [Service Manual](https://www.gov.uk/service-manual) and its
[Technology section](https://www.gov.uk/service-manual/technology),
which covers service design more broadly.

It is inspired by the [GDS Way](https://gds-way.cloudapps.digital) and the
[Ministry of Justice Technical Guidance](https://ministryofjustice.github.io/technical-guidance/#moj-technical-guidance) and also the wider [DfE Dgital Technical Guidance](https://dfe-digital.github.io/technical-guidance/#dfe-digital-technical-guidance)

## Standards

{% assign standards = site.pages
  | where: "standard", true %}

{% for standard in standards %}
- [{{ standard.title }}]({{ standard.url | relative_url }})
{% endfor %}

## Principles

{% assign principles = site.pages
  | where: "principle", true %}

{% for principle in principles %}
- [{{ principle.title }}]({{ principle.url | relative_url }})
{% endfor %}
