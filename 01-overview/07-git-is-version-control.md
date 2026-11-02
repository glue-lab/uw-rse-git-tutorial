# 1.7 Git Is Version Control

▶ [Watch in the video (15:12)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=912s)

So far there's been a single version of the project, built up commit by commit. Something
Git does really well is manage multiple versions at once (it's in the name: a version
control system). A **branch** is a separate version, or timeline, of your project.

**Starting point:** the two-commit repository from [1.6](06-git-saves-changes.md).

## Create a new branch

`git branch` lists branches and marks the one you're on with `*`. `git checkout -b`
creates a new branch and switches to it:

```bash
git branch  # on main branch
git checkout -b new-version
git branch  # now on new-version
```

```
$ git branch
* main

$ git checkout -b new-version
Switched to a new branch 'new-version'

$ git branch
  main
* new-version
```

## Make a new version on it

The new branch starts as a copy of the one you branched from. Change `README.md` and
commit, just as before:

```bash
echo "My Project" > README.md && git add .
git commit -m "A new README version"
git log --oneline
```

The commit belongs only to `new-version`:

```
$ git log --oneline
1fa1277 A new README version
33aeb78 Add description to README
70aae54 Initialize project README
```

## Switch between versions

```bash
git status  # can also see branch from here
cat README.md
git checkout main
cat README.md
```

The two branches now hold different versions of `README.md`, side by side. Switching
branches switches which one is in your directory:

```
$ cat README.md
My Project

$ git checkout main
Switched to branch 'main'

$ cat README.md
My Repository
- A place to work with git
```

---

← [1.6 Git Saves Changes](06-git-saves-changes.md) · [Index](../README.md) · [1.8 … Which Enables Time Travel](08-which-enables-time-travel.md) →
