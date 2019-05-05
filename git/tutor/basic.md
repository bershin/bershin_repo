## Basic command Overview

### Starting with a fresh project with out existing source code

    $ pwd
    /User/bjohn
    $ mkdir projects
    $ cd  projects
    ##Create a new git repository
    $ git init fresh-project
    <git create a folder called fresh-project>
    $ cd fresh-project
    <This is the working directory>
    $ ls -al
    $ cd .git
    <.git is where the actual git repository lives>
    $ ls
    $ cd ..
    $ git status
    <Shows, we are in default master branch>
    <You are in initial commit>
    $ vim hipster.txt
    <write one paragraph>
    $ git status
    <
    $ git add hipster.txt
    $ git status
    $ git commit
    <Invoke the default editor>
    $ git status

> Note: root-commit means very first commit.
> Copt text from [hipster website](http://hipsum.co)

### Add existing project as repository

Get the source code from below website [initializr](http://initializr.com)

 1. select bootstrap 
 2. Download the zip file

```
$ pwd
/User/bjohn
$ cd  projects
$ unzip ~/Download/initializr-verekia-4.0.zip
$ mv initializr web-project
$ cd web-project
$ ls
$ git init
$ ls -al
$ cd .git
$ ls
$ cd ..
$ git status
<Analyse, branch, is that a initial commit, any untracked files>
$ git add .
$ git status
$ git commit -m "My first" commit, inline"
<Invoke the default editor>
$ git status
```
### Setup a project be no longer manage my git

    $ cd /User/bjohn/projects/web-project
    $ rm -rf .git

### Clone git repository
- http://bitly.com/git-start-web
- https://github.com/scm-ninja/starter-web

Fork to your github
Click clone or download and copy the url to clipboard

```
$ git clone https://github.com/scm-ninja/starter-web.git
$ cd starter-web
$ ls -la
$ git status
```

> **Note**: origin - Remote reference.

## Add commit pull & push
```
$ pwd
/User/bjohn
$ cd  projects/starter-web
$ vim hipster.txt
<write one paragraph>
$ git status
<file is not under git control>
$ git add hipster.txt
$ git status
<Says it is in staging area>
$ git commit
<Invoke the default editor>
$ git status
$ git pull origin master
$ git push origin master
```

## Tracked files

```
$ mate ~/.gitconfig
[user]
  name = john bershin
  email = bershin@gmail.com
[core]
  editor = mate -w
$ vim hipster.txt
<Append with second paragraph>
$ git commit -am "Adding more ipsum text"
$ git ls-files
<List of files that are tracked by git in the current directory>
$ vim newfile.txt
$ git ls-files
<Cannot find the file>
$ git status
$ git add newfile.txt
$ git ls-files
<Now you can see>
```
## Editing Files
```
$ vim hipster.txt
<Append extra paragraph>
$ git status
<See newfile.txt in staging area and hipster.txt in modified stage>
$ git commit -m "commited new file"
<This will commit only the newfile.txt>
$ git status
$ git add .
<Add modified hipster.txt in staging area>
$ git status
$ vim hipster.txt
<Append extra paragraph>
$ git status
<See hipster.txt in staging area as well as in modified stage>
$ git commit -am "add content to repository"
$ git status
```
## Recursive add
```
$ mkdir -p level1/level2/level3
$ cd level1
$ vim level1-file.txt
<Append some text>
$ cd level2
$ vim level2-file.txt
<Append some text>
$ cd level3
$ vim level3-file.txt
<Append some text>
$ cd ../../..
$ git status
<Do not show sub files and folders in untracked>
$ git add .
<Add the file recursively from this point forward>
$ git commit
```
## Backout changes
```
$ git status
<Clean working directory>
$ cd level1
$ vim level1-file.txt
<Have 2 paragraph, copy 1 more>
$ git status
<Modified file not indexed>
$ git add level1-file.txt
$ git status
<modified file indexed but not commited>
$ git reset HEAD level1-file.txt
<backout changes from staging area to working area>
$ git status
<level1-file.txt file is in unstage area>
$ cat level1-file.txt
<Still shows 3 paragraph>
$ git checkout -- level1-file.txt
$ git status
<Clean working directory>
$ cat level1-file.txt
<Shows 2 paragraph>
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTA4NDQ5MDEsMTYxMTQzODMyMCw2Mz
E2MDQ3NTcsLTM1MTYzNzE4NSw4NjA5MjEyNjldfQ==
-->