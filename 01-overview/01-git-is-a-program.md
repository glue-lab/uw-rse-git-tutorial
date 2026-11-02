# 1.1 Git Is A Program

▶ [Watch in the video (2:56)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=176s)

Nothing about Git is magic. It's a program installed on your computer, just like `ls` or
`python3`, and you run it from the command line.

## Commands

```bash
which git
git --version
```

## What you'll see

`which` tells you where a program lives:

```
$ which git
/usr/bin/git
```

Compare `which ls` or `which python3`. Git is an ordinary command-line program like those.

`--version` reports which version you have, just as `python3 --version` does for Python:

```
$ git --version
git version 2.39.5 (Apple Git-154)
```

Your path and version may differ. Anything reasonably recent will work for this tutorial.

---

[Index](../README.md) · [1.2 A Repository Is A Directory](02-a-repository-is-a-directory.md) →
