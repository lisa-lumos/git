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



## 3.3 Branch Management



## 3.4 Branching Workflows



## 3.5 Remote Branches



## 3.6 Rebasing



## 3.7 Summary



































