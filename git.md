# Git

## Concepts

- Version Control (VS): a system that allows you to control versions of files and changes made to it in time. 
    - Centralized: a single server contained all the versioned files, when people check out files they only have that snapshop
    - Distributed: every local repository contains the fully history of changes, every checkout is a full backup of all the data

- Three states in git:
    - committed: data is stored in you local database
    - modified: you have changed the file but have not committed it to your database yet
    - staged: means you have marked a modified file in its current version to go into your next commit snapshop
- Three main sections in git:
    - git directory: where git stores the metadata and object database
    - working directory: a single checkout of one version of the project, these files are pulled out of the compressed database in the git directory and placed on disk for you to use or modify
    - staging area: a file that stores info about what will go into your next commit
- Git workflow:
    - you modify files in you working directory
    - you stage the files, adding snapshots of them to your staging area
    - you do a commit, which stores the files in the staging area permanently to your git directory

### Getting help

- `git help <verb>`
- `git <verb> --help`
- `man git-<verb>`

### git config

- git config files:
    - `/etc/gitconfig` file contains values for every user on the system (`--system` option to git config)
    - `~/.gitconfig` specific to your user (`--global` option)
    - `.git/config` config file in you Git directory is specific to that repository
  
- Commands:
    - `git config --list`: list settings
    - `git config --list --global`: list global settings
    - `git config user.name`: shows the config
    - `git config --global user.name "Name"`
    - `git config --global user.email email@email.com`
    - `git config --global core.editor vim`
    - `git config --global core.pager cat`

### git status
- `git status`
- `git status -s` or `git status --short`
    - left column (staging area), right column (working tree)
    - `??` untracked files
    - `A` added to staging area
    - `M` modified files
    - ...

### git diff
- `git diff`: show changes that are still unstaged
- `git diff --cached` or `git diff --staged`: what you've staged so far
- `git difftool`: using a tool to see git diffs
  - `git config --global diff.tool vimdiff : config vimdiff as default tool
  - `git difftool -t vimdiff`: select a tool to use in diff

### git commit
- `git commit -v`: show diffs before commit
- `git commit -m "<commit message>"`: commit without openning the editor

### git rm
- `git rm <filename>`: remove from staging area and working directory (delete the file)
- `git rm <filename> -f`: force removal
- `git rm <filename> --cached`: remove from staging area only and keep the file

### git mv
- `git mv file_from file_to`: rename a file
- equivalent to:
    ```bash
    mv README.md README
    git rm README.md
    git add README
    ```
