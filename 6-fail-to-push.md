# Git Learning Notes - Part 6

## error: failed to push some refs to XXX

When multiple people work on the same repo, e.g., person A and B pulled from the same repo at the same time, and if person A added a new line into README.md and pushed to remote repo, and person B added a different new line into the same file locally, is person B push to remote repo, there will be an error: 

```sh
$ git push
To github.com:lisa-lumos/git-learning.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'github.com:lisa-lumos/git-learning.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

To resolve the error, need to run a `pull` request and integrate remote changes and local changes together: 

```sh
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
Unpacking objects: 100% (3/3), 681 bytes | 340.00 KiB/s, done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
From github.com:lisa-lumos/git-learning
   7b1fcd4..657f0ee  main       -> origin/main
hint: Pulling without specifying how to reconcile divergent branches is
hint: discouraged. You can squelch this message by running one of the following
hint: commands sometime before your next pull:
hint: 
hint:   git config pull.rebase false  # merge (the default strategy)
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint: 
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
Auto-merging 5-fork.md
CONFLICT (content): Merge conflict in 5-fork.md
Automatic merge failed; fix conflicts and then commit the result.
```

When I go to my code editor, I see: 

```
XXX...

After testing, you can push it back to your fork,  then can create a PR (pull request) against the original repo. 

<<<<<<< HEAD
Added from local machine. 
=======
Added from web UI. 

>>>>>>> 657f0ee01fc3a9ac7e828bef4ac54a4fad412c34
```

HEAD indicates current head pointer, the hash indicates changes from remote repo. 

Manually merge both: 

```
XXX...

Added from local machine. 
Added from web UI. 
```

And then could commit and push. 

```sh
$ git add .
$ git commit -m "XXX"
$ git push
```













