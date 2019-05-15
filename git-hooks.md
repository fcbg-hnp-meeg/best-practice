# Git hooks
*Adapted from [an Atlassian Tutorial](https://www.atlassian.com/git/tutorials/git-hooks)*

## Overview
Git hooks execute actions automatically after some events in a git repository. Events can be local or server side repositories.
Examples include checking PEP8 before commit, or running unit tests after a commit. The list of hook event categories are describe below.

## Implementation
Hooks are simple scripts which reside in .git/hooks within a git repository. Git comes with examples with the  '.sample' extension which disable them. To activate them one can simply remove this extension.

Scripts are usually written in shell but any executable is fine.

## Example of PEP 8 validation
### PEP 8 install
conda install flake8 (or pip install)
echo "#!/bin/sh" >> .git/hooks/pre-commit 
echo "flake8 ." >> .git/hooks/pre-commit

## Local hooks categories
* pre-commit
* prepare-commit-msg
* commit-msg
* post-commit
* post-checkout
* pre-rebase

