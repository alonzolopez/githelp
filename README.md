# Git Commands
## Add a remote
[How to Add a New Remote to your Git Repo](https://articles.assembla.com/en/articles/1136998-how-to-add-a-new-remote-to-your-git-repo#:~:text=To%20add%20a%20new%20remote%2C%20use%20the%20git%20remote%20add,tab%20of%20your%20Git%20repo)


## Change a remote’s url
[Changing a remote’s URL](https://help.github.jp/enterprise/2.11/user/articles/changing-a-remote-s-url/)
## How to ignore files with .gitignore
[Atlassian tutorial on .gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore)
## How to ignore files that are already being tracked 
(i.e. forgot to add them in the .gitignore and started tracking them)

[How to ignore files which are in repository?](https://stackoverflow.com/questions/7231608/how-to-ignore-files-which-are-in-repository)

[How to make Git "forget" about a file that was tracked but is now in .gitignore?](https://stackoverflow.com/questions/1274057/how-to-make-git-forget-about-a-file-that-was-tracked-but-is-now-in-gitignore)
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
[How to track a remote branch](https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch)


## Delete a local branch
```bash
git branch -d <branch>
```

## Delete a remote branch
[How can I delete a remote branch in Git?](https://www.git-tower.com/learn/git/faq/delete-remote-branch)
```bash
git push origin --delete <branch>
```
For example,
```bash
git push origin --delete experiment-setup
```

## Push changes from a new branch to the remote and create the branch on the remote
Before doing this, we can push this branch to the remote origin/control using the following commands:
```bash
git push origin control:control
```
Following the format:
```bash
git push <remote> <local-branch>:<remote-branch>
```
This pushes changes on the local control branch to the remote’s control branch.

## Pull changes from a new remote branch that you don’t have locally
To pull these changes, you need to [create a local branch that tracks a remote branch using the following commands](https://stackoverflow.com/questions/9537392/git-fetch-remote-branch) (or see the [git docs regarding tracking branches](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#_tracking_branches))
```bash
git fetch origin
```
```bash
git checkout --track origin/control
```

## Check what branch you’re on by running
```bash
git branch -a
```
You should see a star next to the local branch you’re on. Remote branches show up in red.

## Switching Branches
Now that you’re on the control branch, maybe you want to switch back to the master branch, or vice versa. Do that by running 
```bash
git checkout master
```
Then check what branch you’re on by running 
```bash
git branch -a
```

## Push to remote
[Docs](https://help.github.com/en/github/using-git/pushing-commits-to-a-remote-repository)
To push to a remote branch from the branch you’re currently on (tutorial):
```bash
git push origin <remote-branch>
```
So in our case:
```bash
git push origin control
```

## Pull from remote
Docs
```bash
git pull <remotename> <branchname>
```

## Merge branches
[Git merge conflicts Atlassian tutorial](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)
[Resolving merge conflicts with binary files](https://medium.com/@joshsaintjacque/resolving-merge-conflicts-in-binary-files-79df5aacd86f)
Once you commit your changes to local repo, you just resolve differences:
```bash
git checkout --ours -- [path/to/file.filetype]
git checkout --theirs -- [path/to/file.filetype]
```
Still need to push to central repo 
[Git Merge Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/using-branches/git-merge)

## Undoing Changes
```bash
git reset --hard <commit-hash>
```

## Pulling Just One File
Forum answer: [Is it possible to pull just one file in Git?](https://stackoverflow.com/questions/16230838/is-it-possible-to-pull-just-one-file-in-git)
```bash
git fetch origin
git checkout <branch> -- <file_name>
```

Example:
```bash
git fetch origin
git checkout origin/control -- bbot/src/bbot/bbot_ik.py
```

## Reverting changes for just one file (safely)
[Undo working copy modifications of one file in Git?](https://stackoverflow.com/questions/692246/undo-working-copy-modifications-of-one-file-in-git)
```bash
git checkout <branch> -- <file>
```
For example 
```bash
git checkout demo -- bbot/nodes/mixdrink
```
Reverts mixdrink to the last committed version on local branch demo

## Stashing Changes
[Atlassian tutorial - git stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)

## Install from Requirements files
[Example requirements file](https://pip.pypa.io/en/stable/reference/pip_install/#example-requirements-file). Use the following to install:
```bash
pip install -r requirements.txt
```

## Proxy

[Set proxy](https://gist.github.com/evantoli/f8c23a37eb3558ab8765)
[Remove proxy](https://stackoverflow.com/questions/32268986/git-how-to-remove-proxy)


## Miscellaneous
[How to Force Git Pull to Override Local Files](https://www.w3docs.com/snippets/git/how-to-force-git-pull-to-override-local-files.html)
[Configure Git to use a proxy](https://gist.github.com/evantoli/f8c23a37eb3558ab8765)
[How to make a Readme](https://www.makeareadme.com/)


