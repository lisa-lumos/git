# 2. Git Basics
## 2.1 Getting a Git Repository
You typically obtain a Git repository in one of two ways:
- Take a local directory that is currently not under version control, and turn it into a Git repository, or
- Cone an existing Git repository from elsewhere.

Initializing a repository in an existing directory:
```sh
$ cd /Users/user/my_project

# Create a new subdir named ".git", 
# that contains all of your necessary repository files 
# - a Git repository skeleton. 
$ git init

# begin tracking some files, and do an initial commit
$ git add *.c
$ git add LICENSE
$ git commit -m 'Initial project version'

```

Cloning an existing repository:
```sh
# Every version of every file for the history of the project is pulled down by default, when you run git clone
$ git clone https://github.com/libgit2/libgit2

# To clone the repository into a directory named something else:
$ git clone https://github.com/libgit2/libgit2 mylibgit

```

Git has a number of different transfer protocols you can use. The previous example uses the `https://` protocol, but you may also see `git://` or `user@server:path/to/repo.git`, which uses the SSH transfer protocol.

## 2.2 Recording Changes to the Repository
Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified/modified/staged. In short, tracked files are files that Git knows about.

Untracked files: any files in your working directory that were not in your last snapshot, and are not in your staging area. 

To determine which files are in which state:
```sh
$ git status
# On branch master
# Your branch is up-to-date with 'origin/master'.
# nothing to commit, working tree clean

$ echo 'My Project' > README
$ git status
# On branch master
# Your branch is up-to-date with 'origin/master'.
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)

#     README

# nothing added to commit but untracked files present (use "git add" to track)
```

You can see that your new "README" file is untracked - Git sees a file you didn't have in the previous snapshot (commit), and which hasn't yet been staged; Git won't start including it in your commit snapshots, until you explicitly tell it to do so. It does this so you don't accidentally begin including generated binary files or other files that you did not mean to include.

The `git add` command takes a path name for either a file or a directory; if it's a directory, the command adds all the files in that directory recursively.
```sh
# to begin tracking a new file
$ git add README

# now it shows it is staged to be committed
$ git status
# On branch master
# Your branch is up-to-date with 'origin/master'.
# Changes to be committed:
#   (use "git restore --staged <file>..." to unstage)

#     new file:   README

$ git status
# On branch master
# Your branch is up-to-date with 'origin/master'.
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)

#     new file:   README

# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)

#     modified:   CONTRIBUTING.md
```
"Changes not staged for commit" means that a file that is tracked has been modified in the working directory, but not yet staged.

`git add` is more like "add precisely this content to the next commit". Git stages a file exactly as it is when you run the `git add` command, not the modified version after you run the command.

Short status. New files that have been added to the staging area have an "A", modified files have an "M", new files that aren't tracked have a "??". "MM" means mixed stats, such as modified then staged then modified again.  
```sh
$ git status -s
#  M README
# MM Rakefile
# A  lib/git.rb
# M  lib/simplegit.rb
# ?? LICENSE.txt
```

Setting up a ".gitignore" file for your new repository before you get going is generally a good idea, so you don't accidentally commit files that you don't want in your Git repo. Ignoring files ".gitignore":
```sh
*.[oa] # ignore any files ending in .o or .a
*~ # ignore all files whose names end with a tilde
```

The rules for the patterns you can put in the ".gitignore" file:
- Blank lines, or lines starting with `#` are ignored.
- Standard glob patterns work, and will be applied recursively throughout the entire working tree.
- To avoid recursivity, start patterns with `/`.
- To specify a directory, end patterns with `/` .
- Negate a pattern by starting it with `!`.

Glob patterns are like simplified regex that shells use:
- A `*` matches zero or more characters; 
- `[abc]` matches any character inside the brackets (in this case a, b, or c);
- `?` matches a single character; 
- brackets enclosing characters separated by a hyphen `[0-9]` matches any character between them (in this case 0 through 9). 
- `**` matches nested directories; `a/**/z` would match `a/z`, `a/b/z`, `a/b/c/z`, and so on.

More examples:
```sh
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf

```

To see what you've changed but not yet staged, use `git diff`. If you've staged all of your changes, git diff will give you no output. `git diff --staged` to see what you have staged. 

To commit, run `git commit -m "my test commit"`. Every time you perform a commit, you're recording a snapshot of your project that you can revert to, or compare to later.

To remove a file from git tracking and from the disk, run `git rm my_file.txt`. To remove a file from git tracking but keep it in the disk, run `git rm --cached my_file.txt`. 

To rename a file, run `git mv file_from file_to`. 

## 2.3 Viewing the Commit History
```sh
# list of commits, newest first
git log

# list last 2 commits, show the difference
git log --patch -2

# see abbreviated stats for each commit (num of insertions, deletions for each file)
git log --stat

# list each commit in 1 line, with its commit message
git log --pretty=oneline

git log --since=2.weeks

git log -- path/to/file

```

## 2.4 Undoing Things
```sh
# make changes to a prv commit
# Only amend commits that are still local and have not been pushed somewhere. 
# Amending previously pushed commits and force pushing the branch will cause problems for your collaborators.
git commit --amend

# unstaging a staged file
git reset HEAD file_name_to_unstage.txt
git restore --staged file_name_to_unstage.txt

# unmodifying a modified file, to the last commit
# can be dangerous, because any local change you made to that file is gone
git checkout -- file_name_to_unmodify.txt
git restore file_name_to_unstage.txt

```

Anything that is committed in Git can almost always be recovered. Even commits that were on branches that were deleted or commits that were overwritten with an --amend commit can be recovered. However, anything you lose that was never committed is likely never to be seen again.

## 2.5 Working with Remotes
Remote repositories are versions of your project that are hosted on the Internet or network somewhere.

```sh
# to see which remote servers you have configured (origin is the default name)
git remote

# shows the URLs of the remote
git remote -v

# add a new remote
git remote add my-remote-short-name my-remote-url

# fetch from remote
# it only downloads the data to your local repository, so
# you have to merge it manually into your work when you're ready.
git fetch my-remote-short-name

# automatically fetch and then merge the remote branch into your current branch
git pull

# push to remote
git push my-remote-short-name my-branch-name
# git push origin master

# inspecting a remote
git remote show mmy-remote-short-name
# git remotes show origin

```

## 2.6 Tagging
Git has the ability to tag specific points in a repository's history as being important. Typically, people use this functionality to mark release points (v1.0, v2.0 and so on).

```sh
# list the existing tags, in alphabetical order
git tag

# list the tags using wildcard match
$ git tag -l "v1.8.5*"

```

## 2.7 Git Aliases



## 2.8 Summary





