# 1.3 … That Contains .git

▶ [Watch in the video (5:26)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=326s)

What precisely makes a directory a Git repository? It's the `.git` subdirectory that
`git init` creates. That's where Git keeps everything it knows about your project. You
won't need to look inside it for this tutorial (or touch it by hand), but it's worth
knowing that it's there, and that its presence is what Git checks for.

**Starting point:** the `repo` directory from [1.2](02-a-repository-is-a-directory.md).

## Commands

```bash
ls -al       # .git shows up as a hidden directory
ls -l .git   # files and folders that Git manages
rm -rf .git
git status
git init
```

## What you'll see

`ls -l .git` shows the pieces Git initialized:

```
$ ls -l .git
total 24
-rw-r--r--   1 user  staff   21 Oct 26 13:11 HEAD
-rw-r--r--   1 user  staff  137 Oct 26 13:11 config
-rw-r--r--   1 user  staff   73 Oct 26 13:11 description
drwxr-xr-x  15 user  staff  480 Oct 26 13:11 hooks
drwxr-xr-x   3 user  staff   96 Oct 26 13:11 info
drwxr-xr-x   4 user  staff  128 Oct 26 13:11 objects
drwxr-xr-x   4 user  staff  128 Oct 26 13:11 refs
```

Remove `.git` and the directory is no longer a repository. It's like flipping a light
switch:

```
$ rm -rf .git
$ git status
fatal: not a git repository (or any of the parent directories): .git
```

`git init` switches it back on.

> **Careful:** in a real project, `rm -rf .git` deletes the project's entire history. It's
safe here only because the repository is empty.

---

← [1.2 A Repository Is A Directory](02-a-repository-is-a-directory.md) · [Index](../README.md) · [1.4 Let's Add Files](04-lets-add-files.md) →
