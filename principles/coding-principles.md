---
layout: default
title:  "Coding Principles"
---

# Coding Principles

These principles are stated in no particular order, and are always open to debate. All development is a trade-off between competing pressures, these principles are meant to help you decide which trade-offs are acceptable.

They are guidance, not The Law - there will always be edge cases, but you should expect to be challenged if you go your own way. The principles are to guide future and current development - use your judgement, but in general only rewrite existing code if you really have to.

## General Principles

### 1. Code should be correct, clear, concise - in that order

Correct means provably correct - with tests. All fixes & new features should include tests to prevent regressions.
Choose clarity over cleverness.
Don’t Repeat Yourself - The ‘[Rule of Three](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming))’ is a good approach to managing duplication. Less code is usually better, but not at the expense of clarity - Clean Coding techniques can be used to ensure the code remains correct, clear and concise.
Leave things better than you found them - Boyscout the code

### 2. Optimize for change
Don’t try to solve every conceivable problem up-front, instead focus on making your code easy to change when needed
Don’t prematurely optimize - choose clarity over performance, unless there is a serious performance issue that needs to be addressed.

### 3. Early optimisation is overkill
Don’t over-engineer. Follow the principle of Least Surprise. Choose process
concurrency over threading & let the O/S handle it, unless there is good reason.
When you do use threading, use language abstractions to help. Don’t roll your
own crypto. Handle exceptions at the app level, no lower.

### 4. Everything fails, all of the time.
Accept this and [code defensively](https://en.wikipedia.org/wiki/Defensive_programming) when calling other services.
Every HTTP call could error or hang - handle failures appropriately and fail fast. Don’t let long-running external calls impact your user experience.

### 5. Show, don't tell
If you have to explain how your code works, then your code is not clear enough.
Comments are for explaining <strong>why</strong> something is needed, not how it works.
Commit messages should follow [GDS guidance](https://github.com/alphagov/styleguides/blob/master/git.md)
No-one cares how clever you are - it’s far more important to work well with your team
APIs are interfaces too - Like any other interface, APIs need designing and iterating for usability

### 6. Think smaller
Stick to the Single Responsibility Principle - keep views, controllers and model classes as simple as possible. Keep methods short. (Concepts and patterns which may help with this: Null Object pattern, Facade pattern, Form Objects, Sandi Metz’s “[Rules for Developers](https://robots.thoughtbot.com/sandi-metz-rules-for-developers)”)
A solution composed of many small simple things is usually better than one big complex thing.

### 7. Names have power. Use them wisely.
Don’t be cute or jokey when naming things
Names convey meaning - well-named functions & variables can remove the need for a comment
Avoid meaningless names like ‘obj’ / ‘result’ / ‘foo’.
Use single-letter variables only where the letter represents a well-known mathematical property (e.g. e = mc^2), or where their meaning is otherwise clear.


See [Naming things]({{ 'standards/naming-things' | relative_url  }})

### 8. Composition over inheritance
It’s tempting to build an inheritance tree of objects extending others and redefining methods where needed - but that often just creates tech debt for the future. Choose ‘has-a’ relationships over ‘is-a’ - e.g. a Car has-a Motor, rather than Car is-a MotorVehicle

### 9. Any attempt to predict the future is likely to be wrong
This includes estimates of work - if they are to be used for assigning budget or predicting delivery dates, they should always come with a level of confidence, or a best/worst case range (e.g. “between x and y days” or “maybe x days, but i’m only 50% confident of that”)
The larger the chunk of work you’re estimating, the more inaccurate you will be - so if it doesn’t fit into a single sprint, break it down until it does

## C#-Specific Principles

### 1. Follow the Microsoft coding standards
The Microsoft developed [Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions) were  developed to give a consistent look and feel to C# code so that readers can focus on the content and not the layout. This can help reduce the congitive over-head and enable readers to understand the code more quickly based on their previous experience.

### 2. SOLID
Follow [SOLID principles](https://en.wikipedia.org/wiki/SOLID). This will make code more understandable and easier to maintain
* Single Responsibility - 
* Open/Closed principle
* Liskov Substitution
* Interface Segregation
* Dependency Inversion

### 3. Use static code analysis
To ensure that code meets the quality criteria of the Apprenticeship Service static code analysis via SonarCloud.io should be utilised and integrated into the build pipelines. The output of this analysis should be reviewed as part of the Code Review process and any issues highlighted should be rectified

### 4. Code Reviews
Ensure reviews are carried out on all code regardless of where the change originates. Also ensure the process is carried out with the appropriate riger and attention. Some things to keep in mind during the code review process:

* Give reviews your full attention
* Limit the amount of time you spend reviewing in any one sitting
* If necessary check the code out and test it locally
* Give constructive feedback
* Consider including non-developers in the review process, they may pick up different issues
* Do not merge code when there are unresolved comments or requests for change

### 5. Test Driven Development
Use test-driven development or [Behaviour Driven Development (BDD)](http://dannorth.net/introducing-bdd/) principles. It ensures that before you write your code that you have success criteria, and that your code is testable. It gives developers confidence that the code they have written works and the tests will give context that otherwise would be missing, this is especially valuable when the original developers have left the project.

## Code Branching

### 1. Create a branch from master for each new piece of work
When the work in the branch is complete create a pull request which can be reviewed.

### 2. Approving Pull Requests
When approving pull requests keep in mind the recommendations in the Coding Standards and ensure that any questionable code is challenged appropriately.

### 3. Delete branches once they are merged
Once the PR is approved and you are merging back into the master branch ensure that the original branch is deleted. This prevents the repository becoming littered with dead branches

## Technical Debt

### 1. Logged technical debt 
Technical Debt should be logged (we currently use Jira to do this) and triaged taking into account the effort to pay it back, the consequences and the risk. Then, depending on the identified severity taken directly into the appropriate team's backlog for completion or pushed into the Single Backlog where a larger impact on delivery is identified.

### 2. Ensure technical debt is communicated
When the decision is made to accept technical debt ensure that the decision has been communicated to the relevant people so that it can be understood and prioritised.

### 3. Dependancy management
Each time a dependency is added to a project whether its an internal or external dependency a potential piece of tech-debt is added. Before a dependency is added it should be considered whether it is truely necessary and only added if the answer is yes.
