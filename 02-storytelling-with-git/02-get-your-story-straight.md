# 2.2 Get Your Story Straight

▶ [Watch in the video (46:40)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2800s)

Parallel timelines are useful, but at some point there's a main version of the project
being built up over time. How do you tell a linear, step-by-step story when you've been
working in choose-your-own-adventure mode?

**`git rebase`** is invaluable here. Run on your branch with another branch as its
argument, it finds the last point where the two agreed, sets aside the commits you've made
since, and replays them one by one on top of the other branch. The result reads as if your
work had started from the other branch's latest state all along.

**Starting point:** the `linting` and `testing` branches from
[2.1](01-choose-your-own-adventure.md).

## Rebase testing onto linting

Suppose linting was finished (and merged into the main line) first. Replay the testing
work on top of it:

```bash
git checkout testing
git rebase linting
```

Things mostly run smoothly, but sometimes Git needs your input. Here, both branches
created `requirements.txt` with different contents, so Git can't decide on its own which
version is correct:

```
$ git rebase linting
Auto-merging requirements.txt
CONFLICT (add/add): Merge conflict in requirements.txt
error: could not apply 3368bba... Add testing to project
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
...
```

## Resolve the conflict

`git status` shows where things stand: the new test file is ready to go, but
`requirements.txt` needs a decision.

```bash
git status
cat requirements.txt
```

```
$ git status
...
Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
	both added:      requirements.txt
```

Git marks up the conflicting file to show both versions. The part after `<<<<<<< HEAD` is
the branch you're rebasing onto (`linting`); the part before `>>>>>>>` is from the commit
being replayed:

```
$ cat requirements.txt
<<<<<<< HEAD
ruff
=======
pytest
>>>>>>> 3368bba (Add testing to project)
```

Deciding what's correct takes your knowledge of the project. Here the two shouldn't
replace each other; they're additive. Edit the file to keep both, without the markers:

```bash
cat > requirements.txt <<'EOF'
ruff
pytest
EOF
git add requirements.txt  # mark the conflict as resolved
git rebase --continue     # may open an editor for the commit message
```

## A straight story

```bash
git log --oneline --graph --all
```

```
$ git log --oneline --graph --all
* bee8755 Add testing to project
* 1fb8b76 Add linting to the project
| * d051e21 Update greeting in Python script
| * 09a1c62 Add Python script
|/
* 33aeb78 Add description to README
* 70aae54 Initialize project README
```

The history now starts from `main`, adds linting, then adds testing, one step after
another, even though the work happened in parallel.

> The slides show `git rebase main`, the common case of catching a branch up with the main
line. Rebasing onto `linting` here works the same way.

---

← [2.1 Choose Your Own Adventure](01-choose-your-own-adventure.md) · [Index](../README.md) · [2.3 Control The Narrative: Backups & Undoing Commits](03-control-the-narrative-backups-and-undoing-commits.md) →
