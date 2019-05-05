## Basic command Overview

### Starting with a fresh project

    $ pwd
    /User/bjohn
    $ mkdir projects
    $ cd  projects
    $ git init fresh-project
    $ cd fresh-project
    $ ls -al
    $ cd .git
    $ ls
    $ cd ..
    $ git status
    <Analyse>
    $ vim hipster.txt
    <write one paragraph>
    $ git status
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
Tracked files


Editing Files

Recursive add

Backout changes
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgyODY2MDQwMSw4NjA5MjEyNjldfQ==
-->