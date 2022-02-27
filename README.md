# git-learning

## Clone
```sh
lisa@mac ~/D/git> git clone https://github.com/lisa-lumos/git-learning.git
Cloning into 'git-learning'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (6/6), done.
```

After cloning is done, go to the repo folder: 

```sh
lisa@mac ~/D/git> cd git-learning/
lisa@mac ~/D/g/git-learning (main)>
```
## Show status

After modifying README.md file, to show the status of new changes: 

```sh
lisa@mac ~/D/g/git-learning (main)> git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
lisa@mac ~/D/g/git-learning (main)> 
```
After adding a new file `README_NEW.md` in folder `/Users/lisa/Desktop/git/git-learning`, show the status:

```sh
lisa@mac ~/D/g/git-learning (main)> git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README_NEW.md

no changes added to commit (use "git add" and/or "git commit -a")

```

To let git know (begin to track) this new file, or all the files in current directory, run: 

```sh
lisa@mac ~/D/g/git-learning (main)> git add .
lisa@mac ~/D/g/git-learning (main)> git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   README.md
	new file:   README_NEW.md

```

## Commit changes

Commit changes locally: 

```sh
lisa@mac ~/D/g/git-learning (main)> git commit -m "title of my commit" -m "description of my commit"
[main 615cd52] title of my commit
 Committer: XXXX <XXX@XXX.local>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 2 files changed, 39 insertions(+), 1 deletion(-)
 create mode 100644 README_NEW.md
```

(This step is optional) Set up git with user name and email, also enable colored output in the terminal and use emacs:

```sh
lisa@mac ~/D/g/git-learning (main)> git config --global user.name "my-user-name"
lisa@mac ~/D/g/git-learning (main)> git config --global user.email "my-email@email.com"
lisa@mac ~/D/g/git-learning (main)> git config --global color.ui true
lisa@mac ~/D/g/git-learning (main)> git config --global core.editor emacs
```

Generate a new ssh key (references: [ssh key documentation]). 

```sh
lisa@mac ~/D/g/git-learning (main)> ssh -T git@github.com
Hi lisa-lumos! You've successfully authenticated, but GitHub does not provide shell access.
```

Reset origin url to avoid being asked username and password (references [remote repo documentation]):

```sh
lisa@mac ~/D/g/git-learning (main)> git remote set-url origin git@github.com:lisa-lumos/git-learning.git
```

Otherwise have the following problem: 

```sh
lisa@mac ~/D/g/git-learning (main)> git push origin main
Username for 'https://github.com': lisa-lumos
Password for 'https://lisa-lumos@github.com': 
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/lisa-lumos/git-learning.git/'
```

To push to remote repository: 

```sh
lisa@mac ~/D/g/git-learning (main)> git push origin main
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 1.65 KiB | 1.65 MiB/s, done.
Total 8 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To github.com:lisa-lumos/git-learning.git
   b0ca341..73e0b5c  main -> main
```

Now the new changes can be seen on github website. 

## Summary

To sum up, here are all the commands by far: 
```sh
git add .
git commit -m "title of my commit" -m "description of my commit"
git push origin main
```

 [//]: # (These are reference links)
    [ssh key documentation]: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh>
	[remote repo documentation]: <https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#about-remote-repositories>
 





