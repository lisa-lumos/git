# 3. Git branching
## 3.1 Branches in a Nutshell
Branching means you diverge from the main line of development, and continue to do work without messing with that main line.

The way Git branches is incredibly lightweight, making branching operations nearly instantaneous, and switching back and forth between branches generally just as fast. 

Unlike many other VCSs, Git encourages workflows that branch and merge often, even multiple times in a day.

The 'master' branch in Git is not a special branch. It is exactly like any other branch. The only reason nearly every repository has one is that the git init command creates it by default, and most people don't bother to change it.

HEADis a pointer to the local branch you're currently on. The HEAD branch moves forward when a commit is made. 

```sh
# switch to an existing branch, which moves the HEAD to point to it
git checkout my-existing-branch
git switch my-existing-branch

# creating a new branch and switching to it at the same time
git checkout -b my-new-branch
git switch -c my-new-branch
```

## 3.2 Basic Branching and Merging
An example:
```sh
$ git checkout -b iss53
# Switched to a new branch "iss53"

$ vim index.html
git commit -a -m 'Create new footer [issue 53]'

$ git checkout master
# Switched to branch 'master'

$ git checkout -b hotfix
# Switched to a new branch 'hotfix'

$ vim index.html

$ git commit -a -m 'Fix broken email address'
# [hotfix 1fb7853] Fix broken email address
#  1 file changed, 2 insertions(+)

$ git checkout master

$ git merge hotfix
# merge the hotfix branch back into your master branch
# when the branch you're merging into is an ancestor of the branch you're merging from - this is called a "fast-forward".

$ git checkout iss53
# Switched to branch "iss53"

$ vim index.html
$ git commit -a -m 'Finish the new footer [issue 53]'
# [iss53 ad82d7a] Finish the new footer [issue 53]
# 1 file changed, 1 insertion(+)

$ git checkout master
# Switched to branch 'master'
$ git merge iss53 # basic merging
# Merge made by the 'recursive' strategy.
# index.html |    1 +
# 1 file changed, 1 insertion(+)

# If you changed the same part of the same file differently in the two branches you're merging, Git won't be able to merge them cleanly.
$ git merge iss53
# Auto-merging index.html
# CONFLICT (content): Merge conflict in index.html
# Automatic merge failed; fix conflicts and then commit the result.

# To see which files are unmerged at any point after a merge conflict
$ git status

# Git adds standard conflict-resolution markers to the files that have conflicts, # so you can open them manually and resolve those conflicts.

```

## 3.3 Branch Management
```sh
# list of branches, * prefix shows current branch
$ git branch

# show last commit on each branch
$ git branch -v

# branches merged into cur branch:
$ git branch --merged

# opposite
$ git branch --no-merged

# rename a branch, and push it to remote, and del old branch
$ git branch --move old-branch-name new-branch-name
$ git push --set-upstream origin new-branch-name
$ git push origin --delete old-branch-name

```

## 3.4 Branching Workflows
Topic branches are useful in projects of any size. A topic branch is a short-lived branch that you create and use for a single particular feature or related work. 

## 3.5 Remote Branches



## 3.6 Rebasing



## 3.7 Summary



































