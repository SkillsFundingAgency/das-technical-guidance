---
layout: default
title:  "Solution Architecture, Structure and Layout"
category: development_standards
---

## Solution Architecture

### Onion Architecture

The [Onion Architecture](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) was proposed by Jeffrey Palermo in 2008 to produce more maintainable applications by emphasizing the separation of concerns throughout a system. Similar to the [Hexagon Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)) it forces the externalization of infrastructure, the use of interfaces for behaviour contracts and forcing dependencies to only "move" in one direction, toward the centre and the Domain Model. In the Onion architecture the edges of the onion are where the most change is likely to happen and where tight coupling would be most difficult to manage. It contains the UI, Tests and Infrastructure. 

![](images/OnionArchitecture.png)

The Onion Architecture is in contrast to a layered architecture where layers are coupled to the one below them and potentially to various infrastructure concerns.

![](images/LayeredArchitecture.png)

Core Concepts:

* It emphasizes the use of interfaces for behaviour contracts, and it forces the externalization of infrastructure
* Helps to decouple system dependencies by stating that all code can depend on layers more central, but code cannot depend on layers further out from the core
* The first layer around the Domain Model is typically where we would find interfaces that provide object saving and retrieving behaviour, called repository interfaces
* Object saving behaviour is *not* in the application core, only the interface is in the application core
* On the edges we see UI, Infrastructure, and Tests

Limitations:

* It is appropriate for long-lived business applications as well as applications with complex behaviour
* Relies heavily on the Dependency Inversion principle

#### References

* [Onion Architecture Part 1](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/)
* [Onion Architecture Part 2](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-2/)
* [Onion Architecture Part 3](https://jeffreypalermo.com/2008/08/the-onion-architecture-part-3/)
* [Onion Architecture Part 4](https://jeffreypalermo.com/2013/08/onion-architecture-part-4-after-four-years/)
* [Example Application](https://bitbucket.org/jeffreypalermo/onion-architecture/src/default/)
* [Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))

### Solution Structure and Layout

One Application project per functional area/Bounded Context

<pre>
Solution  

  Application BoundedContext   

    Commands   

      [Task]

        Command -> POCO class that represents a task that has to be performed such as a user action.     

        CommandHandler -> Takes an instance of a command and does the actual work.     

        Validator -> Simple validator that determines if the command contains valid data.   

    DataEntities   

    Queries    

      [Task]

        Query -> Takes an instance of a Request and returns a Response     

        Request -> POCO class     

        Response -> POCO class   

    ViewData  

    Interfaces -> Interfaces for Infrastructure Sevices like Logging and Email   

    Services -> Internal logic used by multiple Commands/Queries   

    Errors -> Exceptions   

    Mappers -> Internal mapping between DTOs that cross the boundaries of Infrastructure/Application and Application/Domain  

  ApplicationTests   

    CommandHandler   

    QueryHandler  

  Data [There could be many of these]  

  Domain  

  Web   

    Controllers   

    Views   

    ViewModels   

    Orchestrators (1 per Controller)  

  WebTests

    Orchestrators

</pre>