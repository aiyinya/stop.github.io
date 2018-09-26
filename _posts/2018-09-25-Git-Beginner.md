---
layout:     post
title:      Git Beginner
subtitle:   History Blogs @ 2015/10/1
date:       2018-09-25
author:     Xin YAO
catalog: true
tags:
    - git
---

<!-- MarkdownTOC -->

- [What is a git](#what-is-a-git)
- [Preparation](#preparation)
  - [History](#history)
  - [Install](#install)
  - [configuration](#configuration)
- [Begin](#begin)
  - [init the git](#init-the-git)
  - [stream](#stream)
- [File Operations](#file-operations)
  - [Add \(git status to check\)](#add-git-status-to-check)
  - [Remove\(git status to check\)](#removegit-status-to-check)
  - [Rename\(git status to check\)](#renamegit-status-to-check)
- [Rollback](#rollback)
  - [git diff to check to change](#git-diff-to-check-to-change)
  - [Warning](#git reset)
  - [.gitignore](#gitignore)
  - [.gitkeep](#gitkeep)
  - [Other options](#other-options)
- [Branch](#branch)
  - [branch is needed, cheap, try](#branch-is-needed-cheap-try)
  - [operations](#operations)
  - [Merge](#merge)
  - [stash](#stash)
- [Remote \(link to the github or others\)](#remote-link-to-the-github-or-others)
  - [Set up a github account](#set-up-a-github-account)
  - [password caching](#password-caching)

<!-- /MarkdownTOC -->


<a id="what-is-a-git"></a>
## What is a git
     git 帮助我们进行代码的版本控制，我于2015/10/1花费一天时间学习一个关于git的视频,然后再参考几篇博客,将git的使用方法全部弄清楚。let's begin!

<a id="preparation"></a>
##Preparation

<a id="history"></a>
### History
1. *SCCS Source Code Control System *
      * 1972， closed source, free with Unix
2. *RCS Revision Control System *
      * 1982， open source.
3. *CVS Concurrent Versions System *
      * 1986 - 1990, open source
4. *SVN * 
      * 2000, open source
5. *BitKeeper SCM*
      *  distributed version
6. *GIT * 
      *  github come out
<a id="install"></a>
### Install
>参考官网的安装方法    —— <a href="https://git-scm.com" target="_blank"> [git web]

1. download the tar.gz or some package[your linux]
2. tar zxvf *.tar.gz
3. /configure
4. make && make install
5. finish.
or you can try:
* apt-get install git
* yum install -y git
* pacman -S git
<a id="configuration"></a>
###configuration
1. git config --global user.name [your name]
2. git config --global user.email [your email]
3. git config --global core.editor "vim"
4. git config --global color.ui true
5. use bash config
   * wget https://github.com/git/git/raw/master/contrib/completion/git-completion.bash
  * ls
  * mv git-completion.bash ~/.git-completion.bash
  * add to .bashrc that if exist this bash, source it.
6. help 
<a id="begin"></a>
## Begin
<a id="init-the-git"></a>
### init the git
1. mkdir dir1
2. cd dir1
3. git init
4. add one file (make change)
5. git add . (add change)
6. git commit -m "some word" (commit change)
7. git log -n/ --since/ --until/ --grep
<a id="stream"></a>
### stream
working -add file- staging index -commit- repositiry

<a id="file-operations"></a>
## File Operations
<a id="add-git-status-to-check"></a>
### Add (git status to check)
   * git add .
   * git commit -m ""
   * git diff
   * git commit -ma ""
<a id="removegit-status-to-check"></a>
### Remove(git status to check)
* git rm filename
* git commit -m ""
<a id="renamegit-status-to-check"></a>
### Rename(git status to check)
* git add file
* git rm file
* git commit -m ""
* or you can use git mv file1 file2
<a id="rollback"></a>
## Rollback
<a id="git-diff-to-check-to-change"></a>
### git diff to check to change
1. git checkout -- file(before add)
    it can return the status of the workspace.
2. git reset HEAD file (after add)
   * unstage the file -> before add
   * git checkout -- file
3. git (after commit)
   * find the Hash value of commit
   * git comment --amend append to the same commit
   * git diff --staged
   * return the commit status
   > git checkout [commit hash] -- file

<a id="git reset"></a>
### Warning [git reset]
1. --soft not change staging index & workspace
2. --mixed(default) change staging & not workspace
3. --hard change staging & change workspace
   > usage : git reset --soft [commit hash]
git reset HEAD file
-n try to do -f force to do
<a id="gitignore"></a>
### .gitignore
it can help us to ignore some file or dir
> reference :
 1. help.github.com/articles/ignoring-files
 2. github.com/github/gitignore
git config --global core.excludesfile pathtofile
* git rm --cached file 
<a id="gitkeep"></a>
### .gitkeep
git log --oneline/ --graph/ --all/ --decorate
<a id="other-options"></a>
### Other options
* git show [hash]
* git diff [hash] & git diff [hash1]..[hash2]
<a id="branch"></a>
## Branch
<a id="branch-is-needed-cheap-try"></a>
### branch is needed, cheap, try
1. try new ideas
2. isolate the workspace
3. fast context switching
<a id="operations"></a>
### operations
> * git branch
> * **create** -> git branch new_branch_name
> * **switch** -> git checkout branch_name
> * git checkout -b new_branch_name
> * git diff [branch1]..[branch2] (use --color-words)
> * git branch --merged
> * git branch -m old_name new_name (--move)
> * git barnch -d(--delete) name (-D to delete a non-empty branch)
> * prompt
>   1. export PS1='\$(__git_ps1 "(%s)") > '
>   2. export PS1='\W\$(__git_ps1 "(%s)") > '
>   3. export PS1=\$PS1'\$(__git_ps1 "(%s)") > ' (it's cool !)

Attantion: barnch is a stack mode, current branch can't be delete
<a id="merge"></a>
### Merge 
> * git merge exist_branch
> * git branch --merged
> * conflict
>    * 1. change by yourselt
>    * 2. git log --graph --oneline --all --decorate
>    * 3. git mergetool --tool= 

Attention: 
* keep lines short
* commits small focused
* merge often
<a id="stash"></a>
### stash
1. git stash save "changed mission ..."
2. git stash list 
3. git stash show stash@{0}  (you may use -p option)
4. git stash apply
5. git stash pop
6. git stash drop stash@{0}
<a id="remote-link-to-the-github-or-others"></a>
## Remote (link to the github or others)
![Remote Git](http://img.blog.csdn.net/20151001194223393)
Easily, this can be changed to
![Remote Git now](http://img.blog.csdn.net/20151001194446158)
<a id="set-up-a-github-account"></a>
### Set up a github account
1. you set up a account
2. Create a repository
3. look at the code following
```
echo #  >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/[User account]/[project name].git
git push -u origin master
```
* you can easy use 
       git remote rm origin
* git branch -a/-r
* git push -f
* git fetch
    * fetch before work
    * fetch before push
    * fetch often
* git pull = git fetch + git merge
* git push origin :your branch
* git push origin [--delete] branch
> [远程分支的使用]
> git checkout -b [new_branch]
> (make some change)
> git commit -am "word"
> git push [远程仓库名] [远程分支名(new_branch)]
<a id="password-caching"></a>
### password caching
[Password Caching](https://help.github.com/articles/caching-your-github-password-in-git/)
or save the ssh key.
