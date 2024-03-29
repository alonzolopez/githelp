# Git and Proxy Helper Commands

## Git Personal Access Tokens

[Using personal access tokens with git and github](https://www.edgoad.com/2021/02/using-personal-access-tokens-with-git-and-github.html)

Make sure to use the classic access tokens.

## Set wget proxy

For all users of the system via the `/etc/wgetrc` or for the user only with the `~/.wgetrc` file:

```bash
use_proxy=yes
http_proxy=http://<user>:<pw>@<ip>:<port>
https_proxy=https://<user>:<pw>@<ip>:<port>
```

or via -e options placed after the URL:

```bash
wget ... -e use_proxy=yes -e http_proxy=http://<user>:<pw>@<ip>:<port> ...
```

## Add a remote

[How to Add a New Remote to your Git Repo](https://articles.assembla.com/en/articles/1136998-how-to-add-a-new-remote-to-your-git-repo#:~:text=To%20add%20a%20new%20remote%2C%20use%20the%20git%20remote%20add,tab%20of%20your%20Git%20repo)

```bash
git remote add adder-ubuntu-20 ssh://alonzo@192.168.68.134/home/alonzo/catkin_ws/src/kinova-aero
```

## Delete a remote

[How to remove a Git Remote](https://linuxize.com/post/how-to-remove-git-remotes/#:~:text=Use%20the%20git%20remote%20rm%20command%20to,a%20remote%20from%20a%20repository.)

```bash
git remote rm <remote-name>
```

See all your remotes with

```bash
git remote -v
```

## Change a remote’s url

[Changing a remote’s URL](https://docs.github.com/en/github/using-git/changing-a-remotes-url)
First, enter the directory hosting the git repo. Then, list the remotes. Finally, set the new remote url.

```bash
cd <directory-to-repo>
git remote-v
git remote set-url <remote-name> <url>
```

A sample might look like

```bash
git remote set-url adder-2 ssh://alonzo@192.168.68.134/home/alonzo/catkin_ws/src/kinova-aero
```

You can check verify that the input was correct with

```bash
git remote -v
```

## How to ignore files with .gitignore

[Atlassian tutorial on .gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore)

## How to ignore files that are already being tracked 

(i.e. forgot to add them in the .gitignore and started tracking them)

[How to ignore files which are in repository?](https://stackoverflow.com/questions/7231608/how-to-ignore-files-which-are-in-repository)

[How to make Git "forget" about a file that was tracked but is now in .gitignore?](https://stackoverflow.com/questions/1274057/how-to-make-git-forget-about-a-file-that-was-tracked-but-is-now-in-gitignore)

[How to stop tracking and ignore changes to a file in Git?](https://stackoverflow.com/questions/936249/how-to-stop-tracking-and-ignore-changes-to-a-file-in-git?rq=1)

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

OR, you can do this all in one line (but it's important to understand that this one line does the two steps above):

```bash
git checkout -b control
```

We can now test changes on our local control branch. These changes should not be pushed to the master repo until they are fully functioning and validated.

## Tracking a Remote branch

[How to track a remote branch](https://www.git-tower.com/learn/git/faq/track-remote-upstream-branch)

## Delete branches

### Delete a local branch

To delete a local branch:

```bash
git branch -d <branch>
```

To delete a local branch set up to track a remote branch:

```bash
git branch -d -r <branch>
```

### Delete a remote branch

```bash
git push origin --delete <branch>
```

For example,

```bash
git push origin --delete experiment-setup
```

Note that this will only delete the remote branch. The remote branch is a separate entity that must be deleted following [these instructions](#delete-a-local-branch). e.g.

```bash
git branch -d -r <branch>
```

If you've deleted a remote branch in the central repo and would like to delete a remote branch locally without pushing, run the following

```bash
git fetch --all --prune
```

### Delete Branch Resources

- [How can I delete a remote branch in Git?](https://www.git-tower.com/learn/git/faq/delete-remote-branch)
- [How to fully delete ]

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

### Selectively merge branches

How to merge specific files or folders from another branch:

```bash
git checkout <branch> -- path/to/file
```

For example, if we're on branch `experimental`, and we'd like to get just a file from `master`, we run

```bash
git checkout master -- file.txt
```

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

[Example requirements file](https://pip.pypa.io/en/stable/reference/pip_install/#example-requirements-file)

Use the following to install:

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
