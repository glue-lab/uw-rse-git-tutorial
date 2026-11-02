# 1.6 Git Saves Changes

▶ [Watch in the video (12:44)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=764s)

Each commit is a snapshot of your project, and Git keeps all of them. You can list the
history of commits and pull up the contents of any file as it was in a particular commit.

**Starting point:** the modified `README.md` from [1.5](05-git-tracks-changes.md).

## Commands

```bash
git add .  # shorthand for "add everything"
git commit -m "Add description to README"
git log    # Commit IDs are hashes
git show <commit>:README.md
```

`git add .` stages everything that isn't committed yet: modified files, new untracked
files, all of it. Adding files by name, as in [1.5](05-git-tracks-changes.md), works too.

## What you'll see

`git log` lists the commits, newest first:

```
$ git log
commit 33aeb78d989d5f09b2257db220f8660952e4419d
Author: Your Name <you@example.com>
Date:   Fri Oct 30 16:29:25 2026 -0500

    Add description to README

commit 70aae54c63688bf71d3794672d02debeb46e4c09
Author: Your Name <you@example.com>
Date:   Fri Oct 30 16:29:25 2026 -0500

    Initialize project README
```

The long strings of letters and digits are **hashes**: unique identifiers for each commit.
Yours will be different. Wherever Git expects a commit, you can use its hash, and the
first several characters are usually enough.

Show `README.md` as it was at each commit, using hashes from your own log:

```
$ git show 70aae54c:README.md
My Repository

$ git show 33aeb78d:README.md
My Repository
- A place to work with git
```

Both versions are saved in the project's history, and either can be retrieved at any time.

---

← [1.5 Git Tracks Changes](05-git-tracks-changes.md) · [Index](../README.md) · [1.7 Git Is Version Control](07-git-is-version-control.md) →
