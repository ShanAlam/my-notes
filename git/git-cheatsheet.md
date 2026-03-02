# Git + GitHub Cheatsheet

## Basic Setup

Set global username and email:
```bash
git config --global user.name "your name"
git config --global user.email "your email"
```

Check current configuration:
```bash
git config --list
```

Initialise a new git repository:
```bash
git init
```

Clone an existing repository:
```bash
git clone <repo URL>
```

Pull latest version of a branch from remote repository to local device:
```bash
git pull origin <branch name>
```

Push latest version of a branch from local device to remote repository:
```bash
git push origin <branch name>
```

## Branches

Check branch your on:
```bash
git branch
```

Switch branch:
```bash
git switch <branch name>
```

Create a branch:
```bash
git switch -c <branch name>
```

Delete a branch:
```bash
git branch -d <branch name>
```

Change branch name: switch to branch and enter:
```bash
git branch -m <new name>
```

## Staging and Committing

Stage all changes:
```bash
git add .
```

Stage specific files:
```bash
git add <file name 1> <file name 2>
```

Commit changes with message:
```bash
git commit -m "your message"
```

Commit changes with multi-line message:
```bash
git commit
```

## Unstaging and Uncommitting

Unstage:
```bash
git reset
```

Unstage specific file:
```bash
git reset <file>
```

Uncommit:
```bash
git reset HEAD^
```

## Undoing Changes

Note: ensure changes have been unstaged or uncommitted before running these.

Undo ALL changes:
```bash
git restore .
```

Remove untracked files:
```bash
git clean -f
```

Undo changes to specific files:
```bash
git restore path/to/file
```

## Status and Logs

Check status i.e. untracked/unstaged files:
```bash
git status
```

Check commit history:
```bash
git log
```

## Merging and Rebasing

Merge ANOTHER branch into CURRENT branch:
```bash
git merge <branch name>
```

Rebase CURRENT branch onto ANOTHER branch:
```bash
git rebase <branch name>
```

## Pulling and Pushing

Fetch changes from remote repo (without merging):
```bash
git fetch
```

Pull changes from remote repo and merge into current branch:
```bash
git pull
```

Push local changes to remote repo:
```bash
git push origin <branch name>
```

Push local changes to remote repo and set upstream (only required for first push):
```bash
git push -u origin <branch name>
```

## Tagging

Once you think you have added all the stuff you want to the tool, test in `dev` branch and get others to review changes.

Once you are happy, open a pull request to merge `dev` to `main`.

Ensure to use a version tag when merging to `main` to keep track of which version you are using.

Do this by:
```bash
git tag -a v1.0 -m "first stable release"
```
