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
    <Shows the untracked files>
    $ git add hipster.txt
    <Add to git index/staging area>
    $ git status
    <Shows changes to be commited>
    $ git commit
    <Invoke the default editor>
    <Shows the SHA1 hashcode unique to this commit>
    $ git status

> Note: root-commit means very first commit of this repository.
> Copt text from [hipster website](http://hipsum.co)

### Add existing project as Git repository

Get the source code from below website [initializr](http://initializr.com)

 1. select bootstrap.
 2. Choose all filed.
 3. Download the zip file
 
```
$ pwd
/User/bjohn
$ cd  projects
$ unzip ~/Download/initializr-verekia-4.0.zip
## Rename the folder to look like a real project.
$ mv initializr web-project
$ cd web-project
$ ls
## Git will initialize a new repo using the current folder as working directory.
$ git init
$ ls -al
$ cd .git
$ ls
$ cd ..
$ git status
<Analyse, branch, is that a initial commit, any untracked files>
$ git add .
<Period will recurcively add all files as part of this project>
$ git status
$ git commit -m "My first" commit, inline"
<Invoke the default editor>
$ git status
```
### Setup a project be no longer manage my git

    $ cd /User/bjohn/projects/web-project
    $ rm -rf .git

> Still we will have all files inside the project folder.

### Clone git repository
- http://bitly.com/git-start-web
- https://github.com/scm-ninja/starter-web

> Fork any of those repository to your github

Click clone or download and copy the url to clipboard
```
$ git clone https://github.com/scm-ninja/starter-web.git
$ cd starter-web
$ ls -la
$ git status
```

> **Note**: origin - Remote reference to the github repository.

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
<Head of orgin/master by 1 commit>
$ git pull origin master
<Best practice>
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
<Applicable only for tracked file>
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
<This will commit only the newfile.txt, i.e files from staging area>
$ git status
$ git add hipster.txt
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
<Add the file recursively from this point forward to the git index>
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
#Make the file same as last commited,with 2 paragraph
$ git checkout -- level1-file.txt
$ git status
<Clean working directory>
$ cat level1-file.txt
<Shows 2 paragraph>
```

## Renaming and moving files
```
$ cd level1/level2/level3
$ ls
$ git status
<Nothing to commit>
$ git mv level3-file.txt level3.txt
$ ls
< git renamed the file in OS level>
$ git status
<Git staged but not commited>
$ git commit -m "renaming level3 file"
<Best Practise: Rename the file before making changes>
```

### Rename the file in OS level (Bash Command)

```
$ cd level1/level2
$ ls
$ git status
$ mv level2-file.txt level2.txt
$ ls
$ git status
< Git sees this as two operation, delete and add>
$ git add -A
<Recursily add and files including renamed files>
$ git status
$ git commit
<Shows the renamed confidence level as well>
```

### Rename the file in Git level

```
$ cd level1/level2
$ ls
$ git status
$ git mv level2.txt 2.txt
$ ls
$ git status
<Staged the file>
$ git mv 2.txt level2.txt
$ ls
<OS level the rename has happened>
$ git status
<Clean WD>
```

### Move the file to another directory using Git

```
$ cd level1/level2
$ ls
$ git status
$ git mv level2.txt level3/
$ ls
<File no longer exist>
$ cd level3
$ ls
$ git status
$ cd ..
$ git status
$ git commit
```

### Move the file to another directory using OS command

```
$ cd level3/
$ ls
$ git status
$ mv level2.txt ..
$ ls
$ cd ..
$ ls
$ git status
<Looks like we deleted and created a new file>
$ git add -A
$ git status
$ git commit
$ cd ..
$ cd level3/
$ ls
$ git status
```

### Rename the file using GUI
Rename the file using right click
```
$ cd level1/
$ ls
$ git status
<Delete and add>
$ git add level1.txt
$ git add -u
<Update the git index>
$ git commit
$ git status
```

## Delete Files in git

### Delete file not tracked by git

```
$ git status
$ mate doomed.txt
$ ls
$ git status
<See the untracked file>
$ git rm doomed.txt
<Git complain it can`t match the file>
$ rm doomed.txt
$ ls
<File is gone>
$ git status
<Clean>
```

### Delete file tracked by git

```
$ git ls-files
<See the newfile.txt>
$ ls
<See the newfile.txt>
$ git rm newfile.txt
$ ls
<Cannot see the newfile.txt>
$ git status
<Git staged the file>
$ git commit -m "Deleting new file"
$ git status
$ ls
```

### Backout a staged deletion

```
$ ls
<Hipster.txt>
$ git ls-files
$ git rm hipster.txt
$ ls
<removedfrom the working directory>
$ git status
<Deletion is staged>
$ git reset HEAD hipster.txt
<Unstaged the deletion>
$ git status
$ git checkout -- hipster.txt
$ ls
<Can locate hipster.txt>
$ git status
<Clean WD>
$ ls
$ rm hipster.txt
$ ls
$ git status
$ git add -A
$ git status
<Clean WD>
```

### Delete file not tracked by git

```
$ ls
$ rm -rf level1
$ ls
$ git status
<See all the untracked file inside the folders>
$ git add -A
$ git status
$ git commit -m "deleteting level1 and all children"
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3Mzc4MDU3NDMsLTQ0OTE1MDc0LDc3Nz
UzMTAzNiwxMzM5NzA2NTg5LDE3NzAwNzQzOTEsMTUzODM5MDQx
LDgyOTUyNzg0OSwxMzA1MjI5MTAyLDIxMTg0MTUyOTksMTkzOD
c3MDQ4MywyNzQ3NjU3MzcsMTAwMDg0MzgwMiwxNjExNDM4MzIw
LDYzMTYwNDc1NywtMzUxNjM3MTg1LDg2MDkyMTI2OV19
-->