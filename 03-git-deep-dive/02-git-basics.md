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







## 2.3 Viewing the Commit History



## 2.4 Undoing Things



## 2.5 Working with Remotes



## 2.6 Tagging



## 2.7 Git Aliases



## 2.8 Summary




