---
layout: default
title:  "Code Branching"
area: development
---

# Code Branching

Maintaining a consistent code branching strategy can help to ensure the development process is as smooth as possible and avoid many pitfalls when a team is  working on the same codebase.

### 1. Create a branch from master for each new piece of work
When the work in the branch is complete create a pull request which can be reviewed. Local-only branches made from the feature branch can be used to split out the work further, these can then be re-integrated back into the feature branch before being pushed to the origin.

### 2. Branches should be as short-lived as possible
So that rebase and merging operations are as straight forward as possible branches should be as short-lived as they can be. 

### 3. Delete branches when they are no-longer needed
Once a branch is no longer needed it should be deleted, this helps keep the repository tidy and prevents the repository becoming littered with dead branches.

[The GDS Way - Branching and Merging](https://gds-way.cloudapps.digital/standards/source-code.html#branching-merging-conventions)