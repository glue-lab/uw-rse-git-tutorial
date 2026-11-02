# 1.5 Git Tracks Changes

▶ [Watch in the video (8:43)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=523s)

One of the main things Git does for you is track changes to your code, precisely, line by
line and file by file. Getting a file tracked is a two-step cycle: **add** it, which
stages it for the next commit, then **commit**, which records a checkpoint of everything
staged.

**Starting point:** the untracked `README.md` from [1.4](04-lets-add-files.md).

## Add and commit

```bash
git add README.md
git status  # README.md staged for commit
git commit -m "Initialize project README"
git status  # README.md is now tracked
```

After `git add`, the file is listed under "Changes to be committed":

```
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   README.md
```

`git commit -m` records the checkpoint with a short message describing the change. After
it, there's nothing left to commit:

```
$ git status
On branch main
nothing to commit, working tree clean
```

That's the full cycle: untracked, then staged, then committed.

## Change a tracked file

```bash
echo "- A place to work with git" \
     >> README.md
git status  # README.md has been modified
git diff README.md
```

Because Git now tracks `README.md`, it notices the edit relative to the last commit:

```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

`git diff` shows exactly what changed, line by line. The `+` marks the added line:

```
$ git diff README.md
diff --git a/README.md b/README.md
index 81e1278..ed09fa5 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,2 @@
 My Repository
+- A place to work with git
```

> In the video, this change gets committed before the diff is shown, then undone with
`git reset` so the diff can be seen. Running `git diff` before committing, as here, shows
the same thing.

---

← [1.4 Let's Add Files](04-lets-add-files.md) · [Index](../README.md) · [1.6 Git Saves Changes](06-git-saves-changes.md) →
