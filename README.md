# git-cheatsheet
Go-to Git commands

## Basic workflow

- `git init  ` Creates aka. "initializes" a new Git repository
- `git status` Shows one of those 3 options :
  1. Tracked files in the **staging area**, ready to be commited to the repo
  2. Untracked files in the **working directory**, to be added to the staging area
  3. "nothing to commit, working tree clean"
- `git add <file_name>`  Adds files from the working directory to the staging area so that Git starts tracking changes made to that file.
  - `-A` adds ALL changed files
- `git diff` Compare the working directory with the staging area
    - `--staged` Compares the staging area with the repository
- `git commit` Permanently stores file changes from the staging area in the repository. A text editor launches for a **commit message** to be written according to the following best practices:

  1. Present tense, always.
  2. Subject line < 50 characters, followed by an empty line
  3. Self-contained 72-char. wrapped longer description addressing the following:
     - **Why the change > What**. As is the case in any code commenting
     - How does it address the problem?
     - Are there any side effects?


- `git log ` Lists all previous commits
  - `--graph --decorate --oneline` G.U.I. like log rendering




## Backtrack & clean

- `git checkout HEAD <file_name> | <SHA>` Discard changes in the working directory

- `git reset HEAD <file_name>` Unstage file changes in the staging area

- `git reset <SHA>` Reset to a previous commit in your commit history

- `git clean <optional_path>` Remove untracked files from the working tree AND directories (-d)

  - `-n` Shows what would be removed, aka. "dry ru**n**"
  - `-d` Removes untracked directories
  - `-f` Git will refuse to delete directories with .git sub directore or file unless a second -f is given




## Branches

- `git branch` Lists all of a Git project's branches.
- `git branch <branch_name>` Creates a new branch named <branch_name>
  - `git branch -D branch_name` Adding the **-D** option deletes <branch_name>
- `git checkout <branch_name>` Switches from the current branch to <branch_name>
- `git merge <branch_name>` Merges <branche_name> with the current branch.




## Teamwork

- `git clone <remote_repo_name>` Create a local copy of a remote
- `git remote` Manage set of tracked repositories
  - `-v` List remote of a local repo
  - `add origin <url>` Send a local repo to GitHub servers. By convention, the main remote name is **origin**.
  - `set-url origin <url>` Set the url for our remote
- `git fetch` Fetches work from the remote into the local copy
- `git merge origin/master`: Merges `origin/master` into your local branch
- `git push`: Pushes a local branch to the **origin** remote
  - `-u origin <branch_name>` Pushes on GitHub servers our local repo to a remote named "origin" and a branch named "master". The argument **-u** saves to **git push** the `origin <branch_name>` parameters.



## Sort after this line !

git pull origin master
  Pulls from GitHub servers our repo after it has been accessed and modified by collaborators
  This pulls down locally any changes that happened server side

git diff HEAD
  Shows difference between our version and a recent pulled one

git reset HEAD filename
  Unstages file changes in the staging area (HEAD is not mandatory I believe)
git reset commit_SHA_firs7chars
	Resets to a previous commit referring to its SHA point in the git log

git checkout -- filename
  GO-TO SAFETY NET !
  Restores our files to the state they were in when we made our last commit ! Excellent

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

inspired from https://github.com/Denyos/

Commands:

q |    exit git log!
git log  |    List the commits and show which files have changed
type "q" to exit git log
git log --stat  |    Show addition information about the commits
git diff id1 id2  |    Compare two commits
git clone  |    Create a local copy/clone from the repository
git config --global color.ui auto |    get colored diff output
git checkout  |    Shows a previous version of the file. This is not a checkout to edit like in SVN or TFS!


  Commands:

 git reset --hard  |    Undo all changes! There is no rollback for this, so be carefull!
  git checkout master  |    Restore the "Head" to the latest commit
	git checkout HEAD filename | restore the staged file to its latest commit state aka HEAD !
  git log --graph --oneline <branch1> <branch2>  |    Show a visual representation of the commit history within different branches

 git checkout -b new_branch_name (an excellent shortcut)
  |    Creates a new branch and do a checkout on this branch in one call instead of git branch new_branch_name and git checkout new_branch_name

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

#####   git fetch origin  |    Get the changes from the remote location into the (hidden?) origin/master branch





git revert —no-commit <SHA>..HEAD