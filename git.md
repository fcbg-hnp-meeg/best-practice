Introduction
============



Create a new repository
=======================
Create a new directory, open it and create a new git repository:

    git init


Clone a remote repository
=========================

    git clone <URL> 


Workflow
========

Your local repository consists of three "trees" maintained by git. 

* _Working Directory_ which holds the actual files. 

* _Index_ which acts as a staging area. 

* _HEAD_ which points to the last commit you've made.


add & commit
============

First, changes are staged to the _Index_ tree

From a specific file:

    git add <filename>

From all the files in the folder including untracked files, without deletions:
    
    git add .

From all the files in the folder including untracked files, including deletions:
    
    git add -A

From all the files already tracked:
    
    git add -U

Second, changes have to be commited to the _HEAD_ tree. They are not yet commited to the remote repository.

     git commit -m "commit message"

If you want to skip the staging area and automatically stage every file that is already tracked before doing the commit

    git commit -a -m "commit message"    

To write a comment, follow those instructions:

* Start the subject line with "Fix", "Add", "Change" instead of "Fixed", "Added", "Changed".
* Limit the subject line to 50 characters (72 is the hard limit)
* Always leave the second line blank
* Not every commit requires a body
* Wrap the body at 72 characters

A properly formed Git commit subject line should always be able to complete the following sentence: 

_If applied, this commit will your subject line here_

For example, 

    If applied, this commit will refactor subsystem X for readability
    If applied, this commit will update getting started documentation
    If applied, this commit will remove deprecated methods

If it seems difficult to summarize what your commit does, it may be because it includes several logical changes or bug fixes, and are better split up into several commits using
    
    git add -p.

Remove or rename a file
=======================

To remove a file from git:

    git rm <filename>

To move or rename a file:

    git move file_from file_to


Status
======

Find out information regarding what files are modified and what files are there in the staging area :

    git status


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

Create a new branch named "feature_x":
    
    git branch feature_x

To switch to the new branch:

    git checkout feature_x 

Create a new branch named "feature_x" and switch to it using:

    git checkout -b feature_x

Delete the branch again:

    git branch -d feature_x

List all the branch

    git branch

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


Configuring tool
================

Sets the name you want attached to your commit transactions:

     git config --global user.name "[name]"

Sets the email you want attached to your commit transactions:

    git config --global user.email "[email address]"

Enables helpful colorization of command line output:

    git config --global color.ui auto

To exclude files and path from git versioning, add the file name to the _.gitignore_ file.

To list all ignored files in this project:

    git ls-files --other --ignored --exclude-standard

Summary
=======

The official documentation can be found at [here][https://git-scm.com/docs]


![Image](gitWorkflow.png "icon")