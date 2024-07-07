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



## 1.5 Installing Git



## 1.6 First-Time Git Setup



## 1.7 Getting Help



## 1.8 Summary



