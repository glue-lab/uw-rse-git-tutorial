# 3.1 Reviewing a Pull Request (linting)

▶ [Watch in the video (1:11:38)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4298s)

Hosting services like GitHub and GitLab let you open a **pull request** (GitLab calls it a
merge request): a proposal to bring the commits on a feature branch into the main version
of the code. This is where the storytelling pays off. A reviewer reads the description to
learn *why* the change exists, then reads the commits to learn *how* it was built.

## On GitHub

**[Pull request #5: Add code linting with `ruff`](https://github.com/glue-lab/vertebrate/pull/5)**

- **The description** sets the stage: what problem the change solves (consistent code
  formatting), what the branch does about it, and a **proof of success**, a command a
  reviewer can run to check that it works.
- **[The commits](https://github.com/glue-lab/vertebrate/pull/5/commits)** tell the story
  bit by bit: add `ruff` as a dependency, configure its rules, then satisfy those rules
  one at a time. Each rule code in a commit message
  (e.g. [`F401`](https://docs.astral.sh/ruff/rules/unused-import/), unused imports) can be
  looked up directly.
- **Commits can be documentation.** The rules commit explains *which* families of lint
  rules the project adopts, and the description simply points to it.

## Check the proof of success locally

This is the check a reviewer would run before approving:

```bash
git clone https://github.com/glue-lab/vertebrate.git
cd vertebrate
python3 -m venv venv && source venv/bin/activate
pip install ruff

git branch            # on main
git checkout linting
git log               # the same commits as the pull request
ruff check            # "All checks passed!"
```

## Read the story from the merged history

In the video, the pull request is merged at this point. It's already merged, so you can
see what merging does to the story: nothing is lost. GitHub records a **merge commit**
whose two parents are the previous `main` and the tip of the `linting` branch, and every
commit from the pull request becomes part of `main`'s history.

```bash
git checkout main
git log --oneline --graph -6 c61f9ca  # the merge commit for pull request #5
```

```
*   c61f9ca Merge pull request #5 from glue-lab/linting
|\
| * 06f32f3 Wrap overly long lines (rule `E501`).
| * 64c4a93 Better syntax for constructing tuples (rule `RUF005`).
| * 45909ff Touch-up: Ensure example narration matches code.
| * a78ed04 Note: Transfer targets can yield false positives for rule `F821`.
| * e5ec666 Ensure variables are used (rule `F841`).
```

To list just the pull request's commits, oldest first, ask for everything reachable from
the merge's second parent (`^2`, the branch) but not its first (`^1`, the old `main`):

```bash
git log --oneline --reverse c61f9ca^1..c61f9ca^2  # the 16 commits, in story order
```

Then pick any chapter of the story and read it in full, message and change together:

```bash
git show d4b687c  # "Remove unused imports (rule `F401`)."
```

---

← [3.0 Real-World Usage: Vertebrate](00-real-world-usage-vertebrate.md) · [Index](../README.md) · [3.2 Opening a Pull Request (testing)](02-opening-a-pull-request.md) →
