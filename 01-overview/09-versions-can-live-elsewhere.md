# 1.9 Versions Can Live Elsewhere

▶ [Watch in the video (20:25)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1225s)

Everything so far has happened on one computer. Part of what makes Git useful is that
versions can live elsewhere too. A **remote** is a copy of your repository that lives
somewhere else, and GitHub is a popular place to keep one.

**Starting point:** the repository from [1.8](08-which-enables-time-travel.md), on `main`.
You'll also need a GitHub account with an SSH key set up (see
[Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)).

## Create an empty repository on GitHub

On GitHub, choose **New repository**, name it `git-tutorial`, and create it **without**
a README, license, or `.gitignore`, so that it starts out empty.

## Point your local repository at it

```bash
git remote -v  # no remote set up
git remote add origin \
  git@github.com:<your-username>/git-tutorial.git
git remote -v
git push -u origin main
```

`git remote add` gives the remote a name and a location. **`origin`** is the conventional
name for a repository's main remote. Afterwards, `git remote -v` lists it:

```
$ git remote -v
origin	git@github.com:<your-username>/git-tutorial.git (fetch)
origin	git@github.com:<your-username>/git-tutorial.git (push)
```

`git push` sends the `main` branch to `origin`. The `-u` sets `origin/main` as the
branch's upstream, so later pushes and pulls on `main` know where to go:

```
$ git push -u origin main
...
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

Refresh the repository's page on GitHub and your commits are there.

---

← [1.8 … Which Enables Time Travel](08-which-enables-time-travel.md) · [Index](../README.md) · [1.10 … Anywhere, Actually](10-anywhere-actually.md) →
