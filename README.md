# git-cheatsheet
A collection of go-to Git commands arranged by use cases.

## Basic workflow

- `git init  ` Create aka. initialize a new Git repository
- `git status` Shows one of those 3 options :
  1. Tracked files in the **staging area**, ready to be commited to the repo
  2. Untracked files in the **working directory**, to be added to the staging area
  3. "nothing to commit, working tree clean"
- `git add <file_name>`  Adds files from the working directory to the staging area so that Git starts tracking changes made to that file.
  - `-A` adds ALL changed files
- `git diff` Compare the working directory with the staging area
    - `--staged` Compare the staging area with the repository
- `git commit` Permanently store file changes from the staging area in the repository. A text editor launches for a **commit message** to be written according to the following best practices:

  1. Present tense, always.
  2. Subject line < 50 characters, followed by an empty line
  3. Self-contained 72-char. wrapped longer description addressing the following:
     - **Why the change > What**. As is the case in any code commenting
     - How does it address the problem?
     - Are there any side effects?


- `git log ` List all previous commits. `q` to exit.
  - `--graph --decorate --oneline` G.U.I. like log rendering
  - `--stat` Show number of changed files, insertions, deletions.




## Backtrack & clean

- `git checkout HEAD <file_name or SHA>` Restore <file_name> or <SHA> to the state of the last commit

- git checkout -- filename

    Restores our files to the state they were in when we made our last commit ! Excellent

- `git reset HEAD <file_name>` Unstage file changes in the staging area

- `git reset <SHA>` Reset to a previous commit in your commit history referring to its <SHA> point in the git log

- `git clean <optional_path>` Remove untracked files from the working tree AND directories (-d)

  - `-n` Shows what would be removed, aka. "dry ru**n**"
  - `-d` Remove untracked directories
  - `-f` Git will refuse to delete directories with .git sub directore or file unless a second -f is given




## Branches

- `git branch` List all of a Git project's branches.
- `git branch <branch_name>` Create a new branch named <branch_name>
  - `git branch -D <branch_name>` Adding the **-D** option deletes <branch_name>
- `git checkout <branch_name>` Switche from the current branch to <branch_name>
- `git checkout -b <branch_name>` Create and switch to a new branch at once.
- `git merge <branch_name>` Merge <branche_name> with the current branch.




## Teamwork & Syncing

- `git clone <remote_repo_name>` Create a local copy of a remote

- `git remote` Manage set of tracked repositories

  - `-v` List remote of a local repo
  - `add origin <url>` Send a local repo to GitHub servers. By convention, the main remote name is **origin**.
  - `set-url origin <url>` Set the url for our remote

- git fetch origin  |    Get the changes from the remote location into the (hidden?) origin/master branch

- `git merge origin master` Merge the server side repository, into your local branch.

- `git push` Push a local branch to the **origin** remote

  - `-u origin <branch_name>` Push on GitHub servers our local repo to a remote named "origin" and a branch named "master". The argument **-u** saves to **git push** the `origin <branch_name>` parameters.

- `git pull <remote_repo_name>` Update the local version of a repo by fetching **and merging** server side changes.

- `git fetch <remote_repo_name>` Update the local version of a repo by fetching server side changes.


## Sort after this line !

git diff HEAD
  Shows difference between our version and a recent pulled one

git rm '*.txt'
  Removes files from Git and the actual files from the disk


git merge <branch name>
  Merges the specified <branch name> with the one we are currently in


git branch -d <branch name>
  The argument -d stands for delete. Deletes the specified branch name.



git branch [branchxyz]
  Creates a new branch

git checkout [branchxyz]
  Switches to another branch

git push origin [branchxyz]
  Pushes a different branch instead of master

git branch
  Displays project's branches. Marks current branch with *

git fetch
  pull locally the files that have been updated on GitHub

git merge origin/master master
  ***NotSure*** merges the distant file I have just "fetched" with my
  master

git pull origin master
  similar to (git fetch + git merge origin/master master)
  this doesn't offer the possibility to examine what change have taken place
  server side before merging them locally.

Commands:

git diff id1 id2  |    Compare two commits
git clone  |    Create a local copy/clone from the repository
git config --global color.ui auto |    get colored diff output
git checkout  |    Shows a previous version of the file. This is not a checkout to edit like in SVN or TFS!


  Commands:

 git reset --hard  |    Undo all changes! There is no rollback for this, so be carefull!
  git checkout master  |    Restore the "Head" to the latest commit
​	git checkout HEAD filename | restore the staged file to its latest commit state aka HEAD !
  git log --graph --oneline <branch1> <branch2>  |    Show a visual representation of the commit history within different branches



  git merge branch1 branch2  |    Merge two branches, branch2 get merged into branch1
  git branch -d name  |    Remove the branch with the specified name
  git show commitId  |    Show the changes made in this commit compared to the previous version. This is working even after merging.



  Commands:

  git remote  |    Show all remote locations for the repository
  git remote add origin url |     Add a new remote location for the repository. Origin is the default name to use when you create only one remote location. Url should be the https url to the github repository.
  git remove -v  |    Outputs the remote locations with verbose information (fetch and push urls)
  git push origin master  |    Push the master branch to the remote location origin.
  git pull origin master  |    Get the master branch from the remote location origin.
  git pull origin master  |    = Git fetch origin + git merge master origin/master

#####   





git revert —no-commit <SHA>..HEAD