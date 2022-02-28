# Git Learning Notes - Part 4

## Undo staging

If staged unwanted changes accidentally with `git add .`, could undo staging: 

```console
$ git reset
```

## Undo a commit

If committed unwanted changes accidentally with `git commit -m "XXX"`, could undo the [stage and commit] by go back one step before `HEAD` (pointer to the last commit): 

```console
$ git reset HEAD~1
```

## Undo multiple commits, but not change local file

If need to undo multiple commits, git doesn't have a quick pointer for these. But can see a log of all the commits, in reverse chronological order, with each commit there's a hash: 

```console
$ git log
```

With the hash of the commit you want to revert to, just do: 

```console
$ git reset <commit-hash>
```

## To not only unstage, but completely remove updates in local file

```console
$ git reset --hard <commit-hash>
```

Or

```console
$ git checkout <commit-hash>
```






















