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

Add existing project as repository

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


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU0MDg4NTkyNyw4NjA5MjEyNjldfQ==
-->