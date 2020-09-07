---
layout: default
category: Building software
title: Storing Source Code
---
# Storing source code

All our source code is open by default, and stored on well-known,
public code hosting services. At the Apprenticeship Service, we use GitHub.

We follow the principles set out in the service manual for managing the
code that we write:

- [use version control](https://www.gov.uk/service-manual/technology/maintaining-version-control-in-coding){:target="_blank"}
- [make source code open](https://www.gov.uk/service-manual/technology/making-source-code-open-and-reusable){:target="_blank"}

You should keep secrets separate from source code, and keep them private.

## GitHub

New repositories for products and services live in the
[Skills Funding Agency organisation](https://github.com/SkillsFundingAgency){:target="_blank"}
on GitHub. New repositories must be created within the [Skills Funding Agency organisation](https://github.com/SkillsFundingAgency){:target="_blank"} organisation, whether they contain service production code or prototypes. Work created outside of the Skills Funding Agency organisation should be transferred into the Skills Funding Agency organisation at the earliest opportunity. [Guide to transferring a repository](https://help.github.com/en/articles/transferring-a-repository){:target="_blank"}.

You can use your personal GitHub account (but you should [add your Apprenticeship Service
email address to your account](https://help.github.com/articles/adding-an-email-address-to-your-github-account/){:target="_blank"},
and maybe [use that for notifications](https://help.github.com/articles/managing-notification-emails-for-organizations/){:target="_blank"}).
Ask your delivery manager to request you being added to the Github organisation.

Private repositories are not a good way to protect secrets, and should only be used where access to the code might reveal draft policy decisions. Secrets should be managed at the platform level.

If a repository becomes redundant and the codebase is no longer in use or required then it should be archived using the following guideline before deletion:

|Repository Type | Archive Duration | Recovery after Deletion
|:-:| - | - |
| Public | 12 months | 90 days |
| Private | 6 months | 90 days |

Archiving of repositories should be completed following agreement with the relevant parties.

Repositories:

|Requirement|Description|Additional Notes
|:-:| - | - |
|Should|be [clearly named]({{ '/standards/naming-things' | relative_url }})|you should be able to infer a basic understanding of what something does from its name.|
|Should|have an [appropriate licence]({{ '/standards/naming-things' | relative_url }})|a software license tells others what they can and can't do with the source code.|
|Should|be well documented in the [README file]({{ '/development/coding-principles#11-create-a-useful-readme' | relative_url}})|there should be enough documentation that someone new can get started with the project.|
|Should|be initialised using the [das-github-template]{:target="_blank"} |(see: [creating a repository from a template]{:target="_blank"}) ensures new repositories include relevant folder structures, files and licence information.|
|Should|be built and deployed through a single build and release pipeline|improves maintainability.|
|Should|use [branch protection rules]{:target="_blank"} that require pull requests|notifies team members of code changes and improves code quality and standardisation through code reviews.|
|Should|use [branch protection rules]{:target="_blank"} that require status checks on commits|helps to maintain code quality by ensuring it is built and tested in the existing pipeline.|
|Should|use [branch protection rules]{:target="_blank"} that require [SonarCloud Code Analysis]({{ '/development/static-code-analysis/#static-code-analysis' | relative_url }})|helps to maintain code quality by using our chosen cloud native static code analysis tool. |
|Should|receive [dependabot alerts and security updates]{:target="_blank"}|improves visibility of vulnerabilities in custom code and dependant packages.|
|Should|assign the das-contributor team write access|ensures the relevant people have access to the repository.|
|Should|include a webhook to receive notifications of repository vulnerability alerts|increases visibility of security and vulnerability alerts.|
|Should|use a [gitignore]{:target="_blank"} file |helps to keep the repository free from temporary local files and artifacts.|
|Should NOT|be a fork of another repo||
|Should NOT|be used to store secrets||

[das-github-template]: https://github.com/SkillsFundingAgency/das-github-template
[creating a repository from a template]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template
[branch protection rules]:https://help.github.com/en/github/administering-a-repository/configuring-protected-branches
[dependabot alerts and security updates]: https://help.github.com/en/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features
[CODEOWNERS]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners
[gitignore]: https://git-scm.com/docs/gitignore