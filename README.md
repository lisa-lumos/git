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

## Commit files

Set up git with user name and email, also enable colored output in the terminal and use emacs:

```sh
lisa@mac ~/D/g/git-learning (main)> git config --global user.name "my-user-name"
lisa@mac ~/D/g/git-learning (main)> git config --global user.email "my-email@email.com"
lisa@mac ~/D/g/git-learning (main)> git config --global color.ui true
lisa@mac ~/D/g/git-learning (main)> git config --global core.editor emacs
```

Generate a new ssh key [ssh key doc]: 






 [//]: # (These are reference links)
    [ssh key doc]: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh>
 





