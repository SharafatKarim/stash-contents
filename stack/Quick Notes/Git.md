---
tags:
  - Software-Development
  - git
  - notes
Published: 2022-11-24
Last Updated: 2023-01-06T14:58
Author: https://www.notion.so/685c212b8dda43ae86b79d2ad364e212?pvs=21
Created: 2022-11-24T07:48
Public: true
Featured: false
---
# Initializing GIT

## Configuration

1) Name

`git config --global user.name "`_`Your Name`_`"`

2) Email

`git config --global user.email "`_`email@example.com`_`"`

> [!important]  
> Italic words in this note mean variable. You have to change ‘em!  

## Initialization

1) Initialize on a empty directory,

`git init`

2) Clone from a GitHub/ similar repository,

`git clone` `_repo-user/repo-name_`

3) Clone with all sub-modules,

`git clone --recurse-submodules` _`````````` ````````` ```````` ``````` `````` ````` ```` ``` `` `user/name` `` ``` ```` ````` `````` ``````` ```````` ````````` ``````````_

> [!important]  
> -j8 can be used to boost performance!  

4) For an already cloned repository,

`git submodule update --init --recursive`

# Working with GIT

## Commit

1) Check status

`git status`

2) Add a (file|folder) | Work → Stage

`git add` _`file|folder`_

> [!important]  
> file = file | folder = folder/  

3) Add everything (except files in the `.gitignore`)

`git add --all` or, `git add .`

4) Git commit, | Stage → Commit

`git commit -m "`_`message`_`"`

5) Git commit with tracked file changes(`git add -u`),

`git commit -am "`_`message`_`"`

> [!important]  
> git add . will track untracked files (not ignored) but git add-u won’t!  

## Reset

1) reset staged changes | Stage → Work

`git reset` `_file|folder_`

> [!important]  
> or, try git reset . to reset everything!  

## Restore

1) restore one file with `git restore` _`file/folder`_

2) restore everything with,

`git restore :/`

## Logging

1) Show the sequence of commits starting from the current one, in reverse chronological order of the Git repository in the current working directory:

`git log`

2) Show the history of a particular file or directory, including differences:

`git log -p` _`path/to/file_or_directory`_

3) Show an overview of which file(s) changed in each commit:

`git log --stat`

4) Show a graph of commits in the current branch using only the first line of each commit message:

`git log --oneline --graph`

5) Show a graph of all commits, tags and branches in the entire repository:

`git log --oneline --decorate --all --graph`

6) Show only commits whose messages include a given string (case-insensitively):

`git log -i --grep` _`search_string`_

7) Show the last N commits from a certain author:

`git log -n` _`number`_ `--author=`_`author`_

8) Show commits between two dates (**yyyy-mm-dd**):

`git log --before="`_`2017-01-29`_`" --after="`_`2017-01-17`_`"`

- Copyright
    
    https://github.com/tldr-pages/tldr
    

## Sub-module

1) First set it by,

`git submodule add https://github.com/`_``````````````` `````````````` ````````````` ```````````` ``````````` `````````` ````````` ```````` ``````` `````` ````` ```` ``` `` `user/repo-name` `` ``` ```` ````` `````` ``````` ```````` ````````` `````````` ``````````` ```````````` ````````````` `````````````` ```````````````_ _`path/`_

> You can track them from `.gitmodules` file (a hidden text file)  
> and to sync it’s update with the parent,  
> `cd` into it, `git pull` and then,  
>   
> `git add` in the parent.

## Large file

1) Install `**git-lfs**` first. Available on most of official repository of various Linux distributions.

2) set it up (**once per user**) by running,

`git lfs install`

> make sure file is tracked in the `.gitattributes` and add it in git.  
> For migrations  
> `git-lfs-migrate` [[link](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.adoc?utm_source=gitlfs_site&utm_medium=doc_man_migrate_link&utm_campaign=gitlfs)] can help you.

Find more from,

> [!info] Git Large File Storage  
> Download and install the Git command line extension.  
> [https://git-lfs.github.com/](https://git-lfs.github.com/)  

# Remote

## Branch

1) List all local branches

`git branch`

> [!important]  
> use -r for remote branches or, -a for all (remote + local)  

2) New branch

`git branch` _`branch-name`_

> [!important]  
> Use -M to move a branch, like, git branch -M main  

3) Change branch

`git checkout` _`branch-name`_

> [!important]  
> Not just branch, you can also trigger a previous commit!  

4) Deleting a branch

`git branch -D` _`branch-name`_

## Merge

1) Merge an another branch with the current one,

`git merge` `_another-branch_`

> [!important]  
> To fix errors, you may need, git merge main --allow-unrelated-histories  

## Sync

1) List all remote,

`git remote -v`

2) add remote,

`git remote add` _`url`_

3) remove remote,

`git remote remove` _`origin`_

4) push,

`git push -u` `_remote branch_`

> [!important]  
> -e will save remote and branch, for you so next time, just run, git push  

5) pull,

`git pull`