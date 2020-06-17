---
layout: default
title:  "Framework Upgrades"
category: development
---

## Framework Upgrades

There is always the temptation to...

### New solutions

New solutions should always use the latest version of the framework which is in Long Term Support.

### When to upgrade

* As soon as an application is undergoing significant development
* When there is a team in place to support testing of the upgrade
* When the new version of the framework is no longer in preview

### When not to upgrade

* When the new version is not covered by Long Term Support.  Details of the versions covered by LTS can be found on the [Microsoft website](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)
* When the application is dormant or changes are very minor and infrequent
* When the application is due to be decommissioned

### Upgrade process

* Speak to Dev Ops - this first step in the process should always be to engage the Dev Ops team.  If you're the first person to implement the new version then additional work may be required for the Dev Ops team which will need to be planned.
* Agree the work with your PO and DM.  If they aren't supportive then speak to either the Dev Lead, Tech Lead or Quality Guild.
* Upgrade the solution
* Liase with Dev Ops to undertake any work required on the build/release pipelines
* Test thoroughly locally
* Execute thorough regression testing

### Framework replacements

If an application is currently using the full version of the .NET framework the recommendation is that the application is not converted to a dotnetcore app unless it is being rewritten.
