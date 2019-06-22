---
layout: post
title:      "Git Cheat Sheet"
date:       2019-03-11 18:39:25 -0400
permalink:  git_cheat_sheet
---


A cheat sheet I compiled on creating and working with your own git repositories.

It was especially useful to have this when it was time to start coding projects. Most of the labs don't require you to initialize your own repos, or branch or commit them.

The basic method of updating a repository is add, commit, then push to the remote (stored on Git) repository.

* `git status` - see changes to be added, to be committed
* `git add .` - Prepares all changed files to be committed.
* `git commit -m ‘message’` - Commits added files to repo with a commit message. Messages should be in this tense, this commit will "...message". For example 'update readme', as the the commit will update the readme when implemented in the project.
* `git push` - pushes all commits to remote
* `git push -u origin master` - same as git push, but specifies pushing to the master branch
* `git commit --amend -m ‘updated commit msg’` - changes commit message of last commit

**Connecting remote repo**
To initialize a new git repo, should use `git init` to initialize a repo locally, then create, add and commit some files. Then create a new empty repository in your GitHub account, and follow the instructions to connect the remote to your local repo. Alternatively, you can create a new remote repo, then clone it down to your local environment before beginning your project in that directory.
* `git init` - create local repository, then create, add and commit some initial files
* `git remote add origin (…link…)` - connects remote repo, check quick setup in online repo
* `git push -u origin master` - pushes first commit to remote repo

**Branches**
Branches are used to separate code, for example to work on a new feature that you may not want to immediately have on the master version of your project.
* `git branch` - view branches
* `git checkout branch-name` - switches branches where future commits will be added
* `git checkout -b branch-name` - creates new branch ‘branch-name’ and switches to have work committed to this branch

After adding and committing files (be sure to be on correct branch), use one of the following to push to your branch. After this first push to a branch, `git push` should automatically go to that branch as well.
* `git push -u origin branch-name.` - pushes commits to branch
* `git push --set-upstream origin branch-name` - pushes commit to branch, same as above command

When your branch feature is finished, you can merge and push to your master branch with the following.
* `git checkout master` - switch branches(back to master)
* `git merge branch-name` - merges branch.

Then git add, commit and push as usual.

* `git branch -d branch-name` - deletes local branch

To clone down a branch of a remote repo
* `git clone -b branch-name ssh-link`
* `git clone -b branch-name ssh-link --single-branch` Add this flag to prevent fetching all branches in git 1.7.10+
