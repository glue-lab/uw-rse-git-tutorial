# 1.13 Versions Can Be Shared

▶ [Watch in the video (32:12)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1932s)

Earlier you pushed `main`, but you can push any branch. A version you've been working on
locally can be shared to the remote just as well, and then picked up from another
location.

**Starting point:** the `python-script` branch in `git-tutorial`, from
[1.12](12-just-like-any-other.md).

## Commands

```bash
git push -u origin python-script
cd ../repo
git fetch origin
git checkout python-script
```

## What you'll see

After the push, the branch exists on GitHub too. Back in `repo`, though, Git doesn't know
about it yet:

```
$ git checkout python-script
error: pathspec 'python-script' did not match any file(s) known to git
```

**`git fetch`** retrieves the latest information about the repository from the remote,
including any new branches:

```
$ git fetch origin
From github.com:<your-username>/git-tutorial
 * [new branch]      python-script -> origin/python-script
```

Now the checkout works. Git creates a local `python-script` branch that tracks the one on
the remote:

```
$ git checkout python-script
Switched to a new branch 'python-script'
branch 'python-script' set up to track 'origin/python-script'.
```

The commit made in one location is now available in the other.

---

← [1.12 … Just Like Any Other](12-just-like-any-other.md) · [Index](../README.md) · [1.14 … And Updated Anywhere](14-and-updated-anywhere.md) →
