# 1. Getting Started
## 1.1 About Version Control
Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.

## 1.2 A Short History of Git
skip

## 1.3 What is Git?
Git thinks of its data like a series of snapshots of a miniature filesystem. Every time you commit, or save the state of your project, Git basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. 

To be efficient, if files have not changed, Git doesn't store the file again, just a link to the previous identical file it has already stored. Git thinks about its data more like a stream of snapshots.

Most operations in Git need only local files and resources to operate - generally no information is needed from another computer on your network.

Everything in Git is check-summed before it is stored, and is then referred to by that checksum. This means it's impossible to change the contents of any file or directory without Git knowing about it. 

Git stores everything in its database not by file name but by the hash value of its contents.

When you do actions in Git, nearly all of them only add data to the Git database. It is hard to get the system to do anything that is not undoable, or to make it erase data in any way.

Git has 3 main states that your files can reside in:
1. Modified. You have changed the file but have not committed it to your database yet.
2. Staged. You have marked a modified file in its current version to go into your next commit snapshot.
3. Committed. The data is safely stored in your local database.

The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

The basic Git workflow goes like this:
1. You modify files in your working tree.
2. You selectively stage just those changes you want to be part of your next commit, which adds only those changes to the staging area.
3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

## 1.4 The Command Line
The command line is the only place you can run all Git commands - most of the GUIs implement only a partial subset of Git functionality for simplicity. Also, all users will have the command-line tools installed and available.

## 1.5 Installing Git
```sh
# If you don't have it installed already, it will prompt you to install it.
git --version
```

## 1.6 First-Time Git Setup
Customize your Git environment. You should have to do these things only once on any given computer; they'll stick around between upgrades. You can also change them at any time by running through the commands again.

Git comes with `git config` tool that lets you get/set config variables that control how Git looks/operates. These variables can be stored in 3 diff files:
1. `[path]/etc/gitconfig` file: Contains values applied to every user on the system and all their repos. Need to pass the option `--system` to r/w from this file. Need admin/su privilege.
2. `~/.gitconfig` or` ~/.config/git/config` file. User-specific. Need to pass the option `--global ` to r/w from this file. It affects all repos for the user.
3. `.git/config` file in the Git repo. Specific to that single repository. Optionally pass the option `--local` to r/w from this file, because it is the default. Need to cd to this repo first. 

Each level overrides values in the previous level. 

You can view all of your settings and where they are coming from using:
```sh
$ git config --list --show-origin
```

The first thing you should do when you install Git is to set your user name and email address. This is important, because every Git commit uses this information, and it's immutably baked into the commits you start creating:
```sh
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
Many of the GUI tools will help you do this when you first run them.

You can configure the default text editor that will be used when Git needs you to type in a message. If not configured, Git uses your system's default editor. If you want to use a different text editor, such as Emacs:
```sh
$ git config --global core.editor emacs
```

By default, Git will create a branch called `master` when you create a new repo with git init. From Git version 2.28 onwards, you can set a different name for the initial branch. To set `main` as the default branch name:
```sh
$ git config --global init.defaultBranch main
```

To check your configs:
```sh
$ git config --list
# user.name=John Doe
# user.email=johndoe@example.com
# color.status=auto
# color.branch=auto
# color.interactive=auto
# color.diff=auto
# ...
```

To check what Git thinks a specific key's value is::
```sh
$ git config user.name
# John Doe
```

## 1.7 Getting Help
skip

## 1.8 Summary
skip
