# 1.2 A Repository Is A Directory

▶ [Watch in the video (4:17)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=257s)

A Git repository isn't anything exotic: it's a directory (folder) on your computer that
Git has been told to track. `git init` is what turns an ordinary directory into one.

## Commands

```bash
mkdir repo && cd repo
git status  # before
git init
git status  # after
```

## What you'll see

Before `git init`, Git doesn't recognize the directory:

```
$ git status
fatal: not a git repository (or any of the parent directories): .git
```

`git init` creates an empty repository in place:

```
$ git init
Initialized empty Git repository in /path/to/repo/.git/
```

Now `git status` works. There's nothing to track yet, but Git recognizes the directory as
a repository:

```
$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

> If your output says `On branch master`, your Git is configured with an older default
branch name. Either is fine for this tutorial; to match the video, run
`git config --global init.defaultBranch main` before `git init`.

---

← [1.1 Git Is A Program](01-git-is-a-program.md) · [Index](../README.md) · [1.3 … That Contains .git](03-that-contains-dot-git.md) →
