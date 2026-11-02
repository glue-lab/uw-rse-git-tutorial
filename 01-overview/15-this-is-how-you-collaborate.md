# 1.15 This Is How You Collaborate!

▶ [Watch in the video (35:28)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2128s)

This is how collaboration works. Someone pushes changes on a branch, and someone else
brings them in, not by cloning the whole project again, but by getting just the commits
added since they last checked in.

**Starting point:** the updated `python-script` branch pushed from `repo` in
[1.14](14-and-updated-anywhere.md).

## Commands

```bash
cd ../git-tutorial
git fetch origin
git status
git pull
git log --oneline
```

## What you'll see

After fetching, `git status` knows the remote branch has moved ahead of yours:

```
$ git status
On branch python-script
Your branch is behind 'origin/python-script' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
```

**`git pull`** brings those commits into your local branch:

```
$ git pull
Updating 09a1c62..d051e21
Fast-forward
 script.py | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

$ git log --oneline
d051e21 Update greeting in Python script
09a1c62 Add Python script
33aeb78 Add description to README
70aae54 Initialize project README
```

Here both directories live on your computer, standing in for two collaborators. In the
real world, the second location would be someone else's machine, or another machine of
your own (a server, say).

---

← [1.14 … And Updated Anywhere](14-and-updated-anywhere.md) · [Index](../README.md) · [2.0 Storytelling with Git](../02-storytelling-with-git/00-storytelling-with-git.md) →
