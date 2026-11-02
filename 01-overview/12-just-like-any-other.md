# 1.12 … Just Like Any Other

▶ [Watch in the video (30:54)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1854s)

A clone is a repository just like any other. You can create branches in it and make
changes that don't exist anywhere else yet. Here it gets a small Python script, a nod at
real functionality.

**Starting point:** the `git-tutorial` clone from [1.11](11-a-clone-is-a-local-copy.md).

## Commands

```bash
git checkout -b python-script
echo 'print("Hello, Git")' > script.py
python3 script.py
git add . && git commit -m \
    "Add Python script"
git log --oneline
```

The new branch starts as a copy of `main`. Before committing, check that the script runs:

```
$ python3 script.py
Hello, Git
```

After the commit, this clone has a version of the project that the original `repo`
directory and GitHub don't:

```
$ git log --oneline
09a1c62 Add Python script
33aeb78 Add description to README
70aae54 Initialize project README
```

---

← [1.11 A Clone Is A Local Copy](11-a-clone-is-a-local-copy.md) · [Index](../README.md) · [1.13 Versions Can Be Shared](13-versions-can-be-shared.md) →
