---
layout: default
title:  "New Solutions"
category: development
---

## New solutions FAQ

Whilst the whole of the Technical Guidance is here to provide you with assistance, below are some key questions that may help you get started on a new solution, or when bringing an existing solution up-to-date)

### 1. Which .Net version should I use?

New solutions should use the latest long-term support (LTS) version available at the time. Any deviation from an LTS version should only be made where a feature is only available in the newer version that is essential to deliver required functionality.

The version used also needs to be supported by our build servers so a check-in with the DevOps team before starting is always useful.

### 2. How do I add analytics?

Do we need to apply analytics to the user journey's and how do we do that?

### 3. How do I add logging?

Adding logging into an application is essential when it comes to supporting it, however what is right in development may become an issue in production. [Ensuring the right configuration is key]({{ 'development_standards/platform-integration#logging-to-redis-and-not-to-file' | relative_url }})

### 4. How do I protect my sensitive settings?

There have been many ways to store sensitive settings in the past, the currently recommended way to do so is by using [the ASP.NET Core data protection stack]({{ 'development_standards/platform-integration#aspnet-core-data-protection' | relative_url }})

### 5. Which storage mechanism should I use?

Azure SQL is the de-facto storage mechanism within the Apprenticeship Service.

However there are scenarios where using unstructured storage is more appropriate, if you think this is the case for your solution you must discuss it with the Architectural and DevOps teams in advance so that the reasoning can be understood and considered against the larger needs of the Service. For instance using semi-structured data can have an impact on other teams and functions such as business reporting.

### 6. How do I report on code quality?

How will you ensure and prove the quality of the code when it comes to handing over to live running?
Adding SonarCloud to your solutions will provide a visual representation of the quality of the codebase and provide a level of confidence to team accepting the code into live running.

### 7. Which authentication mechanism should I use?

There are several authentication mechanisms in-use across the service, these are usually split down by user-group.

|---|---|---|
|Staff IDAMS|Used for internal staff authentication|For instance internal support applications would use this mechanism|
|Provider IDAMS|Used to authenticate training provider users||
|Employer User|Used to authenticate employer users||

### 8. How do I ensure interoperability with other solutions?

It is good to be aware that some solutions may be on older versions of .Netcore or may still be on .Net Framework. This may add work for you to upgrade or conditionally compile older dependencies. This can be especially prevalent with the use of API Client Nuget packages.

### 9. Is that new technology worth it?

We all love new tech but is it too new to have decent support, is there an additional cost involved, do we have the skills to support it once its been built?

If there is something that we want to try out then don't make the decision in isolation, raise it with the other professions first as any decision is likely to impact them as well. The architects, developers, DevOps and testing clans must all be given the chance to have their input. 

New technology also needs to be proven before it is introduced into a Live environment to prevent issues surfacing only when under load, deployed into a complex environment etc... 

The effort required to prove the technology may make it non-viable and although it may not be as exciting using an already proven alternative may be the right choice once all considerations have been taken into account.

### 10. Should I add unit tests?

[Yes, we follow Test Driven Development practices]({{ 'development/coding-principles#10-use-test-driven-development' | relative_url }})

Which framework you use is less important than creating the tests in the first place but you should be using either NUnit or xUnit.

### 11. Should I automate testing?

A comprehensive automation framework has been created [for just this purpose]({{ 'principles/testing.html#test-automation' | relative_url }})

### 12. How should I build my API's?

[By following the comprehensive architectural standards]({{ 'standards/api-standards.html' | relative_url}})

### 13. Which non-functional requirements do I need to know about?

