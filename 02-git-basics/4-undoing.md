# Git Learning Notes - Part 4
## Undo staging
If staged unwanted changes accidentally with `git add .`, could undo staging: 
```sh
$ git reset
```

## Undo a commit
If committed unwanted changes accidentally with `git commit -m "XXX"`, could undo the [stage and commit] by going back one step before `HEAD` (pointer to the last commit): 
```sh
$ git reset HEAD~1
```

## Undo multiple commits, but not change local file
If need to undo multiple commits, git doesn't have a quick pointer for these. But can see a log of all the commits, in reverse chronological order, with each commit there's a hash: 
```sh
$ git log
```

With the hash of the commit you want to revert to, just do: 
```sh
$ git reset <commit-hash>
```

## To not only unstage, but completely remove updates in local file
```sh
$ git reset --hard <commit-hash>
```

Or
```sh
$ git checkout <commit-hash>
Note: switching to '0570ad182103eaac1ec409fc7b935476fb3d0d9e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 0570ad1 test
```

Above command takes us to a new branch, to go back to main and see the most current status: 
```sh
$ git checkout main
Previous HEAD position was 0570ad1 test
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```
