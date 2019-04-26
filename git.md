Introduction
============



Create a new repository
=======================
create a new directory, open it and perform a

    git init

to create a new git repository.


Workflow
========

Your local repository consists of three "trees" maintained by git. 
The first one is your _Working Directory_ which holds the actual files. 
The second one is the _Index_ which acts as a staging area. 
Finally the _HEAD_ which points to the last commit you've made.


add & commit
============

First, changes are staged to the _Index_ tree

From a specific file:

    git add <filename>

From all the files in the folder including untracked files:
    
    git add *

From all the files already tracked:
    
    git add -U


Second, changes have to be commited to the _HEAD_ tree. They are not yet commited to the remote repository.

     git commit -m "commit message"


Pushing changes
===============

Your changes are now in the _HEAD_ of your local working copy. 

To send those changes to your remote repository:

     git push origin master
Change master to whatever branch you want to push your changes to. 

If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with:

    git remote add origin <server>
Now you are able to push your changes to the selected remote server


Branching
=========

Branches are used to develop features isolated from each other. The master branch is the "default" branch when you create a repository. Use other branches for development and merge them back to the master branch upon completion.

Create a new branch named "feature_x" and switch to it using:

    git checkout -b feature_x

switch back to master:

    git checkout master

and delete the branch again:

    git branch -d feature_x

A branch is not available to others unless you push the branch to your remote repository:

    git push origin <branch>


update & merge
==============

To update your local repository to the newest commit:

    git pull

It is identical to:
    
    git fetch
    git merge

To merge another branch into your active branch:

    git merge <branch>

Unfortunately, this can result in conflicts. You are responsible to merge those conflicts manually by editing the files shown by git.

Before merging changes, you can also preview them by using:

    git diff <source_branch> <target_branch>

Log
===

You can study repository history using:

    git log

To see only the commits of a certain author:

    git log --author=bob

To see a very compressed log where each commit is one line:

    git log --pretty=oneline

To see only which files have changed: 

    git log --name-status

These are just a few of the possible parameters you can use. For more, see:

    git log --help


Replace local changes
=====================

To replace local changes in your working tree with the last content in _HEAD_:

    git checkout -- <filename>
Changes already added to the INDEX, as well as new files, will be kept.

To drop all your local changes and commits:

    git fetch origin
    git reset --hard origin/master