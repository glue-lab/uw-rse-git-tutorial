# 2.6 Control The Narrative: Force Pushing

▶ [Watch in the video (1:10:12)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4212s)

Rewriting history (amending, resetting, rebasing) replaces commits with new ones. If the
branch was already pushed, the remote still has the old commits, and the two versions now
disagree. On a feature branch you created, you can make the remote match what you have
locally by **force pushing**.

**Starting point:** the `testing` branch from [2.5](05-control-the-narrative-what-if-its-too-late.md).

## Push, rewrite, push again

```bash
git checkout testing
git push -u origin testing

git commit --amend  # rewrite the latest commit (e.g. reword its message)
git push            # rejected
```

Git refuses the second push, because it would throw away the commit that's on the remote:

```
$ git push
 ! [rejected]        testing -> testing (non-fast-forward)
error: failed to push some refs to 'github.com:<your-username>/git-tutorial.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
```

Here that's not a problem to fix but a sign you rewrote history on purpose. Tell Git to
replace the remote branch with yours:

```bash
git push --force-with-lease
```

```
$ git push --force-with-lease
 + 879a895...5c19fbf testing -> testing (forced update)
```

## Notes

- `--force-with-lease` is a safer variant of `--force` (shown on the slide). It refuses to
  overwrite the remote branch if someone else has pushed to it since you last fetched, so
  you can't silently discard a collaborator's commits.
- Only force push branches that are yours. Rewriting a shared branch like `main` changes
  history out from under everyone else working from it.

---

← [2.5 Control The Narrative: What If It's Too Late?](05-control-the-narrative-what-if-its-too-late.md) · [Index](../README.md) · [3.0 Real-World Usage: Vertebrate](../03-real-world-usage/00-real-world-usage-vertebrate.md) →
