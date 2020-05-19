---
layout: default
title:  "Static Code Analysis"
area: development
permalink: /development/static-code-analysis/
---

# Static Code Analysis

Static code analysis can help to reduce the amount of bugs and vulnerabilities in a codebase by searching for known issues and highlighting them prior to them reaching a production environment. They can remove a lot of the overhead involved with manual code review processes by highlighting issues before the code reaches the point of a manual review. Automation of analysis also removes the likelihood of issues being missed and can help speed up the review process.

Static code analysis should be performed as early in the development process as practical, ideally this will be in the "Create" phase and before testing so that developers are aware of and can rectify issues as quickly as possible and can avoid the need for re-testing when issues are found. Where possible static code analysis should be integrated into Continuous Integration build pipelines so that no manual intervention is required for it to occur.

Any output of the analysis should be reviewed as part of the Code Review process and issues highlighted should be rectified before the review is accepted.

There are many static code analysers available, the Apprenticeship Service has chosen to use SonarCloud.

### SonarCloud

[SonarCloud](https://sonarcloud.io/organizations/educationandskillsfundingagency/projects) is a cloud native static code analyser based on SonarQube that integrates with GitHub and is free when analysing public repositories. It has support for many programming languages and there is an Azure DevOps build task available enabling it to be integrated into CI build pipelines.

Projects defined in SonarCloud can be connected to using an IDE Extension called [SonarLint](https://www.sonarlint.org/).  


### SonarLint

[SonarLint](https://www.sonarlint.org/) brings issues identified by SonarCloud rules closer to the developer by providing in-IDE feedback allowing developers to fix issues before they commit code.

There are extensions for four of the main development IDE's

* Visual Studio
* VS Code
* IntelliJ IDEA
* Eclipse