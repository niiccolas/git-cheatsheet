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