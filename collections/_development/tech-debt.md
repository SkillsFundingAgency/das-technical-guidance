---
layout: default
title:  "Technical Debt"
category: development
---

## Technical Debt

[Technical Debt](https://en.wikipedia.org/wiki/Technical_debt) is a concept in software development that reflects the implied cost of additional rework caused by intentionally choosing an easy (limited) solution now instead of using a better approach that would take longer. When this debt is taken on it will likely need paying back at some future point and to be able to effectively manage the debt it is necessary to log and triage it. 

The process of triage should document the causes of the debt and the decisions that were taken to accrue it and by who. The estimated effort that will be required to pay it back and the impact it will have if left in-place will also need to be included.

Debt should go back through the triaging process periodically to ensure it is still correctly categorised.  

### Examples of Debt

* Out of date dependencies
* Hardcoded configuration
* Component has too many responsibilities
* Long running test suite
* Manual deployment task
* Missing documentation
* No admin interface
* Not using lessons learnt since build

### Example consequences of tech debt

* Harder to patch security vulnerabilities
* Harder to implement new features
* Harder to onboard new developers
* Consumes too many compute resources
* Too closely coupled to an architecture
* Causes too many support tickets
* Creates too much chore work
* Difficult to debug issues
* Inconsistent architecture


### Example

> Whitehall has its own upload management system
> 
> **Cause:** Whitehall’s system for handling uploads of PDFs, CSVs and images from publishing users is different to the Asset Manager application used by Specialist Publisher and others. This is due to it being developed in isolation from another system.
> 
> **Consequences:**
> 
> Inconsistent architecture
> Too closely coupled to physical disk
> Causes support tickets due to delay in processing attachments
> Impact of debt: High due to confusion, operational restrictions and support burden.
>
> Effort to pay down: **High** due to the technical effort involved in changing Whitehall to talk to Asset Manager, implementing missing features in Asset Manager and migrating existing assets.
>
> Overall rating: **High**

[The GDS Way - How to track technical debt](https://gds-way.cloudapps.digital/standards/technical-debt.html)