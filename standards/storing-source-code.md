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

Repositories should be [clearly named]({{ '/standards/naming-things' | relative_url }}),
and have an [appropriate licence]({{ '/standards/licencing-software-or-code' | relative_url }})
and enough documentation that someone new can get started with the
project. They should be initialised using the [das-github-template]{:target="_blank"} (WIP) (see: [creating a repository from a template]{:target="_blank"} and contain code that will be built and deployed through a single build and release pipeline. 

At a minimum the repository should:

- not be a fork
- use [branch protection rules]{:target="_blank"} that
    - require pull requests reviews
    - require status checks on commits
- receive [dependabot alerts and security updates]{:target="_blank"}
- assign the das-contributor team write access
- include a webhook to receive notifications of repository vulnerability alerts
- make use of:
    - the [CODEOWNERS]{:target="_blank"} file which should be updated regularly as the team responsible for maintaining the repository changes
    - [gitignore]{:target="_blank"} file to keep the repository free from temporary local files and artifacts

Private repositories are not a good way to protect secrets, and should only be used where access to the code might reveal draft policy decisions.  Secrets should be managed at the platform level.

If a repository becomes redundant and the codebase is no longer in use or required then it should be archived for # months before it is deleted altogether. This should be done following agreement with relevant parties.

[das-github-template]: https://github.com/SkillsFundingAgency/das-github-template
[creating a repository from a template]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template
[branch protection rules]:https://help.github.com/en/github/administering-a-repository/configuring-protected-branches
[dependabot alerts and security updates]: https://help.github.com/en/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository#enabling-or-disabling-security-and-analysis-features
[CODEOWNERS]: https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners
[gitignore]: https://git-scm.com/docs/gitignore