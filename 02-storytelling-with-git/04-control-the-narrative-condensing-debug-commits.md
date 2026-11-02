# 2.4 Control The Narrative: Condensing Debug Commits

▶ [Watch in the video (55:32)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3332s)

Fixing a bug is often iterative: you try something, commit, test, try something else.
Committing as you go is good practice, but it can leave a long trail of small "debug"
commits. Are those worth telling in your project's story, or were they only relevant to
the moment you were in? You get to choose how much space a series of changes takes up in
your history.

**Starting point:** the `testing` branch from [2.1](01-choose-your-own-adventure.md), with
`pytest` installed in an activated virtual environment.

## Make a change that breaks a test

```bash
git status  # on branch testing

cat > tests/test_project.py <<'EOF'
def test_project():
    result = 0
    assert result == 2
EOF

git add . && git commit -m "Cool new feature"
pytest  # fails: assert 0 == 2
```

## Debug it, committing as you go

```bash
cat > tests/test_project.py <<'EOF'
def test_project():
    # How I think the result should be computed
    result = 0

    # What I think the result should be
    assert result == 2
EOF
git add . && git commit -m "Diagnosing the problem"
pytest  # still failing

cat > tests/test_project.py <<'EOF'
def test_project():
    # How I think the result should be computed
    result = 0
    result += 1

    # What I think the result should be
    assert result == 2
EOF
git add . && git commit -m "Debug: Result needs to be higher"
pytest  # still failing

cat > tests/test_project.py <<'EOF'
def test_project():
    # How I think the result should be computed
    result = 0
    result += 1
    result += 1

    # What I think the result should be
    assert result == 2
EOF
git add . && git commit -m "Debug: Result needs to be even higher"
pytest  # passes
```

## Back up before rewriting history

You're about to change history, so first save a reference to the current state
(see [2.3](03-control-the-narrative-backups-and-undoing-commits.md)):

```bash
git checkout -b testing-troubleshooting
git checkout testing
git log  # four new commits on top of "Add testing to project"
```

## Option 1: collapse the debugging into one commit

Reset to the "Cool new feature" commit. Without `--hard`, `git reset` moves the branch
back but **keeps your files as they are now**, so all the debugging work shows up as one
set of uncommitted changes:

```bash
git reset <hash-of-cool-new-feature>  # from git log
git status                            # tests/test_project.py modified
cat tests/test_project.py             # still the final, working version
git add . && git commit -m "Debug: Result should be 2"
```

## Option 2: fold the fix into the feature itself

If the debugging isn't worth a commit of its own, reset to the same commit and **amend**
it instead, so the working code simply lives in "Cool new feature":

```bash
git reset <hash-of-cool-new-feature>
git add .
git commit --amend
```

Either way, `git diff` between the old and new commits shows exactly what was needed to
fix the problem, without the trial and error in between.

## Notes

- `git reset <commit>` (the default "mixed" mode) keeps your changes in the working
directory, unstaged. `git reset --soft <commit>` also keeps them staged.
`git reset --hard <commit>` discards them, which is why it's the one to use with care.
- Amending replaces a commit with a new one (it gets a new hash). That's fine for local
commits; for commits you've already pushed, see
[2.6](06-control-the-narrative-force-pushing.md).

---

← [2.3 Control The Narrative: Backups & Undoing Commits](03-control-the-narrative-backups-and-undoing-commits.md) · [Index](../README.md) · [2.5 Control The Narrative: What If It's Too Late?](05-control-the-narrative-what-if-its-too-late.md) →
