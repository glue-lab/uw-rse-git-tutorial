# 1.11 A Clone Is A Local Copy

▶ [Watch in the video (26:17)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1577s)

Hosting services show a **Clone** button on every repository. Cloning just creates a local
copy of a remote repository, so you can take code that's been posted there and work with
it on your own machine.

**Starting point:** the `repo` directory from [1.10](10-anywhere-actually.md), pushed to
GitHub.

## Commands

On your repository's GitHub page, open the **Code** menu and copy the SSH URL. Then:

```bash
cd ..
git clone \
  git@github.com:<your-username>/git-tutorial.git
cd git-tutorial
git status
```

The clone has the same history you pushed, and it already knows where it came from:

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

$ git log --oneline
33aeb78 Add description to README
70aae54 Initialize project README
```

You now have two copies of the project side by side: `repo` and `git-tutorial`.

## Why keep a remote at all?

Plenty of Git's value is purely local: commits give you checkpoints you can always return
to, so you can try something new without fear of losing a version that works. Remotes add
two things:

- **Backups:** your computer isn't the only place the code lives. If you lose your laptop,
  or just need to work somewhere else, clone the repository and pick up where you left
  off.
- **Sharing:** others can get the code, and you can get theirs.

Remote doesn't have to mean public. GitHub projects are public by default but can be
private, and services like a group's own GitLab can keep everything internal.

---

← [1.10 … Anywhere, Actually](10-anywhere-actually.md) · [Index](../README.md) · [1.12 … Just Like Any Other](12-just-like-any-other.md) →
