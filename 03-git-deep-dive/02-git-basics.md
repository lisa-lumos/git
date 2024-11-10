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



## 2.3 Viewing the Commit History



## 2.4 Undoing Things



## 2.5 Working with Remotes



## 2.6 Tagging



## 2.7 Git Aliases



## 2.8 Summary





