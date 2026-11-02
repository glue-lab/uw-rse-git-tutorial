# 3.3 When Rebasing Gets Messy

▶ [Watch in the video (1:19:57)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4797s)

Throughout this tutorial, `git rebase` has been used as if it were magic, which runs a
little counter to the point. Sometimes you want to paint a clean picture of a project's
history, but the changes made along the way conflict with each other at many different
steps. Rebasing then means resolving conflicts commit by commit. It's still worth doing to
tell a good story, but it isn't free.

**Starting point:** your Vertebrate clone from [3.2](02-opening-a-pull-request.md), with a
local `testing-abcs` branch.

## On GitHub

**[Pull request #4: Draft: Fixes to built-in Environments](https://github.com/glue-lab/vertebrate/pull/4)**

The description explains why the branch exists (bugs surfaced after the first release),
flags that it's a **draft**, and states what must be true before it's ready: rebased on
top of `testing-abcs`, with tests written for the built-ins. That rebase is what this
module attempts.

> **About the branch name:** pull request #4 tracks `environment-fixes`, which will move
on as that work continues. The `environment-fixes-uw-rse` branch preserves it exactly as
it was during the talk, so the conflicts below stay reproducible.

## Back up, then rebase

```bash
git checkout environment-fixes-uw-rse
git checkout -b environment-fixes-uw-rse-backup  # a backup, as in 2.3
git checkout environment-fixes-uw-rse
git rebase testing-abcs
```

The very first commit to be replayed conflicts:

```
$ git rebase testing-abcs
Auto-merging src/vertebrate/builtins/psql.py
CONFLICT (content): Merge conflict in src/vertebrate/builtins/psql.py
error: could not apply 71c7274... Debug: For Windows compatibility, use `shutil.which` to check for executables.
...
```

`git status` shows how far along the rebase is (1 of 15 commits) and what needs attention:

```bash
git status
```

```
$ git status
interactive rebase in progress; onto b3fcb2c
Last command done (1 command done):
   pick 71c7274 Debug: For Windows compatibility, use `shutil.which` to check for executables.
Next commands to do (14 remaining commands):
   pick dde9dbb Debug: Don't shadow inherited environment variables.
   pick 4d4a3bc Raise `KeyError` for missing executables.
...
Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
	both modified:   src/vertebrate/builtins/psql.py
```

## Resolve with project knowledge

Open `src/vertebrate/builtins/psql.py` and find the conflict markers:

```
<<<<<<< HEAD
    def _find_psql_on_path(self):
        completed = subprocess.run(
            ("which", "psql"), env=os.environ, capture_output=True
        )
        psql_path = completed.stdout.decode("utf-8").strip()
        if psql_path == "":
=======
    def _find_psql_on_path(self) -> str:
        psql_path = shutil.which("psql")
        if psql_path is None:
>>>>>>> 71c7274 (Debug: For Windows compatibility, use `shutil.which` to check for executables.)
```

The top half is the method as it stands on `testing-abcs`; the bottom half is the commit
being replayed. Git can't know which is right, but
the project's history can: this commit exists precisely to replace calling `which` in a
subprocess with Python's `shutil.which`. So keep the bottom version, delete the top one
along with the markers, and continue:

```bash
git add src/vertebrate/builtins/psql.py
git rebase --continue
```

## And another one

The next commit conflicts too, this time in two files:

```
$ git rebase --continue
CONFLICT (content): Merge conflict in src/vertebrate/builtins/os.py
CONFLICT (content): Merge conflict in src/vertebrate/builtins/psql.py
error: could not apply dde9dbb... Debug: Don't shadow inherited environment variables.
```

Here neither side is simply right. The linting work changed *how* a tuple of command
arguments is written (rule `RUF005`), while this commit changes *what* gets passed along
(the environment variables). The correct resolution combines them: keep the environment
fix, written in the style the linter expects. And after that, there are more conflicts
still.

## Back out (or keep going)

You can work through the remaining conflicts the same way. To stop instead, abort the
rebase, which puts the branch back exactly as it was:

```bash
git rebase --abort
git log --oneline -1  # back at the original tip
```

```
$ git log --oneline -1
234547a Raise on non-zero exit in `SSHEnvironment`, matching `OSEnvironment`.
```

If you'd already finished and regretted it, the backup branch still points at the
original state.

## The lesson

Rebasing can be genuinely hard, and that can shape how you plan concurrent development.
If two pieces of work are going to change much of the same code, it's sometimes easier to
schedule one after the other than to reconcile them later.

---

← [3.2 Opening a Pull Request (testing)](02-opening-a-pull-request.md) · [Index](../README.md)
