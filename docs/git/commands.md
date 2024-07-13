# Git commands

<!-- for Joplin users -->
<!-- ${toc} -->

### initialiser un projet

```sh
git init
```

### update the index

```sh
git add .
```

note:

-|-
`git add -A` | stages all changes
`git add .` | stages new files and modifications, without deletions (on the current directory and its subdirectories).
`git add -u` | stages modifications and deletions, without new files

note: `git add -A` is equivalent to `git add .; git add -u`.

([source](https://stackoverflow.com/a/572660))

### commit + message

> see [changelog](:/eb07fdb1821447c8bcbf1f9ed9dcb0a3)

```sh
git commit -m 'message'
```

### commit update

```sh
git commit -a -m 'message'
git commit -am 'message'
```

### log

```sh
git log
```

### add a new element

```sh
git add page.html
# or
git add .
```

### revert a commit

[how to revert a single file to a previous version?](https://stackoverflow.com/a/2734035)

```bash
git log path/to/file
# or git log -p path/to/file if commit msg not useful
# get the version of the file from the given commit
git checkout <commit> path/to/file
# and commit this modification
git commit
```

----------------------------------------------
GitHub

1st create a new repository on github
Tell github where you want to up files
git remote add origin https://github.com/ngenty/projectname.git
then push files
git push -u origin master

clone repository
git clone https://github.com/…

pull
git pull - origin master

upstream and sync to the master
see https://help.github.com/articles/configuring-a-remote-for-a-fork/

