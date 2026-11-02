# 1.4 Let's Add Files

▶ [Watch in the video (7:27)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=447s)

Repositories are meant to be more than empty folders. Start simple: put a short message in
a README file and see how Git treats a new file.

**Starting point:** the empty repository from [1.3](03-that-contains-dot-git.md).

## Commands

```bash
echo "My Repository" > README.md
git status  # README.md is untracked
```

## What you'll see

```
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

**Untracked** means the file exists in the directory, but Git isn't aware of it in a
version-control sense: it doesn't belong to any version of your project that Git has
recorded. The next module brings it under Git's watch.

---

← [1.3 … That Contains .git](03-that-contains-dot-git.md) · [Index](../README.md) · [1.5 Git Tracks Changes](05-git-tracks-changes.md) →
