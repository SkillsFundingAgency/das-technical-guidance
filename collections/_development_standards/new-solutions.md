---
layout: default
title:  "New Solutions"
category: development
---

## New solutions

Below are some considerations that we should be taking into account when creating new solutions.

### Which .Net version should I use

In the main new solutions should be using the latest long-term support version available at the time. It also needs to be supported by our build servers so a check-in with the DevOps team before starting is always useful.

### Storage mechanisms

Azure SQL or CosmosDB, Is the data likely to be structured or unstructured, will it require fast reads and horizontal scalability?
How will we extract the data out into the DataMart solution?

### Analytics

Do we need to and how will we apply analytics to the user journey's and how do we do that?

### Code quality

How will you ensure and prove the quality of the code when it comes to handing over to live running?
The use of SonarCloud can be of use here as it is a way to visually show that the code you're handing over has a level of quality


### Authentication mechanisms

There are several authentication mechanisms in-use across the service, these are usually split down by user-group.

|---|---|---|
|Staff IDAMS|Used for internal staff authentication|For instance internal support applications would use this mechanism|
|Provider IDAMS|Used to authentication training provider users||
|Employer User|Used to authentication employer users||

### Interoperability with other solutions

It is good to be aware that some solutions may be on older versions of .Netcore or may still be on .Net Framework. This may add work for you to upgrade or conditionally compile the older dependencies. This can be especially prevalent with the use of API Client Nuget packages.

### Is that sparkly new technology worth the learning curve?

We all love new tech but is it too new to have decent support, is there an additional cost involved, do we have the skills to support it once its been built?