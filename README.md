
***

# 💻 Basic Git Version Control Guide - Feature Branch Update!

This guide provides a fundamental overview of Git, the widely-used Distributed Version Control System (DVCS), covering core concepts, essential commands, and basic repository management.

***

## 1. Core Git Concepts

Git helps you track changes to files over time, allowing you to revert to any previous version of your project.

| Concept | Description | Analogy |
| :--- | :--- | :--- |
| **Repository (Repo)** | The main project folder containing all your files and the complete history (`.git` directory). | A complete photo album, including all photos and chronological records. |
| **Working Directory** | The actual files you see and edit on your local machine. | The desk where you are currently arranging and editing photos. |
| **Staging Area (Index)** | A middle ground where you prepare a snapshot of changes before committing them. | The set of photos you have selected and put into a pile, ready to be glued into the album. |
| **Commit** | A permanent snapshot of your staged changes at a specific point in time. Each commit has a unique ID (SHA) and a message. | Gluing the selected photos onto a page with a title/date. |
| **Branch** | An independent line of development. The default branch is usually **`main`** (or `master`). | A parallel timeline where you can experiment without affecting the main project. |
| **HEAD** | A pointer to the **latest commit** in the currently active branch. | The "currently viewing" sticker on your photo album. |
| **Remote** | A version of your repository hosted on the internet (e.g., GitHub, GitLab). | The cloud storage or shared album everyone collaborates on. |

***

## 2. Setting Up and Initializing

These commands are used to set up Git on your local machine and create a new repository.

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git config`** | Set user-specific configuration details (done once per machine). | `git config --global user.name "Your Name"` |
| **`git init`** | Initializes a new local Git repository in the current directory. | `git init` |
| **`git clone`** | Creates a local copy of an existing remote repository. | `git clone <repo_url>` |

***

## 3. The Basic Git Workflow (The 3 States)

The typical development cycle involves moving changes between three states: Working Directory, Staging Area, and Local Repository.

### 3.1. Checking Status

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git status`** | Shows the state of the working directory and staging area. It tells you what is untracked, modified, or staged. | `git status` |
| **`git diff`** | Shows the difference between the Working Directory and the Staging Area (i.e., unstaged changes). | `git diff` |
| **`git diff --staged`** | Shows the difference between the Staging Area and the last commit (i.e., staged changes). | `git diff --staged` |

### 3.2. Staging and Committing

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git add`** | Adds changes from the Working Directory to the Staging Area. | `git add <file_name.js>` |
| **`git add .`** | Stages **all** changes (new files and modifications) in the current directory. | `git add .` |
| **`git commit`** | Records the staged snapshot permanently to the local repository history. | `git commit -m "Descriptive commit message"` |
| **`git log`** | Displays the commit history for the current branch. | `git log --oneline` (Condensed view) |

***

## 4. Branching and Merging

Branches are essential for non-linear development, allowing features or fixes to be developed in isolation.

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git branch`** | Lists all local branches in the repository. | `git branch` |
| **`git branch <name>`** | Creates a new branch with the specified name. | `git branch feature/new-login` |
| **`git switch <name>`**| Switches to the specified branch and updates the working directory. | `git switch feature/new-login` |
| **`git switch -c <name>`**| Creates a new branch **and** immediately switches to it (shorthand for `git branch` and `git switch`). | `git switch -c fix/typo` |
| **`git merge <name>`** | Integrates changes from the specified branch into the current branch. | `git merge feature/new-login` |
| **`git branch -d <name>`**| Deletes the local branch (must not be on the branch). | `git branch -d feature/new-login` |

***

## 5. Repository Management (Remote Operations)

These commands synchronize your local repository with a remote repository (like one hosted on GitHub).

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git remote -v`** | Lists the remote repositories associated with your local repo. | `git remote -v` |
| **`git remote add`** | Connects a local repository to a new remote server. | `git remote add origin <url>` |
| **`git push`** | Uploads your local branch commits to the remote repository. | `git push origin main` |
| **`git pull`** | Fetches and automatically merges changes from the remote repository into your current local branch. (Shorthand for `git fetch` + `git merge`). | `git pull origin main` |
| **`git fetch`** | Downloads commits, files, and refs from a remote repository into your local repository, but **does not** automatically merge. | `git fetch origin` |

***

## 6. Undoing Changes (Basic)

| Command | Purpose | Example |
| :--- | :--- | :--- |
| **`git restore <file>`** | **Unstages** a staged file OR **discards local changes** in the Working Directory (reverts to the last commit/staged version). | `git restore index.html` |
| **`git reset <file>`** | **Unstages** a file from the staging area, keeping the changes in the Working Directory. | `git reset -- index.html` |
| **`git commit --amend`** | Rewrites the very last commit message or adds missing files to the previous commit. | `git commit --amend -m "Updated message"` |
| **`git reset --soft HEAD~1`** | Undoes the last commit, but keeps all changes **staged**. | `git reset --soft HEAD~1` |
| **`git reset --hard HEAD~1`** | **WARNING: DANGEROUS!** Undoes the last commit and **discards all changes** from the working directory. | `git reset --hard HEAD~1` |