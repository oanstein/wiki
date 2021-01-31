# wiki
Wiki for Ruby on Rails and Nuxt.js https://github.com/oanstein/wiki/wiki

- [Ubuntu](https://github.com/oanstein/wiki/tree/master#ubuntu)
- [Ruby on Rails](https://github.com/oanstein/wiki/tree/master#ruby-on-rails)
- [Git Commands](https://github.com/oanstein/wiki/tree/master#git-commands)


# Ubuntu
## Cloud9
### Install the Cloud9 CLI

@source https://cloud9-sdk.readme.io/docs/the-cloud9-cli

`npm install -g c9`

***

## Check disk space usage
*Check disk space usage** with http://lintut.com/ncdu-check-disk-usage/

`ncdu` Check current folder and subfolder

`sudo ncdu -x /` Check all files in workspace

`bundle clean --force` will remove old gems (or older versions of
currently-used gems) previously installed, but not currently being used in your
current Gemfile.lock manifest.

`yarn cache clean <module_name>` Clear the global cache;
https://yarnpkg.com/lang/en/docs/cli/cache/#toc-yarn-cache-clean

***

## Clean up Linux
```
sudo apt-get update        # Fetches the list of available updates
sudo apt-get upgrade       # Installs some updates; does not remove packages
sudo apt-get full-upgrade  # Installs updates; may also remove some packages, if needed
sudo apt-get autoremove    # Removes any old packages that are no longer needed
````

`sudo apt-get update && sudo apt-get autoclean && sudo apt-get clean && sudo apt-get autoremove`

# Ruby on Rails
## Database
### DB Development: Reset
    rails db:rollback STEP=100

OR (with reset)

    rails db:migrate:reset
    rails db:seed:development:users_admin

< manually upload default avatars >

    rails db:seed

***

### DB Test: problem enum is nill OR test db full of garbage
Check for pending migrations and load the test schema

    rails db:test:prepare

Recreate the test database from the current schema.rb

    rails db:test:load

****

### problem: PG::ConnectionBad -> restart pg

    sudo service postgresql restart

***
***

# Git Commands
## [Git Overwrite master with branch](https://stackoverflow.com/questions/30105210/git-overwrite-master-with-branch)

`git branch -f master dev_branch` will rewrite local master branch.

`git push remote +dev_branch:master` will rewrite remote branch.

***

## Git `main`
Using 'master' as the name for the initial branch. This default branch name
is subject to change. To configure the initial branch name to use in all
of your new repositories, which will suppress this warning, call:

    git config --global init.defaultBranch <name>
 
Names commonly chosen instead of 'master' are 'main', 'trunk' and
'development'. The just-created branch can be renamed via this command:
 
    git branch -m <name>

## [How do I properly force a Git push?](https://stackoverflow.com/questions/5509543/how-do-i-properly-force-a-git-push)

Just do:

    git push origin <your_branch_name> --force

or if you have a specific repo:

    git push https://git.... --force

This will delete your previous commit(s) and push your current one.

It may not be proper, but if anyone stumbles upon this page, thought they might want a simple solution...

### Short flag

Also note that `-f` is short for `--force`, so

    git push origin <your_branch_name> -f

will also work.

***

## [Create Git Aliases](https://git-scm.com/book/tr/v2/Git-Basics-Git-Aliases)

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

git config --global alias.last 'log -1 HEAD'
```

`git push -u origin froala-editor` *Push branch* to origin (froala-editor)

`git checkout -b modify-README` Switched to a *new branch* 'modify-README'

`git branch -m <oldname> <newname>` *Rename* a branch while pointed to *any* branch

`git branch -m <newname>` *Rename* the *current* branch

`git branch -d the_local_branch` *Delete* local branch

`git commit --amend -m "New commit message"` *Amending* (rename) the most recent *commit message*

`git push <remote> <branch> -f` *Changing* the message of a *commit* that you've *already pushed* to your remote branch

***

## How do I rename a local Git branch?

If you want to rename a branch while pointed to any branch, do:

    git branch -m <oldname> <newname>

If you want to rename the current branch, you can do:

    git branch -m <newname>

A way to remember this, is `-m` is for "move" (or `mv`), which is how you rename files.

***

## [Delete a branch (local or remote)](https://makandracards.com/makandra/621-git-delete-a-branch-local-or-remote)

`git branch -d the_local_branch`
To delete a local branch

`git push origin :the_remote_branch`
To remove a remote branch (if you know what you are doing!)

`git push origin --delete the_remote_branch`
or simply use the new syntax (v1.7.0)

## Authorize new App (Permission Denied)
https://stackoverflow.com/questions/2643502/how-to-solve-permission-denied-publickey-error-when-using-git

## Generating a new SSH key and adding it to the ssh-agent
https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

***

## How to change your Git editor
There are two ways in which this can be done. The first is via the terminal; this is useful if you want your editor to be Nano, for example. The command to do this is `git config --global core.editor "nano"`. You can change the highlighted section with your editor of choice!

Another way to do this is to edit the `.gitconfig` file in your `home` directory. The location of this file depends on the operating system you're using.
