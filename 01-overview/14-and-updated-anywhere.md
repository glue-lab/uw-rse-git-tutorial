# 1.14 … And Updated Anywhere

▶ [Watch in the video (34:15)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2055s)

Sharing works in both directions. Now that `repo` has the `python-script` branch, you can
update it there and push the result back up to the remote, ping-ponging between locations.

**Starting point:** the `python-script` branch in `repo`, from
[1.13](13-versions-can-be-shared.md).

## Commands

```bash
echo 'print("Hello, UW RSE")' > script.py
git add . && git commit -m \
    "Update greeting in Python script"
git push -u origin python-script
```

The push sends just the new commit:

```
$ git push -u origin python-script
To github.com:<your-username>/git-tutorial.git
   09a1c62..d051e21  python-script -> python-script
branch 'python-script' set up to track 'origin/python-script'.
```

> Make sure to name the branch you're on. In the video, `main` nearly gets pushed instead
(muscle memory).

---

← [1.13 Versions Can Be Shared](13-versions-can-be-shared.md) · [Index](../README.md) · [1.15 This Is How You Collaborate!](15-this-is-how-you-collaborate.md) →
