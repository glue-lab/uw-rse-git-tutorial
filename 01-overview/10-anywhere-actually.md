# 1.10 … Anywhere, Actually

▶ [Watch in the video (23:35)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1415s)

GitHub is popular, but it's one option of many. A Git repository can live anywhere that's
set up to host one: GitLab, Bitbucket, a server you run yourself. Here the same project
gets a second remote on GitLab.

**Starting point:** the repository from [1.9](09-versions-can-live-elsewhere.md), and an
empty project created on GitLab. This module is optional: nothing later depends on the
GitLab remote.

## Commands

```bash
GIT_URL="git@gitlab.com:<your-group>"
GIT_URL="${GIT_URL}/git-tutorial.git"
git remote add gitlab "${GIT_URL}"
git remote -v
git push -u gitlab main
git remote rename origin github  # or not
```

The URL is built in two steps only to keep each line short. Now the repository knows about
two remotes:

```
$ git remote -v
gitlab	git@gitlab.com:<your-group>/git-tutorial.git (fetch)
gitlab	git@gitlab.com:<your-group>/git-tutorial.git (push)
origin	git@github.com:<your-username>/git-tutorial.git (fetch)
origin	git@github.com:<your-username>/git-tutorial.git (push)
```

Pushing to `gitlab` instead of `origin` puts the exact same project, history and all, on a
different service. Only the web interface around it differs.

## Nothing is magic about "origin"

As far as Git is concerned, `origin` is just a name, and `git remote rename` can change
it. That said, people (and tools) often expect a repository's primary remote to be called
`origin`, so it's usually worth keeping. The rest of this tutorial assumes `origin`, so if
you tried the rename, undo it with `git remote rename github origin`.

---

← [1.9 Versions Can Live Elsewhere](09-versions-can-live-elsewhere.md) · [Index](../README.md) · [1.11 A Clone Is A Local Copy](11-a-clone-is-a-local-copy.md) →
