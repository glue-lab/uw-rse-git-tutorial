# 3.2 Opening a Pull Request (testing)

▶ [Watch in the video (1:17:23)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4643s)

While the linting pull request from [3.1](01-reviewing-a-pull-request.md) was in review,
work didn't have to stop. The `testing-abcs` branch, which adds tests that do more than
pass vacuously, was built on top of the `linting` branch in the meantime. Once linting was
merged, the testing work was rebased onto the new `main` and a pull request was opened for
it.

**Starting point:** your Vertebrate clone from [3.1](01-reviewing-a-pull-request.md).

## On GitHub

**[Pull request #10: Provide tests for core classes](https://github.com/glue-lab/vertebrate/pull/10)**

- Pull requests can be opened at various stages. This one was opened during the talk as a
  stub, a placeholder to be filled in before review.
- **[The commits](https://github.com/glue-lab/vertebrate/pull/10/commits)** tell the story
  of the testing work: configure testing, add unit tests for individual core classes, then
  provide generic tests that accompany each of them ("Provide tests for any …").

## Read the story locally

```bash
git checkout testing-abcs
git log --oneline --reverse origin/linting..testing-abcs  # oldest first
```

`origin/linting..testing-abcs` means "commits on `testing-abcs` that aren't on the linting
branch", which is exactly the testing work:

```
$ git log --oneline --reverse origin/linting..testing-abcs
3a18897 Configure testing for project.
1b10f30 Add unit tests for `compute.py`.
b8e66ad Touch-up: Ignore test coverage output files.
6228a80 Touch-up: Don't count abstract methods towards test coverage.
...
e65dd6e Allow read-only namespaces to pass generic tests.
084e745 Provide tests for any set of orders.
33e453a Provide tests for any plan.
```

## Catch it up with main

On GitHub, `testing-abcs` still sits on the last commit of the `linting` branch. In the
video, it's rebased onto `main`, which by then includes the merged linting work, so its 19
commits play on top of the latest main line (as in
[2.2](../02-storytelling-with-git/02-get-your-story-straight.md)). You can do the same
locally; nothing is pushed.

`main` will keep moving as more pull requests are merged, so to rebase onto `main` as it
was during the talk, use the commit that merged the linting pull request:

```bash
git log --oneline --graph -3 c61f9ca  # the merge of pull request #5
git rebase c61f9ca                    # main as of the talk
git log --oneline -21                 # the 19 commits now sit on top of it
```

```
$ git rebase c61f9ca
Successfully rebased and updated refs/heads/testing-abcs.

$ git log --oneline -21
...
33abcc2 Configure testing for project.
c61f9ca Merge pull request #5 from glue-lab/linting
```

The rewritten commits get new hashes (yours will differ from these), but they tell the
same story, now starting from the merged linting work.

## Open a pull request of your own

You can't push to Vertebrate, but you can practice on your own `git-tutorial` repository
from section 1, which already has a `python-script` branch on GitHub
([1.13](../01-overview/13-versions-can-be-shared.md)):

1. On your repository's GitHub page, open **Pull requests → New pull request**, and
   compare `python-script` against `main`.
2. Write a description that tells the story: what the change is for, what the branch does,
   and a **proof of success**, such as `python3 script.py` printing a greeting.
3. Open it, as a **draft** if it isn't ready for review yet.

Pushing a new branch with `git push -u origin <branch>` usually makes GitHub offer a
**Compare & pull request** button, which is the quickest way in.

---

← [3.1 Reviewing a Pull Request (linting)](01-reviewing-a-pull-request.md) · [Index](../README.md) · [3.3 When Rebasing Gets Messy](03-when-rebasing-gets-messy.md) →
