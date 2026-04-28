# Git & GitHub Cheat Sheet

> A personal reference guide covering core concepts, commands, and workflows.
> Built while learning — updated as I grow. 

---

## Table of Contents

- [Core Concepts](#-core-concepts)
- [Setup & Configuration](#-setup--configuration)
- [Repository Basics](#-repository-basics)
- [Staging & Committing](#-staging--committing)
- [Branching](#-branching)
- [Merging & Rebasing](#-merging--rebasing)
- [Syncing with GitHub](#-syncing-with-github)
- [Undoing Changes](#-undoing-changes)
- [Viewing History & Diffs](#-viewing-history--diffs)
- [File Management](#-file-management)
- [Collaboration & Open Source](#-collaboration--open-source)
- [Markdown Syntax](#-markdown-syntax)
- [Tips & Best Practices](#-tips--best-practices)

---

## Core Concepts

| Term | Meaning |
|------|---------|
| **Git** | A version control tool that runs locally on your computer |
| **GitHub** | A cloud platform that hosts Git repositories online |
| **Repository (Repo)** | A project folder tracked by Git |
| **Commit** | A saved snapshot of your changes, like a checkpoint |
| **Branch** | A parallel version of the project to work on safely |
| **Merge** | Combining changes from one branch into another |
| **Clone** | Downloading a repo to your local machine |
| **Fork** | Your own copy of someone else's repository |
| **Pull Request (PR)** | A request to merge your changes into a project |
| **Staging Area** | Where you prepare changes before committing |
| **Remote** | The online version of your repo |
| **Origin** | The default name Git gives to your remote repo |
| **Main/Master** | The default primary branch of a repo |
| **HEAD** | A pointer to your current position in the repo |

---

## Setup & Configuration

```bash
# Set your name and email (required before first commit)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Set default branch name to 'main'
git config --global init.defaultBranch main

# Set VS Code as default editor
git config --global core.editor "code --wait"

# View all config settings
git config --list

# View a specific setting
git config user.name
```

---

## Repository Basics

```bash
# Initialize a new Git repo in current folder
git init

# Clone a repo to your machine - repo URL
git clone https://github.com/username/repo-name.git 

# Clone into a specific folder name
git clone https://github.com/username/repo-name.git my-folder

# Check repo status - changes done, added or not, un-committed changes etc
git status

# View remote connections
git remote -v

# Add a remote connection
git remote add origin https://github.com/username/repo-name.git

# Change remote URL
git remote set-url origin https://github.com/username/new-repo.git
```

---

## Staging & Committing

```bash
# Stage a specific file
git add filename.txt

# Stage all changes in current folder
git add .

# Stage all changes in the entire repo
git add -A

# Unstage a file (keep changes, just remove from staging)
git restore --staged filename.txt

# Commit staged changes with a message
git commit -m "Your commit message here"

# Stage and commit files in one step
git commit -am "Your commit message"

# Amend the last commit message (before pushing)
git commit --amend -m "Corrected commit message"
```

## Branching

```bash
# List all local branches
git branch

# List all branches including remote
git branch -a

# Create a new branch
git branch branch-name

# Switch to an existing branch
git checkout branch-name
# OR (modern way)
git switch branch-name

# Create AND switch to a new branch
git checkout -b branch-name
# OR
git switch -c branch-name

# Rename current branch
git branch -m new-branch-name

# Delete a branch (safe, only if merged)
git branch -d branch-name

# Force delete a branch (even if not merged)
git branch -D branch-name

# Push a new branch to GitHub
git push origin branch-name
```

---

## Merging & Rebasing

```bash
# Merge a branch into your current branch
git merge branch-name

# Merge with a commit message
git merge --no-ff branch-name

# Abort a merge in progress
git merge --abort

# Rebase current branch onto main
git rebase main

# Abort a rebase in progress
git rebase --abort
```

> **Merge vs Rebase:**
> - `merge` keeps full history with a merge commit
> - `rebase` rewrites history for a cleaner, linear log
> - Never rebase branches others are working on

---

## Syncing with GitHub

```bash
# Push local commits to GitHub
git push origin main

# Push a branch for the first time and track it
git push -u origin branch-name

# Pull latest changes from GitHub (fetch + merge)
git pull origin main

# Fetch changes without merging
git fetch origin

# Pull with rebase instead of merge
git pull --rebase origin main
```

---

## Undoing Changes

```bash
# Discard changes in a file (revert to last commit)
git restore filename.txt

# Discard ALL unstaged changes
git restore .

# Undo last commit but keep changes staged
git reset --soft HEAD~1

# Undo last commit and unstage changes (keep files)
git reset --mixed HEAD~1

# Undo last commit and DELETE all changes (destructive!)
git reset --hard HEAD~1

# Revert a commit by creating a new opposite commit (safe for shared branches)
git revert commit-hash

# Stash uncommitted changes temporarily
git stash

# Apply the most recent stash
git stash pop

# List all stashes
git stash list

# Drop a specific stash
git stash drop stash@{0}
```

> `git reset --hard` is **permanent**, changes are gone.

---

## Viewing History & Diffs

```bash
# View commit history
git log

# Compact one-line log
git log --oneline

# Visual branch graph
git log --oneline --graph --all

# Show changes not yet staged
git diff

# Show changes staged but not committed
git diff --staged

# Show changes in a specific commit
git show commit-hash

# Show who changed each line in a file
git blame filename.txt
```

---

## File Management

```bash
# Delete a file and stage the deletion
git rm filename.txt

# Remove file from Git tracking only (keep it locally)
git rm --cached filename.txt

# Move or rename a file
git mv old-name.txt new-name.txt

# List all tracked files
git ls-files
```

---


> *This guide is a living document — updated as I learn new things.*
