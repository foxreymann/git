# What is Git?

# Distributed / decentralised

very easy branching

# Branching

![branching](./img/branching.png)

# Commit access

open source

# https://try.github.io/

$ mkdir git-test-repo
$ cd git-test-repo

initialize a Git repository

$ git init

The .git directory
On the left you'll notice a .git directory. It's usually hidden.
If you click it you'll notice it has all sorts of directories and files inside it. You'll rarely ever need to do anything inside here but it's the guts of Git, where all the magic happens.

$ git status

It's healthy to run git status often. Sometimes things change and you don't notice it.

$ touch one.txt
$ git status

staged:
Files are ready to be committed.

unstaged:
Files with changes that have not been prepared to be committed.

untracked:
Files aren't tracked by Git yet. This usually indicates a newly created file.

deleted:
File has been deleted and is waiting to be removed from Git.

$ git add one.txt

Staging Area:
A place where we can group files together before we "commit" them to Git.

$ echo line one >> one.txt

$ git status

$ git diff

$ git diff --staged

$ git add one.txt

$ echo line two >> one.txt

$ git add -A .

add all:
You can also type git add -A . where the dot stands for the current directory, so everything in and beneath it is added. The -A ensures even file deletions are included.

$ git commit -m "added one.txt"

$ git push

$ git remote add origin git@github.com:foxreymann/git-test-repo

# set upstream

One way to avoid having to explicitly do --set-upstream is to use the shorthand flag -u along-with the very first git push as follows:

$ git push -u origin local-branch

This sets the upstream association for any future push/pull attempts automatically.

$ vi ~/.gitconfig

$ vi ~/.bash_profile

### git reset

$ echo password > secret

$ git add secret
$ git status

You can unstage files by using the git reset command.

$ git reset secret

### gitignore

$ echo secret > .gitignore

$ git status

$ git add .

$ git commit -m "ignore the secret file"

### git checkout

$ echo 'wrong line' >> one.txt

Files can be changed back to how they were at the last commit by using the command: git checkout <target>. Go ahead and get rid of all the changes since the last commit for 'good'

$ cat one.txt
$ git checkout one.txt
$ cat one.txt

### branching and merging

$ git checkout -b clean_up // branch of current branch
$ git rm goodi
$ git add -A .
$ git commit -m "clean up"

$ git checkout master
$ git merge clean_up

$ git branch -D clean_up
$ git push

$ git branch file-two
$ git checkout file-two
$ echo

# merge conflict

branch
modify one
delete two
master
modify one
modify two
branch
merge master into the branch
make PR between branches on github

# git log

$ git log

By default, with no arguments, git log lists the commits made in that repository in reverse chronological order — that is, the most recent commits show up first. As you can see, this command lists each commit with its SHA-1 checksum, the author’s name and email, the date written, and the commit message.

A huge number and variety of options to the git log command are available to show you exactly what you’re looking for. Here, we’ll show you some of the most popular.

$ git log -p -2

$ gl -p -2

git log per file

$ git log one.txt

see all removed lines in a file

$ git log one.txt | grep ^-

$ git log --graph

see ~/.bash_aliases gl

 The -G flag allows you to search for all commits and only return commits and their files whose changes include that regexp. So it will look

Regex on Commits!! The -G flag allows your to run regex that search both changes in files and filenames and return only matching commits.

$ gl -p -G 'two'

### HEAD

### git reset

git reset --hard HEAD~2

git reset --soft HEAD~2

### git revert

Undo any commit.

$ git revert <SHA>

git revert will create a new commit that’s the opposite (or inverse) of the given SHA..

This is Git’s safest, most basic “undo” scenario, because it doesn’t alter history—so you can now git push the new “inverse” commit to undo your mistaken commit.

$ git log -p

$ git revert <SHA>

git revert changes on removed file

### git checkout

git checkout any file from any commit

### fork

A fork is a copy of a repository.

Used to:
- propose changes (make a pull request) to someone else's project
- use someone else's project as a starting point for your own idea.

Power of a fork: io.js story

Exrx:
Fork https://github.com/octocat/Spoon-Knife
Clone
change index.html
Make pull request
See pull request

### Continius Deployment

code, copy via ftp

### heroku

revert
new remote repository just for deployment

[manual](https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up)

$ apt search heroku
$ sudo apt install heroku
$ heroku login

fork https://github.com/heroku/node-js-getting-started.git

rename

$ git clone heroku-exrx
$ heroku local web
$ heroku apps:create heroku-exrx --region eu
$ git push heroku master
$ heroku logs --tail
$ npm i
$ heroku local web
$ npm install cool-ascii-faces

$ vi index.js


```javascript
const cool = require('cool-ascii-faces')
...
  .get('/cool', (req, res) => res.send(cool()))
```

$ git status
$ git add index.js package.json
$ git commit -m "add cool faces page'
$ git push
$ git push heroku master
$ heroku open cool
