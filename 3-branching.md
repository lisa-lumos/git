# Git Learning Notes - Part 3

Branch can be used as a sandbox (for new features, hot fixes, etc), later can be merged into the main branch. 

## To show branches

The \* in front of main indicates that main is my current branch. 

```sh
$ git branch
* main
```

##Create and switch to a new brach

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



















