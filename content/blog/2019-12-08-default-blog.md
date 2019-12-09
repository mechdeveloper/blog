---
title: Basic Git commands
date: 2019-12-09T15:22:49.004Z
description: basic commands to get started with git version control
---
## git clone
clone an existing git repository.
```
git clone <remote-repository-url>
git clone https://github.com/libgit2/libgit2
```

## git init
initialize a git repository

## git status
Checking the Status of Your Files
```
git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

## git add 
Tracking New Files or Staging Modified files
```
git add <file-name>
```

To stage all modified files / track all new files
```
git add .
```

## git commit
commit your changes to git repository
```
git commit -m "Story 182: Fix benchmarks for speed"
```

Skip staging area by using ```-a``` option to the ```git commit``` command, this will make Git automatically stage every file that is already tracked before doing the commit, letting you skip the ```git add``` part
```
git commit -a -m 'added new benchmarks'
```

## git rm
Removing Files from Git. ```git rm``` removes file from working directory
```
git rm <file-name>
git rm PROJECTS.md
```

## git mv
Moving Files. To rename a file in Git, you can run
```
git mv <file-from> <file-to>
git mv README.md README
```

### git log
Viewing the Commit History.
```
git log
git log -p -2
git log --stat
git log --pretty=oneline
git log --pretty=format:"%h - %an, %ar : %s"
git log --pretty=format:"%h %s" --graph
git log --since=2.weeks
```

## git remote 
Working with Remotes. Manage remote repositories.

Showing Your Remotes. 
```
git remote
origin
git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
```

Adding Remote Repositories.
>Note: ```git clone``` command implicitly adds the origin remote for you. 
To add a new remote Git repository as a shortname you can reference easily
```
git remote add <shortname> <url>
git remote add pb https://github.com/paulboone/ticgit
```

Inspecting a Remote. 
use the following command to see more information about a particular remote
```
git remote show <remote>
git remote show origin
```

Renaming Removing Remotes
Following command will rename the pb remote to paul. this changes all your remote-tracking branch names, too. pb/master is now paul/master
```
git remote rename pb paul
```

To remove a remote use following command
```
git remote remove paul
```
or 
```
git remote rm paul
```


## git fetch
Fetching and Pulling from Your Remotes. To get data from your remote project you can run 
```
git fetch <remote>
git fetch origin
```
>Note: ```git fetch``` command only downloads the data to your local repository - it doesn't automatically merge it with any of your work or modify what you're currently working on. You have to merge it manually into your work when you're ready.

## git pull
```git pull``` command is used to automatically fetch and then merge the remote branch into your current branch. Running ```git pull``` generally fetches data from server you originally cloned from and automatically tries to merge it into the code you're currently working on.

## git push
Pushing to Your Remotes. push committed changes in local repository up to remote repository.
```
git push
git push <remote> <branch>
git push origin master
```

## git tag
Tagging.

Listing Your Tags. 
Listing tag wildcards requires ```-l``` or ```--list``` option
```
git tag
git tag -l "v1.8.5*"
```

Annoated Tags
```
git tag -a v1.4 -m "my version 1.4"
```

Lightweight Tags
```
git tag v1.4-lw
```

To see tag information
```
git show v1.4
git show 1.4-lw
```

Tagging Later
```
git tag -a <tag-name> <commit-hash>
git tag -a v1.2 9fceb02
```

Sharing Tags
```
git push origin v1.5
git push origin --tags
```

Deleting Tags
```
git tag -d v1.4-lw
```
to delete a remote tag
```
git push origin --delete <tagname>
```

Checkout Tags
```
git checkout v2.0.0
git checkout -b version2 v2.0.0
```

## git branch
Branch Management.

List your current branches
```
git branch
```

To see last commit on each branch
```
git branch -v
```

The useful ```--merged and --no-merged options can filter the list of branches that you have not yet merged into the branch you're currently on.
```
git branch --merged
git branch --no-merged
```

create a new branch 
```
git branch testing
```

delete a branch
```
git branch -d hotfix
```

delete an unmerged branch or delete a branch and lose the work
```
git branch -D testing
```

## git checkout
Switching Branches
```
git checkout testing
```

Creating a new branch and switching to it at the same time
```
git checkout -b <newbranchname>
```

## git merge
merge branch
```
git checkout master
git merge hotfix
```


