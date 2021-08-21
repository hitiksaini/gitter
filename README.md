# gitter
gitter is a info-project to use git and GitHub. 

## What is git and GitHub 
* Git is a version control system that lets you manage and keep track of your source code history.
* GitHub is a cloud-based hosting service owned by microsoft that lets you manage git repositories(contains all of your project's files and each file's revision history).

## Why I should even use it
GitHub is a website for developers and programmers to **collaboratively work on code.** The primary benefit of GitHub is its version control system, which allows for seamless collaboration without compromising the integrity of the original project.

## 

 
 
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

