---
layout: default
title:  "Solution structure and layout"
category: development_standards
---

## Solution structure and layout

### Onion Architecture

* [Onion Architecture - Jeffrey Palermo](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/)

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