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

- [use version control](https://www.gov.uk/service-manual/technology/maintaining-version-control-in-coding)
- [make source code open](https://www.gov.uk/service-manual/technology/making-source-code-open-and-reusable)

You should keep secrets separate from source code, and keep them private.

## GitHub

New repositories for products and services live in the
[Skills Funding Agency organisation](https://github.com/SkillsFundingAgency)
on GitHub. New repositories must be created within the [Skills Funding Agency organisation](https://github.com/SkillsFundingAgency) organisation, whether they contain service production code or prototypes. Work created outside of the Skills Funding Agency organisation should be transferred into the Skills Funding Agency organisation at the earliest opportunity. [Guide to transferring a repository](https://help.github.com/en/articles/transferring-a-repository).

You can use your personal GitHub account (but you should [add your Apprenticeship Service
email address to your account](https://help.github.com/articles/adding-an-email-address-to-your-github-account/),
and maybe [use that for notifications](https://help.github.com/articles/managing-notification-emails-for-organizations/)).
Ask your delivery manager to request you being added to the Github organisation.

Private repositories are not a good way to protect secrets, and should only be used where access to the code might reveal draft policy decisions. Secrets should be managed at the platform level.

If a repository becomes redundant and the codebase is no longer in use or required then it should be archived for # months before it is deleted altogether. This should be done following agreement with relevant parties.

Repositories:

|Requirement| Description                     | Additional Notes
|:-:| - | - |
|Should|be [clearly named]({{ '/standards/naming-things' |relative_url }})||
|Should|have an [appropriate licence]({{ '/standards/licencing-software-or-code' | relative_url }})|a software license tells others what they can and can't do with the source code|
|Should|be well documented in the README file|there should be enough documentation that someone new can get started with the project|
|Should|be initialised using the [das-github-template]{:target="_blank"} (WIP) |(see: [creating a repository from a template]{:target="_blank"}ensure new repositories include relevant folder structure, files and license information|
|Should|contain code that will be built and deployed through a single build and release pipeline|the repository should not need multiple pipeline |
|Should|use [branch protection rules]{:target="_blank"} that require pull requests|this helps notify teams of code changes and improves code quality and standardisation through code reviews|
|Should|use [branch protection rules]{:target="_blank"} that require status checks on commits|helps to maintain code quality by ensuring new code is built and tested in the existing pipeline|
|Should|receive [dependabot alerts and security updates]{:target="_blank"}|maintains and improves security by notifying of vulnerabilities in custom code and dependant packages on a regular basis|
|Should|assign the das-contributor team write access|ensures the required access to the repository by |
|Should|include a webhook to receive notifications of repository vulnerability alerts|improves visibility of security and vulnerability alerts|
|Should|use a [gitignore]{:target="_blank"} file |helps to keep the repository free from temporary local files and artifacts|
|Should NOT|be a fork of another repo||
|Should NOT|be used to store secrets||

[das-github-template]: https://github.com/SkillsFundingAgency/das-github-template
[creating a repository from a template]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template
[branch protection rules]:https://help.github.com/en/github/administering-a-repository/configuring-protected-branches
[dependabot alerts and security updates]: https://help.github.com/en/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features
[CODEOWNERS]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners
[gitignore]: https://git-scm.com/docs/gitignore