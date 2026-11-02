# 2.3 Control The Narrative: Backups & Undoing Commits

▶ [Watch in the video (51:37)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3097s)

One of the best things about Git as a storytelling device is that you can be intentional
about your commits: you get to construct the history that best communicates how your
project evolved. That includes leaving things out. If you change something and think
"wait, no", the change doesn't have to become part of the story at all.

**Starting point:** the rebased `testing` branch from
[2.2](02-get-your-story-straight.md).

## Make a backup first

When you're about to destroy project history, save a reference to it with a **backup
branch**. A branch is like a variable name pointing at a version of your code: as long as
it exists, you can always jump back to that version.

```bash
git checkout -b backup
git checkout testing
```

(`git branch backup` does the same thing without switching branches.)

## Make a change you'll regret

Suppose the project feels under-organized, so you move the script into a nested structure
that you think better advertises what it does. `git mv` moves a file and records the move
in one step:

```bash
mkdir -p loggers/messages/start
git mv script.py loggers/messages/start/
git status  # renamed: script.py -> loggers/messages/start/script.py
git commit -m "Move script into project structure"
python3 loggers/messages/start/script.py
```

On reflection, that path is far too verbose to type every time. You'd rather go back.

## Undo it entirely

Rather than adding another commit that moves the file back, erase the commit:

```bash
git log --oneline     # the move is the latest commit
git reset --hard HEAD~1
git log --oneline     # the move is gone
```

```
$ git reset --hard HEAD~1
HEAD is now at bee8755 Add testing to project
```

`HEAD~1` means "one commit before the current one", a handy alternative to copying a hash.
The ill-advised over-engineering never makes it into the history.

## Notes

- `git reset --hard` discards the commit **and** any uncommitted changes. That's exactly
  what you want here, and exactly why the backup branch matters when you're less sure.
- If you made the `backup` branch, it still points at the original state. Delete it once
  you're happy with `git branch -D backup`.
- This is safest for commits that only exist locally. For commits you've already pushed,
  see [2.6](06-control-the-narrative-force-pushing.md).

---

← [2.2 Get Your Story Straight](02-get-your-story-straight.md) · [Index](../README.md) · [2.4 Control The Narrative: Condensing Debug Commits](04-control-the-narrative-condensing-debug-commits.md) →
