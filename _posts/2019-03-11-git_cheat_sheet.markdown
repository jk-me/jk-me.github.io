---
layout: post
title:      "Git Cheat Sheet"
date:       2019-03-11 18:39:25 -0400
permalink:  git_cheat_sheet
---


A cheat sheet I compiled on remembering how to create your own git repositories.

It was especially useful to have this when it was time to start coding projects. Most of the labs don't require you to initilialize your own repos, or branch or commit them.

* git status  //see changes to be added, to be committed

* $git add .   //prepares all changed files to be committed 
* $git commit -m ‘message’  //commits files to repo with a commit message
                              //messages should be in this tense, this commit will “add function x”
* $git push             //pushes to remote
* $git push -u origin master 
 
* $git commit --amend -m ‘updated commit msg’ //changes commit message of last commit

Connecting remote repo
* $git init  //create local repository
                     //create, add and commit some initial files 
                    //create a new repo in GitHub acc, readme not req if exists
* $git remote add origin (…link…)  //connects remote repo, check quick setup in online repo
* $git push -u origin master 

Branches
* $git checkout -b branch-name           //creates new branch ‘branch-name’
* $git branch             //view branches
* $git add .               //prepare for commit
* $git commit -m ‘message’                //commit 
* $git push -u origin branch-name.               //pushes commits to branch
* $git push --set-upstream origin branch-name   //pushes commit to branch 

* $git branch -d branch-name   //deletes local branch

Push branch to master
* $git checkout master //switch branches(back to origin)
* $git merge branch-name //merges branch 

git add >> commit >> push
