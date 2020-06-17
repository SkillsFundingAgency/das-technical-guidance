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

* When an application is undergoing significant development
* When there is a team in place to support testing of the upgrade
* When the new version of the framework is no longer in preview

### When not to upgrade

* When the new framework version is not covered by Long Term Support. Details of the versions covered by LTS can be found on the [Microsoft website](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)
* When the application is in the maintenance phase of its life-cycle, or when changes to it are very minor and infrequent
* When the application is due to be decommissioned

### Upgrade process

* Engage with DevOps to discuss the upgrade. The first time that a new version is used there may be additional work  required by the DevOps team to upgrade build servers for example that will need to be planned into their workload.
* Agree the extra work to upgrade with your Delivery Team. If they are not supportive ask them to speak to the Developer Clan Lead to discuss their objections. It may then be raised with the Quality Guild to gain wider opinions if necessary.
* Upgrade the solution
* Liase with Dev Ops to undertake any work required on the build/release pipelines
* Thoroughly test the solution in your local environment, ensuring all unit tests and any integration tests pass
* Ensure that the solution is thoroughly regression tested

### Framework replacements

If an application is currently using the full version of the .NET framework the recommendation is that the application is not converted to a dotnetcore app unless it is being rewritten.
