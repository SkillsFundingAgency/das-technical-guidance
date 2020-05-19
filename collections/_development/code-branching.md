---
layout: default
title:  "Code Branching"
area: development
---

# Code Branching

Maintaining a consistent code branching strategy can help to ensure the development process is as smooth as possible and avoid many pitfalls when a team is  working on the same codebase.

### 1. Create a branch from master for each new piece of work
When the work in the branch is complete create a pull request which can be reviewed. Local-only branches made from the feature branch can be used to split out the work further, these can then be re-integrated back into the feature branch before being pushed to the origin. When multiple people are working on the same feature, the Feature branch can be used as an integration point for those branches taken from it. 

### 2. Branches should be as short-lived as possible
Short-lived branches minimise the effort involved when performing merging & rebase operations and reduce the potential for conflicts to emerge if multiple workstreams move concurrently

### 3. Delete branches when they are no-longer needed
Once a branch is no longer needed it should be deleted, this helps keep the repository tidy and prevents the repository becoming littered with dead branches.

[The GDS Way - Branching and Merging](https://gds-way.cloudapps.digital/standards/source-code.html#branching-merging-conventions)