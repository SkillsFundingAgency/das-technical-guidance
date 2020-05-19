---
layout: default
title:  "Coding Principles"
area: development
---

# Coding Principles

These principles are stated in no particular order, and are always open to debate. All development is a trade-off between competing pressures, these principles are meant to help you decide which trade-offs are acceptable.

They are guidance, not The Law - there will always be edge cases, but you should expect to be challenged if you go your own way. The principles are to guide future and current development - use your judgement, but in general only rewrite existing code if you really have to.

## General Principles

### 1. Code should be correct, clear, concise - in that order

Correct means provably correct - with tests. All fixes & new features should include tests to prevent regressions.
Choose clarity over cleverness.
* Don’t Repeat Yourself - The ‘[Rule of Three](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming))’ is a good approach to managing duplication. 
* Less code is usually better, but not at the expense of clarity - Clean Coding techniques can be used to ensure the code remains correct, clear and concise.
* Leave things better than you found them - boyscout the code
* Follow [SOLID principles](https://en.wikipedia.org/wiki/SOLID). This will make code more understandable and easier to maintain

### 2. Optimize for change
Focus on making your code easy to change rather than attempting to predict what changes will be required.

### 3. Early optimisation is overkill
Don’t over-engineer or prematurely optimize and follow the [principle of Least Surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment)  For instance:
* Choose process concurrency over threading & let the O/S handle it, unless there is good reason.
* When you do use threading, use language abstractions to help. 
* Handle exceptions at the app level, no lower.
* Don't roll you own crypto.
* Choose clarity over performance, except when there is a serious performance issue that needs to be addressed.

### 4. Everything fails, all of the time.
Accept this and [code defensively](https://en.wikipedia.org/wiki/Defensive_programming) when calling other services.
Every HTTP call could error or hang, every message could deadletter - handle failures appropriately and fail fast. Don’t let long-running external calls impact your user experience.

### 5. Show, don't tell
If you have to explain how your code works, then your code is not clear enough.
Comments are for explaining <strong>why</strong> something is needed, not how it works.
Commit messages should follow [GDS guidance](https://www.gov.uk/service-manual/technology/maintaining-version-control-in-coding#writing-commit-messages)
No-one cares how clever you are - it’s far more important to work well with your team
APIs are interfaces too - Like any other interface, APIs need designing and iterating for usability

### 6. Think smaller
Stick to the Single Responsibility Principle - keep views, controllers and model classes as simple as possible. Keep methods short. (Concepts and patterns which may help with this: Null Object pattern, Facade pattern, Form Objects, Sandi Metz’s “[Rules for Developers](https://robots.thoughtbot.com/sandi-metz-rules-for-developers)”)
A solution composed of many small simple things is usually better than one big complex thing.

### 7. Names have power. Use them wisely.
Don’t be cute or jokey when naming things
Names convey meaning - well-named functions & variables can remove the need for a comment
Avoid meaningless names like ‘obj’, ‘result’, ‘foo’.
Use single-letter variables only where the letter represents a well-known mathematical property (e.g. e = mc^2), or where their meaning is otherwise clear.

See [Naming things]({{ 'standards/naming-things' | relative_url  }})

### 8. Composition over inheritance
It’s tempting to build an inheritance tree of objects extending others and redefining methods where needed - but that often just creates tech debt for the future. Choose ‘has-a’ relationships over ‘is-a’ - e.g. a Car has-a Motor, rather than Car is-a MotorVehicle

### 9. Any attempt to predict the future is likely to be wrong
This includes estimates of work - if they are to be used for assigning budget or predicting delivery dates, they should always come with a level of confidence, or a best/worst case range (e.g. “between x and y days” or “maybe x days, but I'm only 50% confident of that”)
The larger the chunk of work you’re estimating, the more inaccurate you will be - so if it doesn’t fit into a single sprint, break it down until it does

### 10. Use Test Driven Development
Use [Test-driven Development](https://en.wikipedia.org/wiki/Test-driven_development) or [Behaviour Driven Development (BDD)](http://dannorth.net/introducing-bdd/) principles. It ensures that before you write your code that you have success criteria, and that your code is testable. It gives developers confidence that the code they have written works and the tests will give context that otherwise would be missing, this is especially valuable when the original developers have left the project.

### 11. Create a useful README
Each project should enable new users to get up-to-speed as quickly as possible. A comprehensive README should explain how a project should be set up, configured and run as well as give a background of the goals driving it. Rather than being a static document the README should evolve as the project evolves.

## C#-Specific Principles

### 1. Follow the Microsoft coding standards
The Microsoft developed [Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions) were  developed to give a consistent look and feel to C# code so that readers can focus on the content and not the layout. This can help reduce the cognitive over-head and enable readers to understand the code more quickly based on their previous experience.