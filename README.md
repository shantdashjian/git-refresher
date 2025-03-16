# git-refresher
A refresher of the core Git commands

![Terminal](https://upload.wikimedia.org/wikipedia/commons/e/e0/Git-logo.svg)

## In This Document:
  - [What is Git?](#what-is-git)
  - [RTFM](#rtfm)
  - [Types of Commands](#types-of-commands)
  - [What is a Git Repo](#what-is-a-git-repo)
  - [The Git Lifecycle](#the-git-lifecycle)
  - [How Do You](#how-do-you)


## What is Git
- Git is the de facto standard, and most popular, version control system. 
- It's open source and distrubuted. 
- It's created by Linus Torvalds in 2005.
- He wrote it in 5 days.

## RTFM
- [Docs](https://git-scm.com/docs)
- [Book](https://git-scm.com/book/en/v2)

## Types of Commands
1. Porcelain: High level, used 99% of the time
```
> git init
> git status
> git add
> git commit
> git push
> git pull
> git log
```

2. Plumbing: Low level, used 1% of the time
```
> git apply
> git commit-tree
> git hash-object
```

## What is a Git Repo
- It's your code + a `.git` direcotry.
- `.git` contains files to track the changes.

## The Git Lifecycle
1. Untracked: You write code. Now it's **untracked**.
2. Staged: You `> git add .` your untracked code. Now it's **staged**.
3. Committed: You `> git commit -m "Fix bug"` your staged code. Now it's committed.
4. Pushed: You `> git push origin main` your committed code. Now it's pushed to the remote repository on GitHub.

**Staged** means prepared to be committed.

To **commit** your staged code, is to take a snapshot of your code at this point in time, saving the state of your code, in the `.git` directory.

## How Do You
**init**ialize a Git repo
```
> mkdir project
> cd project
> git init
```

Check the **status** of the Git repo
```
> git status
```

Stage untracked code changes, **add**ing them to the staged area, ready to be committed
```
> git add .
```

**commit** the staged changed to the Git tracking system
```
> git commit -m "Fix bug"
```

**amend** the commit you just made, in case you missed something or screwed up the code or message
```
> git commit --amend
```

See the **log** of all changes committed so far
```
> git log
> git log --oneline --graph --decorate --parents
```

Decrypt a commit object
```
> git cat-file -p <SHA>
```

CRUD the **config**
```
> git config set --global user.name "shantdashjian" # Default is the --local
> git config list
> git config get user.name
> git config unset polar.bookshop
> git config unset --all polar.bookshop
> git config remove-section polar
```

For most of the time, you'd use the global config found in `~/.gitconfig`. At times, you'd use the local config found in `project/.git/config`.

Track your changes (feature, bug fix) separately from `main`.

A **branch** is just a pointer to a commit.

set the **default branch** in config
```
> git config set init.defaultBranch main
```

**move** or rename a branch
```
> git branch -m master main
```

create a new branch (3 ways, first is the recommended)
```
> git switch -c feature-branch # create and switch
> git branch feature-branch # create
> git checkout -b feature-branch # create and switch
```

switch to existing branch
```
> git switch feature-branch
> git checkout feature-branch
```

A **merge commit** is a commit created when merging two branches. It has 2 parents.

When doing a fast forward merge, no merge commit is created. This happens when the other branch I am merging into this branch, has its base being the head of the current branch. In other words, after the other branch was checked out based on this branch, and commits were added there, no commits were added here. So we just fast forward merge.

**merge** another branch to this branch I am on
```
> git merge feature-branch # into what I am on
```

**d**elete another branch I an NOT on
```
> git branch -d feature-branch
```

**rebase** the feature branch such that it gets all the "base" commits after it was created, resulting in a clean history, and no merge commits in the future.
```
> git rebase main # into this feature branch
```

**reset** to a previous commit
**soft**ly, moving commited changes back to staged
```
> git reset --soft <SHA>
```

**hard**ly, completely removing commited changes
```
> git reset --hard <SHA>
```

**add** a **remote** branch connection
```
> git remote add origin <url to remote branch>
```

**fetch** from the remote branch
```
> git fetch
```

Use GitHub to:
1. **back up** your code in the cloud
2. **collaborate** with other team members by sharing code in a central place
3. make your projects available to the public as a **portfolio**

Top 3 Cloud Git Providers:
1. Github
2. GitLab
3. BitBucket

**delete** a remote branch
```
> git push origin :remote-branch-name
```

**pull** latest changes from remote, which means to **fetch** and **merge** into this branch
```
> git pull origin main
```

to **rebase** when pulling
```
> git config set --global pull.rebase true
```

PR = Pull Request. It's how you propose changes to a remote repo.

Use `.gitignore` to put files in your project directory on your machine, but not track them in Git.

You can use `*` as a wild card
```
*.text
```

You can NOT ignore a file
```
!important.txt
```

show the **diff** between the current changes and the last commit
```
> git diff
```
