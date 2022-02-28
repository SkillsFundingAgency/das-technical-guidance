---
layout: default
title:  "Code Reviews"
category: development
---

# Code Reviews

Code reviews are an essential part of the development process and must be carried out on all code regardless of where the change originates. The process should also be carried out with the appropriate rigour and attention. Some things to keep in mind during the code review process:

* Give reviews your full attention
* Limit the amount of time you spend reviewing in any one sitting
* In the main you should check the code out during the review and test it locally
* Give **constructive** feedback
* Consider including non-developers in the review process, they may pick up different issues
* Do not merge code when there are unresolved comments or requests for change
  * Code merging in the main is a responsibility of the Quality Assurance team and will be performed after review from the Product Owner

[The GDS Way - Code Reviews](http://gds-way.cloudapps.digital/manuals/code-review-guidelines.html)

## Using static code analysis during reviews

Reviewers are advised to make use of the department's chosen [static code analysis](/development/static-code-analysis) tools (SonarCloud) to review the quality of the code and take remedial action where necessary.

- Static code analysis occurs automatically when a pull request is raised and is viewable on the 'check' tab for that pull request in GitHub.
- Reviewers should examine the output of the check to determine:
  - If the code has any vulnerabilities.
  - If the code has any 'code smells' (potential bugs or exploits).
  - If the code has sufficient test coverage.
  - If the code has a high percentage of duplication.
- A check will pass or fail based on a range of criteria.[^1] For example:
  - Test coverage within the required tolerance.
  - Code duplication within the required tolerance.
  - A sufficient security rating.
  - A sufficient maintainability rating.
  - A sufficient reliability rating.
- Any failures should be investigated and, where possible, rectified.
  - Where a failure is not (or cannot be) rectified, but the release is still intended to be approved and merged, the reviewer should document the justification and, where necessary, escalate to their lead developer or developer clan lead. Unresolved issues should be considered tech debt for which the team is responsible.
- A pull request with a failed check cannot be merged unless it has at least one approval.

[^1]: Note that the values for each of the required criteria are subject to change and may vary between projects. Please see the check statistics for the project in question for specific requirements.
