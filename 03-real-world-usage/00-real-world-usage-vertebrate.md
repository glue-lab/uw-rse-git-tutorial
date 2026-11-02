# 3.0 Real-World Usage: Vertebrate

▶ [Watch in the video (1:10:34)](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4234s)

Sections 1 and 2 used deliberately tiny examples: tests that pass vacuously, one-line
scripts. This section looks at what the same practices look like on a real project.

**[Vertebrate](https://github.com/glue-lab/vertebrate)** is an open-source package
maintained at GLUE for specifying abstract interfaces that we like to use in our code. It
started in spring 2026 and is still relatively young, which makes its history small enough
to read but real enough to be messy in places.

## Where to look

- **[The repository](https://github.com/glue-lab/vertebrate)**, starting with its README
- **[Pull requests](https://github.com/glue-lab/vertebrate/pulls?q=is%3Apr)**: proposals
  to bring feature branches into `main`, each with a description and its sequence of
  commits

The next three modules each follow one pull request:

- [3.1 Reviewing a Pull Request](01-reviewing-a-pull-request.md): linting, reviewed and
  merged
- [3.2 Opening a Pull Request](02-opening-a-pull-request.md): testing, opened during the
  talk
- [3.3 When Rebasing Gets Messy](03-when-rebasing-gets-messy.md): a draft with conflicts
  to work through

## Get a copy

```bash
git clone https://github.com/glue-lab/vertebrate.git
cd vertebrate
```

Cloning over HTTPS works without any GitHub setup, since you'll only be reading.

---

← [2.6 Control The Narrative: Force Pushing](../02-storytelling-with-git/06-control-the-narrative-force-pushing.md) · [Index](../README.md) · [3.1 Reviewing a Pull Request (linting)](01-reviewing-a-pull-request.md) →
