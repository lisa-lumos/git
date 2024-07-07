# Git Learning Notes - Part 3
Branch can be used as a sandbox (for new features, hot fixes, etc), later can be merged into the main branch. 

## To show branches
The \* in front of main indicates that main is my current branch. 
```sh
$ git branch
* main
```

## Create and switch to a new brach
`git checkout -b feature-test` or `git branch feature-test` both work:
```sh
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
```sh
$ git push --set-upstream origin feature-test
```

## Merge this branch to main
When at master branch, 
```sh 
$ git merge feature-test
$ git log
```

`git log` now shows commits to the branch. 

## After merging this branch to main
```sh
$ git pull
```
And the newly updated changes to main is pulled to local. 

Then delete the branch, because it is already merged to main:
```sh
$ git branch -d feature-test
Deleted branch feature-test (was 362a0ab).
```

## If multiple people collaborates
In this case, when you are working on your branch, you want to keep up with changes that has been made to main. 

This would return a merge conflict if main branch has changed: 
```sh
$ git merge main
```

The easy way is to accept changes in code editor. After fixing the merge conflict, need to commit. 
