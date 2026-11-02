# 2.5 Control The Narrative: What If It's Too Late?

▶ [Watch in the video (1:04:30)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3870s)

Sometimes history feels cemented: you've already built other work on top of commits you'd
rather not keep. Say a new feature branched off before the debugging commits were cleaned
up. Is it too late to change the story?

It isn't. Clean up the base first (as in [2.4](04-control-the-narrative-condensing-debug-commits.md)),
then use **`git rebase --onto`** to transplant the newer work onto the cleaned-up base,
leaving the messy commits behind. It's important to amend the base commit *before*
rebasing.

**Starting point:** after [2.4](04-control-the-narrative-condensing-debug-commits.md):
`testing` holds the cleaned-up "Cool new feature" commit, and `testing-troubleshooting`
still points at the original debugging commits.

## Build new work on the messy history

```bash
git checkout testing-troubleshooting
git checkout -b new-feature

echo "Spec for new feature" > planning.md
echo 'print("New feature")' > feature.py

git add planning.md
git commit -m "Planning for new feature"
git add feature.py
git commit -m "Initial implementation"
```

`new-feature` now sits on top of the debugging commits that `testing` has already cleaned
up:

```
$ git log --oneline --graph testing new-feature
* 879a895 Cool new feature
| * d8d1d91 Initial implementation
| * 3096981 Planning for new feature
| * 20bfdb1 Debug: Result needs to be even higher
| * f11c754 Debug: Result needs to be higher
| * 1840b45 Diagnosing the problem
| * 4895266 Cool new feature
|/
* bee8755 Add testing to project
...
```

## Transplant it with rebase --onto

`git rebase --onto <new-base> <old-base>` takes the commits on your current branch that
come after `<old-base>` and replays them on top of `<new-base>`. Following the letters in
[this Stack Overflow answer](https://stackoverflow.com/questions/29914052/how-to-git-rebase-a-branch-with-the-onto-command),
call them `F` and `D`:

```bash
git checkout testing
git log --oneline  # copy the hash of the clean "Cool new feature" commit
F=<hash>           # the new base: where the work should attach

git checkout new-feature
git log --oneline  # copy the hash of "Debug: Result needs to be even higher"
D=<hash>           # the old base: where the work currently attaches

git rebase --onto $F $D
```

```
$ git log --oneline --graph testing new-feature
* 0aa3e08 Initial implementation
* f465306 Planning for new feature
* 879a895 Cool new feature
* bee8755 Add testing to project
...
```

Exactly the intended history: the clean testing story, then the new feature's commits on
top. The debugging process is paved over; all that was needed was the working "Cool new
feature".

> Here the old base is also the tip of `testing-troubleshooting`, so
`git rebase --onto testing testing-troubleshooting` would do the same thing. Branch names
work anywhere hashes do.

---

← [2.4 Control The Narrative: Condensing Debug Commits](04-control-the-narrative-condensing-debug-commits.md) · [Index](../README.md) · [2.6 Control The Narrative: Force Pushing](06-control-the-narrative-force-pushing.md) →
