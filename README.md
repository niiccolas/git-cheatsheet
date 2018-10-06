# git-cheatsheet
A collection of go-to Git commands arranged by use cases.

## Basic workflow

- `git init  ` Create aka. initialize a new Git repository
- `git status` Show one of 3 options:
  1. Tracked files in the **staging area**, ready to be commited to the repo
  2. Untracked files in the **working directory**, to be added to the staging area
  3. "nothing to commit, working tree clean"
- `git add <file_name>`  Add files from working directory to staging area where Git tracks changes.
  - `-A` add **a**ll changed files
- `git rm <file_name>` Remove file from Git and from the disk
- `git diff` Compare the working directory with the staging area
    - `--staged` Compare the staging area with the repository
- `git commit` Permanently store file changes from the staging area in the repository. A text editor launches for a **commit message** to be written according to the following best practices:
  1. Present tense, always.
  2. Subject line < 50 characters, followed by an empty line
  3. Self-contained 72-char. wrapped longer description addressing the following:
     - **Why the change over What**. As is the case in any code commenting
     - How does it address the problem?
     - Are there any side effects?


- `git log ` List all previous commits. `q` to exit.
  - `--graph --decorate --oneline` GUI-like rendering of previous commits log
  - `--stat` Show number of changed files, insertions, deletions
  - `--graph --oneline <branch1> <branch2>` GUI-like rendering of commits log within different branches
- `git config --global color.ui auto` Set diff to colored output




## Backtrack & clean

- `git checkout HEAD <file_name_or_SHA>` Restore <file_name> or <SHA> to its state at the last commit
- `git reset HEAD <file_name>` Unstage file changes in the staging area
- `git reset <SHA>` Reset to a previous commit in your commit history referring to its <SHA> point in the git log
-  `git reset --hard` **Undo all changes. No rollback, be careful!**
- `git clean <optional_path>` Remove untracked files from the working tree AND directories (-d)

  - `-n` Show what would be removed, aka. "dry ru**n**"
  - `-d` Remove untracked directories
  - `-f` Force delete of directories containing .git sub directory or file 




## Branches

- `git branch` List all branches in a git repository. The ***** (star) symbol marks the current branch
- `git branch <branch_name>` Create a new branch named <branch_name>
  - `git branch -d <branch_name>` **D**elete <branch_name>
- `git checkout <branch_name>` Switch to the <branch_name> branch
- `git checkout -b <branch_name>` Create and switch to a new branch at once.
- `git merge <branch_name>` Merge <branch_name> with the current branch.
  -  git merge `<branch1> <branch2>` Merge <branch2> into <branch1>




## Teamwork & Sync

- `git clone <remote_repo_name>` Create a local copy of a remote repository
- `git remote` Show all remote locations for current repository
  - `-v` **V**erbose output of fetch and push urls for remote repo
  - `add origin <url>` Add new remote for current repository. By convention, the main remote name is **origin** when there is only one remote location.
  - `set-url origin <url>` Set remote's url
- `git merge origin master` Once fetched, merge server side repository into local master branch.
- `git push` Push a local branch to the **origin** remote

  - `-u origin <branch_name>` Push local <branch_name> instead of master to remote server. Argument **-u** saves to **git push** the `origin <branch_name>` parameters.
- `git pull <remote_repo_name>` Update the local version of a repo by fetching first **then merging** server side changes.
- `git fetch <remote_repo_name>` Update the local version of a repo by fetching server side changes, without merging them locally. Interesting when in need to check out what new changes have been made before merging.
