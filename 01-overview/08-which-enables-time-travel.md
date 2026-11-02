# 1.8 … Which Enables Time Travel

▶ [Watch in the video (18:45)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1125s)

Because Git keeps every commit, you can jump back to an earlier state of the
project. Doing it on a new branch leaves `main` untouched.

**Starting point:** the repository from [1.7](07-git-is-version-control.md), on `main`.

## Commands

```bash
git checkout -b old-version
git reset --hard <commit>  # hash of "Initialize project README", from git log
git log
cat README.md
git checkout main && git log --oneline
```

`git reset --hard` moves the current branch to the given commit and makes your files match
it. `old-version` now looks like the project did after its very first commit:

```
$ git reset --hard 70aae54c
HEAD is now at 70aae54 Initialize project README

$ git log
commit 70aae54c63688bf71d3794672d02debeb46e4c09
Author: Your Name <you@example.com>
Date:   Fri Oct 30 16:29:25 2026 -0500

    Initialize project README

$ cat README.md
My Repository
```

`main` is unaffected:

```
$ git checkout main && git log --oneline
Switched to branch 'main'
33aeb78 Add description to README
70aae54 Initialize project README
```

> `--hard` discards uncommitted changes on the branch you reset. Here there weren't any.
[2.3](../02-storytelling-with-git/03-control-the-narrative-backups-and-undoing-commits.md)
comes back to using it with care.

---

← [1.7 Git Is Version Control](07-git-is-version-control.md) · [Index](../README.md) · [1.9 Versions Can Live Elsewhere](09-versions-can-live-elsewhere.md) →
