# Git Learning Notes - Part 3

Branch can be used as a sandbox (for new features, hot fixes, etc), later can be merged into the main branch. 

## To show branches

The \* in front of main indicates that main is my current branch. 

```console
$ git branch
* main
```

## Create and switch to a new brach

```console
$ git checkout -b feature-test
Switched to a new branch 'feature-test'

$ git branch
* feature-test
  main
  
$ git checkout main
M	3-branching.md
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

$ git checkout feature-test
M	3-branching.md
Switched to branch 'feature-test'
```

## Push to the new branch

```console
$ git push --set-upstream origin feature-test
```

## After merging this branch to main via UI

```console
$ git pull
```
And the newly updated changes to main is pulled to local. 

Then delete the branch, because it is already merged to main:

```console
$ git branch -d feature-test
Deleted branch feature-test (was 362a0ab).
```

## If multiple people collaborates

In this case, when you are working on your branch, you want to keep up with changes that has been made to main. 

This would return a merge conflict if main branch has changed: 

```console
$ git merge master
```

The easy way is to accept changes in code editor. After fixing the merge conflict, need to commit. 





