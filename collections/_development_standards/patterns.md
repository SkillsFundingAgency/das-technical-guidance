---
layout: default
title:  "Patterns"
category: development_standards
---

## Development Patterns

Below are described the major engineering patterns currently in-use across the Service. There is no definitive list as it is understood that patterns should be used when and where appropriate.

### Orchestrator

As controllers age they are asked to do more and more work which can result in serious bloat. We want to keep our controllers focused on what they should be doing such as handling requests, invoking business rules and returning responses. So to keep them light we need to hand-off any other work that may end up in a controller out to somewhere else and the Orchestrator can be used to fill this need. 

The use of Orchestrators can also make a codebase more testable by moving logic and flow out of controllers and their tight coupling to the runtime.

![Orchestrator Overview](./images/OrchestratorOverview.png)

* [simplify-your-architecture-using-the-orchestrator-pattern](http://www.jamiemaguire.net/index.php/2017/05/06/simplify-your-architecture-using-the-orchestrator-pattern/)
* [orchestrator-pattern](http://www.michaeltaylorp3.net/orchestrator-pattern/)
* [never-mind-the-controller-here-is-the-orchestrator](https://www.simple-talk.com/dotnet/asp-net/never-mind-the-controller-here-is-the-orchestrator/)
  

### Command Query Responsibility Segregation (CQRS)

The Command and Query Responsibility Segregation (CQRS) pattern separates read and update operations for a data store. This segregation can allow us to maximize an applications performance, improve its scalability, and simplify its security model.

Performance is improved by separating the read and write operations within the application. A read operation may have a significantly different profile to an write operation. Separating then means that each can focus on what it needs, for instance there may be properties of the data that must be updated for a successful write operation but which are not needed when reading the data.

Data contention can be reduced by removing the times that reads and writes are accessing the same data at the same time. For instance writes may be placed on a queue to be actioned for asynchronous processing and you may separate out the read data store from the write store.

Securing a task based write operation such as 'Book Ticket' may be easier than choosing which individuals properties of a data representation can be updated in a more traditional model.

* Commands and used to update data and should be task based not data centric ('Book Room' rather than 'set ReservationStatus to Reserved')
* Queries used to read data should never be used to update it, contain domain logic and should only return a DTO.
* Commands and Queries should not depend on each other. If there is a need to share functionality or data the logic should be moved into a new shared Application Service.

![CQRS](./images/cqrs.png)

Another positive side-effects of using CQRS is that there are naturally less merging issues when working in a team as the codebase is broken into smaller, more cohesive chunks.

* [CQRS - Microsoft](https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs)
* [CQRS - Martin Fowler](https://martinfowler.com/bliki/CQRS.html)

### Mediator

With the mediator pattern, communication between objects is encapsulated within a mediator object and do not communicate directly with each other, but instead communicate through the mediator. This reduces the dependencies between communicating objects and reduces coupling.

`How do Mediator and Orchestrator work together and also there's this:` [mediatr-didnt-run-over-dog.html](http://scotthannen.org/blog/2020/06/20/mediatr-didnt-run-over-dog.html)

* [simplifying-development-and-separating-concerns-with-mediatr](https://blogs.msdn.microsoft.com/cdndevs/2016/01/26/simplifying-development-and-separating-concerns-with-mediatr/)
* [thin-controllers-cqrs-mediatr](https://codeopinion.com/thin-controllers-cqrs-mediatr/)
* [simplify-your-controllers-with-the-command-pattern-and-mediatr](https://jonhilton.net/2016/06/06/simplify-your-controllers-with-the-command-pattern-and-mediatr/)


