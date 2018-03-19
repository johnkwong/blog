---
layout: post
title: Git branching model
tags: [git]
---
#### Types of branches
* Main branches
  * Master
  * Develop
* Supporting branches
  * Feature branch (topic branch)
  * Release branch
    * release-*
  * Hot fix branch
    * hotfix-*  

#### Feature Branch
##### Creating a feature branch
Create a new feature branch and branch off from the develop branch
```
$ git checkout -b myfeature develop
Switched to a new branch "myfeature"
```
##### Incorporating a finished feature on develop
```
$ git checkout develop
Switched to branch 'develop'
$ git merge --no-ff myfeature
Updating ea1b82a..05e9557
(Summary of changes)
$ git branch -d myfeature
Deleted branch myfeature (was 05e9557).
$ git push origin develop
```
#### Release Branch
##### Creating a release branch
```
$ git checkout -b release-1.2 develop
Switched to a new branch "release-1.2"
$ ./bump-version.sh 1.2
Files modified successfully, version bumped to 1.2.
$ git commit -a -m "Update: release 1.2"
[release-1.2 74d9424] Update: release 1.2
1 files changed, 1 insertions(+), 1 deletions(-)
```
##### Finishing a release branch
```
$ git checkout master
Switched to branch 'master'
$ git merge --no-ff release-1.2
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2 -m "Release v1.2 Tag"
```
Merge release back into develop
```
$ git checkout develop
Switched to branch 'develop'
$ git merge --no-ff release-1.2
Merge made by recursive.
(Summary of changes)
```
```
$ git branch -d release-1.2
Deleted branch release-1.2 (was ff452fe).
```
#### Hotfix branches
##### Creating the hotfix branch
```
$ git checkout -b hotfix-1.2.1 master
Switched to a new branch "hotfix-1.2.1"
$ ./bump-version.sh 1.2.1
Files modified successfully, version bumped to 1.2.1.
$ git commit -a -m "Bumped version number to 1.2.1"
[hotfix-1.2.1 41e61bb] Bumped version number to 1.2.1
1 files changed, 1 insertions(+), 1 deletions(-)
```
##### Finishing a hotfix branch
```
$ git checkout master
Switched to branch 'master'
$ git merge --no-ff hotfix-1.2.1
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2.1
```
Merge hotfix back into develop
```
$ git checkout develop
Switched to branch 'develop'
$ git merge --no-ff hotfix-1.2.1
Merge made by recursive.
(Summary of changes)
```
```
$ git branch -d hotfix-1.2.1
```

References:  
http://nvie.com/posts/a-successful-git-branching-model/
