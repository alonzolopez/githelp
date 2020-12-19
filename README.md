# Git Commands
## Add a remote
[How to Add a New Remote to your Git Repo](https://articles.assembla.com/en/articles/1136998-how-to-add-a-new-remote-to-your-git-repo#:~:text=To%20add%20a%20new%20remote%2C%20use%20the%20git%20remote%20add,tab%20of%20your%20Git%20repo)


## Change a remote’s url
Changing a remote’s URL
## How to ignore files with .gitignore
Atlassian tutorial on .gitignore
## How to ignore files that are already being tracked 
(i.e. forgot to add them in the .gitignore and started tracking them)

[How to ignore files which are in repository?]()

[How to make Git "forget" about a file that was tracked but is now in .gitignore?]()
## Create a new branch
To create a new branch, first sync up to the master repo by running
```bash
git pull origin master
```
Then create a new branch named, for example “control” branch, using the following:
```bash
git branch control
```
And checkout (work on) the branch using 
```bash
git checkout control
```
We can now test changes on our local control branch. These changes should not be pushed to the master repo until they are fully functioning and validated.

## Tracking a Remote branch
[How to track a remote branch]()


## Delete a local branch
git branch -d <branch>

## Delete a remote branch
[How can I delete a remote branch in Git?]()
git push origin --delete <branch>
For example,
git push origin --delete experiment-setup
## Push changes from a new branch to the remote and create the branch on the remote
Before doing this, we can push this branch to the remote origin/control using the following commands:
> git push origin control:control
Following the format:
> git push <remote> <local-branch>:<remote-branch>
This pushes changes on the local control branch to the remote’s control branch.

## Pull changes from a new remote branch that you don’t have locally
To pull these changes, you need to create a local branch that tracks a remote branch using the following commands (or see the git docs regarding tracking branches)
> git fetch origin
> git checkout --track origin/control

## Check what branch you’re on by running
> git branch -a
You should see a star next to the local branch you’re on. Remote branches show up in red.

## Switching Branches
Now that you’re on the control branch, maybe you want to switch back to the master branch, or vice versa. Do that by running 
> git checkout master
Then check what branch you’re on by running 
> git branch -a

## Push to remote
Docs
To push to a remote branch from the branch you’re currently on (tutorial):
> git push origin <remote-branch>
So in our case:
> git push origin control

## Pull from remote
Docs
> git pull <remotename> <branchname>

## Merge branches
Git merge conflicts Atlassian tutorial
Resolving merge conflicts with binary files
Once you commit your changes to local repo, you just resolve differences:
git checkout --ours -- [path/to/file.filetype]
git checkout --theirs -- [path/to/file.filetype]
Still need to push to central repo 
Git Merge Atlassian Git Tutorials

## Undoing Changes
git reset --hard <commit-hash>

## Pulling Just One File
Forum answer: Is it possible to pull just one file in Git?
git fetch origin
git checkout <branch> -- <file_name>

Example:
git fetch origin
git checkout origin/control -- bbot/src/bbot/bbot_ik.py

## Reverting changes for just one file (safely)
Undo working copy modifications of one file in Git?
git checkout <branch> -- <file>
For example 
git checkout demo -- bbot/nodes/mixdrink
Reverts mixdrink to the last committed version on local branch demo

## Stashing Changes
Atlassian tutorial - git stash

## Install from Requirements files
Example requirements file
Use pip install -r example-requirements.txt to install

## Proxy
Set proxy
Remove proxy

## Miscellaneous
How to Force Git Pull to Override Local Files
Configure Git to use a proxy
How to make a Readme

$\lceil f \rceil$

