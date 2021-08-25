### Suggestion 
For better readability, use [webpage](https://hitiksaini.github.io/gitter/) version. Thanks!

### Hey there!
So you’ve just decided to use GitHub for your upcoming projects but don’t know what tf is going on with all those commands.

gitter is a info-project to use git and GitHub. These commands are good to get you started and even collaborate with your friends in projects.

## What is git and GitHub 
* Git is a version control system that lets you manage and keep track of your source code history.
* GitHub is a cloud-based hosting service owned by microsoft that lets you manage git repositories(contains all of your project's files and each file's revision history).

## Why should you even use it
GitHub is a website for developers and programmers to **collaboratively work on code.** The primary benefit of GitHub is its version control system, which allows for seamless collaboration without compromising the integrity of the original project.


Let's start from the beginning, you can be in two different scenarios :

### 1) Starting fresh with no code/file/project
One thing you can do is clone someone else's code and make a local copy of it in your system for instance let's clone this repo: https://github.com/hitiksaini/gitter.git

* `git clone https://github.com/hitiksaini/gitter.git`

And you're done! Now you can make changes to this copy you've just cloned. Also, if these changes are impactful you can create a PR(Pull Request) where in I(owner) can review your changes and merge them into the remote repository and once I accept your PR you become contributor.

Secondly, if you don't want to clone you can make a new one

* `git init`
* `git add .`
* `git commit -m"first commit message"`
* `git remote add origin <repo_link>`
* `git push origin main`

### 2) Had already done your project and now moving it to github

In this case you can create a new repository on github website and then import your files directly with remote command 

Set up git in your project directory as done before. Process in almost same for both these scenarios

`git remote add origin <new_repo_link>`

## Basic git commands

### `git config --global`
Configure the author name and email address to be used with your commits. This is probably the first thing you will do while starting git:

`git config --global user.name "Hitik"`

`git config --global user.email your@mail.com`

### `git init`
Create a new local repository

### `git add`
Add one or more files to staging (index)

### `git commit`
Commit changes to head (but not yet to the remote repository):

### `git push`
Send changes to the master branch of your remote repository:

### `git pull`

### `git clone`
Create a working copy of a local repository:
 
 
## Auto merge conflict commit 
When you do a `git pull` modifications from the remote branch are merged into your local branch and they might or might not have some conflicts with this local.

I suggest you to pull this way next time:

#### `git pull --rebase`

### Best way to avoid?
* Always `git pull` before you even start working + commit on milestones.(I personally use the same)

* If you are in a situation where someone else has already pushed some changes (commits) before you, use `git reset --hard origin/master` on your local copy. This should not a cause a conflict.

### Again, why does this happens at first place?
When you add a commit to your local copy of a branch and then pulling upstream(remote) changes into this local branch, **since your local commits are not on the remote repository yet**, when `git pull` runs git merge origin/[branch] [branch], **it will automatically do a "recursive" merge and create a commit with the remote changes.** 

Now, when you push your changes up to remote repository, you end up with both a **merge from the remote integration branch into your local branch**, and a **merge from your local branch into the integration branch** 

