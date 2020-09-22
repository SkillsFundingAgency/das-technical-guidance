---
layout: default
title:  "Source Control"
---

# Source Control

All our source code is [open by default](https://www.gov.uk/service-manual/technology/making-source-code-open-and-reusable), and stored on well-known,
public code hosting services. At the Apprenticeship Service, we use [GitHub](https://www.gov.uk/service-manual/technology/maintaining-version-control-in-coding).

## GitHub

New repositories for products and services live in the
[Skills Funding Agency organisation](https://github.com/SkillsFundingAgency)
on GitHub. New repositories must be created within the [Skills Funding Agency organisation](https://github.com/SkillsFundingAgency) organisation, whether they contain service production code or prototypes. Work created outside of the Skills Funding Agency organisation should be transferred into the Skills Funding Agency organisation at the earliest opportunity. [Guide to transferring a repository](https://help.github.com/en/articles/transferring-a-repository).

You can use your personal GitHub account (but you should [add your Apprenticeship Service
email address to your account](https://help.github.com/articles/adding-an-email-address-to-your-github-account/),
and maybe [use that for notifications](https://help.github.com/articles/managing-notification-emails-for-organizations/)).
Ask your delivery manager to request you being added to the Github organisation.

## Secrets and Sensitive Configuration

To ensure the safety and security of our systems; secrets, sensitive configuration and artefacts should not be pushed to public repositories. However this does not mean that private repositories are a good way to protect secrets, they are not. Secrets should be stored using technologies specifically designed for the task such as Azure Key Vaults, Secure Azure DevOps pipeline secret variables, etc...

## Code Branching

Maintaining a consistent code branching strategy can help to ensure the development process is as smooth as possible and avoid many pitfalls when a team is  working on the same code-base.

### 1. Create a branch from master for each new piece of work
When the work in the branch is complete create a pull request which can be reviewed. Local-only branches made from the feature branch can be used to split out the work further, these can then be re-integrated back into the feature branch before being pushed to the origin. When multiple people are working on the same feature, the Feature branch can be used as an integration point for those branches taken from it. 

### 2. Branches should be as short-lived as possible
Short-lived branches minimise the effort involved when performing merging & rebase operations and reduce the potential for conflicts to emerge if multiple work-streams move concurrently

### 3. Delete branches when they are no-longer needed
Once a branch is no longer needed it should be deleted, this helps keep the repository tidy and prevents the repository becoming littered with dead branches.

[The GDS Way - Branching and Merging](https://gds-way.cloudapps.digital/standards/source-code.html#branching-merging-conventions)

## Licensing

Repositories should be [clearly named]({{ '/standards/naming-things' | relative_url }}),
and have an [appropriate licence]({{ '/standards/licencing-software-or-code' | relative_url }})
and enough documentation that someone new can get started with the
project.

## Creating an Effective Readme

An effective and comprehensive Readme within a repository can help to simplify and accelerate the job new contributors have getting up to speed with a new code-base.

An effective Readme should contain at least the following information:

- An overview of the purpose of the code
- All pre-requisites and dependencies will be identified
- An explanation on how to get the code
- An explanation on how to set-up and run the code, give examples with code snippets and images
- The requirements that must be met for someone to start contributing, for instance
  - Coding conventions
  - Unit testing practices (style, code coverage, etc)
  - Any documentation requirements
- Licensing details

Optionally, adding build and analysis status badges can enhance the amount of information being presented.
 
### Example Readme

<pre>
# Project Title
*Brief overview of your project*

## Getting Started
*These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.*

### Prerequisites
*List the minimum requirements and tools needed to run your program*

### Installing
*Setup instructions*

1.
2.
3.

## Usage
*Include a variety of examples using snippets, images etc.*

## Testing
*Explain how to run the automated tests for this system*

## Known Issues
*Acknowledge known issues and provide a workaround* 

## Contributing
*Please read [CONTRIBUTING.md](#contributingUrl) for details on our code of conduct, and the process for submitting pull requests to us.*

## License
*License name*
</pre>

