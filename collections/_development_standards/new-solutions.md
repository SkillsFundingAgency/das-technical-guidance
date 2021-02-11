---
layout: default
title:  "New Solutions"
category: development
---

## New solutions

Below are some considerations that we should be taking into account when creating new solutions.

### Which .Net version should I use?

New solutions should use the latest long-term support (LTS) version available at the time. Any deviation from an LTS version should only be made where a feature is only available in the newer version that is essential to deliver required functionality.

The version used also needs to be supported by our build servers so a check-in with the DevOps team before starting is always useful.

### How do I add analytics?

Do we need to apply analytics to the user journey's and how do we do that?

### How do I add logging?

Adding logging into an application is essential when it comes to supporting it, however what is right in development may become an issue in production. [Ensuring the right configuration is key]({{ 'development_standards/platform-integration#logging-to-redis-and-not-to-file' | relative_url }})

### How do I protect my sensitive settings?

There have been many ways to store sensitive settings in the past, the currently recommended way to do so is by using [the ASP.NET Core data protection stack]({{ 'development_standards/platform-integration#aspnet-core-data-protection' | relative_url }})

### Which storage mechanisms?

Azure SQL or CosmosDB, Is the data likely to be structured or unstructured, will it require fast reads and horizontal scalability?
How will we extract the data out into the DataMart solution?

### How do I report on code quality?

How will you ensure and prove the quality of the code when it comes to handing over to live running?
Adding SonarCloud to your solutions will provide a visual representation of the quality the codebase and provide a level of confidence to team accepting the code into live running.

### Which authentication mechanism should I use?

There are several authentication mechanisms in-use across the service, these are usually split down by user-group.

|---|---|---|
|Staff IDAMS|Used for internal staff authentication|For instance internal support applications would use this mechanism|
|Provider IDAMS|Used to authentication training provider users||
|Employer User|Used to authentication employer users||

### Interoperability with other solutions

It is good to be aware that some solutions may be on older versions of .Netcore or may still be on .Net Framework. This may add work for you to upgrade or conditionally compile older dependencies. This can be especially prevalent with the use of API Client Nuget packages.

### Is that sparkly new technology worth it?

We all love new tech but is it too new to have decent support, is there an additional cost involved, do we have the skills to support it once its been built?

Have you considered using already known and in-use alternatives, have you spoken with the right people to fully understand the repercussions?