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
* `git remote add origin <repo_link>` (get the repo_link by [creating a new repository](https://docs.github.com/en/get-started/quickstart/create-a-repo))
* `git add .`
* `git commit -m"first commit message"`
* `git push origin main`

Now you will see a dedicated webpage for your new project.

### 2) Had already done your project and now moving it to github

In this case you can create a new repository on github website as done in previous step and then export your files directly by configuring remote.

Set up git in your project directory as done before. Process in almost same for both these scenarios

`git remote add origin <new_repo_link>`

Now just add your changes to staging area(`git add`) and later push it to working directory.

## Basic git commands

### `git config --global`
Configure the author name and email address to be used with your commits. This is probably the first thing you will do while starting git:

`git config --global user.name "Hitik"`

`git config --global user.email your@mail.com`

### `git init`
Create a new local repository, basically adds git to your project directory.

### `git add`
Add one or more files to staging (index), you can specifically use `git add <filename>` or just do `git add .` this will add every **new or changed** file's.

### `git commit`
Commit changes to head (but not yet to the remote repository), this is like your signature and it means you are approving the changes done in your local version. 

But wait, `git commit` doesn't work? Yes! because it requires an important argument i.e, a **commit message** this is why **-m flag** is used while using cmd
It always a good idea to describe a good commit message so that others can know what you did.

### `git push`
Send changes to the master branch of your remote repository.

### `git pull`
Pull changes from remote to local (see [auto merge conflict](https://github.com/hitiksaini/gitter#auto-merge-conflict-commit) to pull the right way)

### `git clone`
Create a working copy of repository.

## Branching in GitHub

I'll be honest this feature of git is developer's best friend. After that you've done all that is said above I think you're ready to grasp this concept now. So, in simple words branching is nothing but **a copy of your production** which you can use for **fixing bugs, add or try new features** in your project application. When you create a branch of your project it literally copies each and every line from that point in repository and later you can mess around with the code without compromising production.

It's not only for messing around though :) you can merge your changes with the original copy(main) if you don't break the code and it still works :p 

Here's how you can check all present branches in a repository :

### `git branch`

It will show all available branches, you can shift to any of those(please be sure to ask your senior dev before cracking his code lol) use this cmd to switch

### `git checkout _branch_name`

Now everything you do any changes any commits will be on this branch of the project.
 
## Auto merge conflict commit 
When you do a `git pull` modifications from the remote branch are merged into your local branch and they might or might not have some conflicts with this local.

I suggest you to pull this way next time:

#### `git pull --rebase`

### Best way to avoid?
* Always `git pull` before you even start working + commit on milestones.(I personally use the same)

* If you are in a situation where someone else has already pushed some changes (commits) before you, use `git reset --hard origin/master` on your local copy. This should not cause any conflict.

### Again, why does this happens at first place?
When you add a commit to your local copy of a branch and then pulling upstream(remote) changes into this local branch, **since your local commits are not on the remote repository yet**, when `git pull` runs git merge origin/[branch] [branch], **it will automatically do a "recursive" merge and create a commit with the remote changes.** 

Now, when you push your changes up to remote repository, you end up with both a **merge from the remote integration branch into your local branch**, and a **merge from your local branch into the integration branch** 

## Setting up git for work & personal account (multiple access from cmd)
This will come handy when you want will have to manage your organisations repos with your work email gtihub account(yourname@company.com). It is possible to allow your cmd to act differently(use your work email instead of your personal github) whenever you are accessing a private repo of your company.

Go to your home directory you'll find `.gitconfig` change its content as following:

    [include]
            path = ~/git-personal.conf
    [includeIf "gitdir:~/Desktop/company_work/"]
            path = ~/git-work.conf

Note: "company_work" is a folder on your desktop(you can change path as per your needs) that will help git to separate your work from personal. This will keep all the work in one folder as well.

Now we will create these two conf files that we have mentioned above

`vim git-personal.conf` 
A editor will open now paste the content and change the details

    [user]
            name = hitiksaini
            email = hitik9045saini@gmail.com
            
`vim git-work.conf` 
Same for git-work.conf

    [user]
            name = hitik_companyName
            email = hitik.saini@company.in

Great! Now we have successfully separated the work and personal directory. Let's setup the SSH(Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username and personal access token at each visit) 


`cd ~./ssh`

Generate SSH key for Personal account
`ssh-keygen -t rsa -f "id_rsa_personal" -C "email_personal@gmail.com" -P "give_a_password"`

Generate SSH key for Work account
`ssh-keygen -t rsa -f "id_rsa_work" -C "email_work@company.com" -P "give_a_password"`

This will create 4 files in /ssh public and private x 2

Now run `cat id_rsa_personal.pub`
it will print a string this is your personal public ssh key add this to your github account. Go to <b>Add SSH Key page</b> give title as you wish and paste this string.
Repeat the same for your work email github account and paste contents of `id_rsa_work.pub`

One last step is to configure these settings. 

In the same directory(~/.ssh)

`vim config` 
And paste the settings as:

    #personal
    Host github.com
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa_personal

    #work
    Host github-work
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_rsa_work

And Done!!
Next time if you want to clone a private repo from your companies github account do it as:
### `git clone github-work:company/repo_name.git`

