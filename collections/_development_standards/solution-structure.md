---
layout: default
title:  "Solution architecture, structure and layout"
category: development_standards
---

## Solution architecture

### Onion architecture

[Onion Architecture](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) was proposed by Jeffrey Palermo in 2008 to produce more maintainable applications by emphasising the separation of concerns throughout a system. Similar to [Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)), it forces the externalisation of infrastructure, the use of interfaces for behaviour contracts and describing dependencies that only "flow" in one direction: toward the centre and the Domain Model. In onion architecture, the edges of the onion are where the most change is likely to happen and is where the UI, tests and infrastructure is found. 

Onion architecture is in contrast to a layered architecture where layers are coupled to the one below them and potentially to various infrastructure concerns.

#### Core concepts

* It emphasises the use of interfaces for behaviour contracts, and forces the externalisation of infrastructure.
* It helps to decouple system dependencies by stating that all code can depend on layers more central, but code cannot depend on layers further out from the core.
* The first layer around the Domain Model is typically where we would find interfaces that provide object saving and retrieving behaviour, called repository interfaces.
* Object saving behaviour is *not* in the application core. Only the interface is in the application core.
* On the edges we see UI, infrastructure, and tests.

#### Limitations

* It is appropriate for long-lived business applications as well as applications with complex behaviour
* Relies heavily on the Dependency Inversion principle

#### References

* [Onion Architecture Part 1](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/)
* [Onion Architecture Part 2](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-2/)
* [Onion Architecture Part 3](https://jeffreypalermo.com/2008/08/the-onion-architecture-part-3/)
* [Onion Architecture Part 4](https://jeffreypalermo.com/2013/08/onion-architecture-part-4-after-four-years/)
* [Example Application](https://bitbucket.org/jeffreypalermo/onion-architecture/src/default/)
* [Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))

### Solution structure and layout

The intention of this section is to outline preferred naming conventions and usage for the types of projects that might be included in a solution. The goal is to ensure that common patterns are used throughout the service, rather than each team adopting their own standard.

Note that there is no one prescribed structure for any given solution, regardless of the type of solution being worked on. It is intended that teams have the flexibility they need to include the projects that are relevant to them.

#### Solution
Wherever possible, solutions should:
* Adopt the naming convention ```SFA.DAS.{SolutionName}``` (where {SolutionName} is a meaningful name relevant to the piece of work this solution is for).
  * Note that in any of the projects suggested below, the ```*``` in the project name should be the same as the solution name.
* Have a single application (e.g. a website, an API, etc.).
* Have its own repo in GitHub.

Solutions can contain any of the below projects. Only projects that are relevant to the work being completed should be included.

##### API projects
Where you have an API, use these projects to configure your endpoints. The core logic should be in the separate ```Application``` project.
```
SFA.DAS.*.Api
SFA.DAS.*.Api.AcceptanceTests
SFA.DAS.*.Api.UnitTests
```
API projects should contain all of the logic to handle the requests and responses for the included endpoints. This can include:
* Controllers that receive and route requests and return responses.
* Request and response types that will be received or returned by each endpoint.

##### Application projects
Use these projects for your application's core logic as it applies to your domain objects.
```
SFA.DAS.*.Application
SFA.DAS.*.Application.UnitTests
```
The content will vary from one application to the next, but examples of things an application project might include are:
* Calls to repository interfaces in the solution's ```Data``` project.
* CQS calls (where the ```Application``` project replaces separate ```Commands``` and/or ```Queries``` projects).

In onion architecture, the application layer is not responsible for business logic. For example, the application logic may be concerned with retrieving data in a specific use case, but it would not be responsible for modifying that data based on business rules or practices as part of its retrieval.

##### Commands projects
Use these projects for your CQS pattern commands (add/update/delete data).
```
SFA.DAS.*.Commands
SFA.DAS.*.Commands.UnitTests
```
Try to organise your commands in individual folders. Each folder should contain:
* Your command.
* Your handler.
* Your command validator.

##### Data projects
Use this project for classes that implement the repository pattern for data access.
```
SFA.DAS.*.Data
SFA.DAS.*.Data.UnitTests
```
The repository pattern uses abstract methods to access or modify data without having a direct reliance on an actual database. You should create one file per repository, with each file containing all the expected actions that can be performed on that repository.

##### Database projects
Use this project for database scripts (.sql) for things like creating tables and adding indexes for your solution.
```
SFA.DAS.*.Database
```

##### Domain projects
Use this project for your domain objects (models) and interfaces. As the project at the heart of the onion architecture pattern, this should contain all of the enterprise level objects for your solution.
```
SFA.DAS.*.Domain
SFA.DAS.*.Domain.UnitTests
```
Try to organise your models into logical groupings. For example, if you have a number of models related to an 'account', create an account folder and put those models in there, separate from the models used for another element of your application.

This project can also contain interfaces for any methods that may be associated with your models. The implementation of these interfaces will sit in a separate project (e.g. ```Application```).

##### Events projects
Use these projects for any event based logic and associated handlers.
```
SFA.DAS.*.Events
SFA.DAS.*.Events.UnitTests
```
Events will often make calls to repositories in the solution's ```Data``` project, or ```Commands``` or ```Queries``` projects in order to update data when an subscribed event is triggered.

##### Functions projects
Use these projects for Azure functions projects and durable functions. These will contain your orchestrators, triggers and activities.
```
SFA.DAS.*.Functions
SFA.DAS.*.Functions.UnitTests
```

##### Infrastructure projects
Infrastructure can vary wildly from one solution to the next, both in terms of content and scope. Often an infrastructure project will be used to store configuration information.
```
SFA.DAS.*.Infrastructure
SFA.DAS.*.Infrastructure.UnitTests
```
Examples of things infrastructure projects can contain are:
* Clients
* Configuration
* Extensions
* External APIs
* Event listeners
* Helpers
* Repository implementations
* Services

Try to avoid using the infrastructure project as a dumping ground for orphan classes and logic. In onion architecture, infrastructure projects should be used to implement things like the repositories you constructed in other projects. If the code you write forms a core part of your application, it probably belongs in a different project type.

##### Jobs projects
Use these projects for any scheduled tasks that need to run in an environment.
```
SFA.DAS.*.Jobs
SFA.DAS.*.Jobs.UnitTests
```

##### Mock projects
Use these projects to create mock instances for use when testing your applications.
```
SFA.DAS.*.MockServer
```

##### Queries projects
Use these projects for your CQS pattern queries (data retrieval).
```
SFA.DAS.*.Queries
SFA.DAS.*.Queries.UnitTests
```
Try to organise your queries in individual folders. Each folder should contain:
* Your query handler.
* Your query request type.
* Your query response type.

##### Web projects
Web projects are used for applications that have a web-based user interface.
```
SFA.DAS.*.Web
SFA.DAS.*.Web.AcceptanceTests
SFA.DAS.*.Web.UnitTests
```
Web projects should follow the MVC design pattern.

The [das-reservations](https://github.com/SkillsFundingAgency/das-reservations) codebase is a great example of how to structure an Apprenticeship Service codebase
