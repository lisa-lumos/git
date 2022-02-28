# Git Learning Notes - Part 2

## If create a repo locally instead of cloning 

If create a new folder `SQL-notes`, and show all files in this dir:

```console
$ pwd
/Users/lisa/Desktop/git/SQL-notes
$ ls -la
total 8
drwxr-xr-x  3 lisa  staff   96 Feb 27 18:48 .
drwxr-xr-x@ 5 lisa  staff  160 Feb 27 18:33 ..
-rw-r--r--@ 1 lisa  staff   35 Feb 27 18:48 SQL-notes-Part 1.md
```

Can see that there's no `.git` folder. So need to create it with `init`: 

```console
$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint: 	git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint: 	git branch -m <name>
Initialized empty Git repository in /Users/lisa/Desktop/git/SQL-notes/.git/

$ ls -la  
total 8
drwxr-xr-x  4 lisa  staff  128 Feb 27 19:48 .
drwxr-xr-x@ 5 lisa  staff  160 Feb 27 18:33 ..
drwxr-xr-x  9 lisa  staff  288 Feb 27 19:48 .git
-rw-r--r--@ 1 lisa  staff   35 Feb 27 18:48 SQL-notes-Part 1.md

$ git config --global init.defaultBranch main   
$ git branch -m main
$ touch .gitignore
$ vi .gitignore
```

To pulish it online, need to go to Github web UI and create a repo `SQL-notes`, with nothing added inside. Next, copy the ssh link `git@github.com:lisa-lumos/SQL-notes.git` of this remote repo, and add this link as remote repository to git, and view it to confirm:

```console
$ git remote add origin git@github.com:lisa-lumos/SQL-notes.git
$ git remote -v
origin	git@github.com:lisa-lumos/SQL-notes.git (fetch)
origin	git@github.com:lisa-lumos/SQL-notes.git (push)
```

Now can push this local repo to Github: 

```console
$ git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 309 bytes | 309.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:lisa-lumos/SQL-notes.git
 * [new branch]      main -> main
```

If would like to no longer type `origin main` when using the `push` command, set it as default: 

```console
$ git push -u origin main  
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 331 bytes | 331.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:lisa-lumos/SQL-notes.git
   58ebb0a..d7d0237  main -> main
```

To force a push: 

```console
$ git push -f
Enumerating objects: 45, done.
Counting objects: 100% (45/45), done.
Delta compression using up to 8 threads
Compressing objects: 100% (40/40), done.
Writing objects: 100% (45/45), 7.20 KiB | 7.20 MiB/s, done.
Total 45 (delta 10), reused 6 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (10/10), done.
To github.com:lisa-lumos/git-learning.git
 + 433060c...6e9208d main -> main (forced update)
```

## Summary

To sum up, here are all the git commands by far: 

```console
$ git init
$ git add .
$ git commit -m "title of my commit"
$ git remote add origin git@github.com:lisa-lumos/SQL-notes.git
$ git push -u origin main  
$ git push
```














