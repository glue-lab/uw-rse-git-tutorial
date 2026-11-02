# The Story Of Your Project: UW RSE Git Tutorial

Companion materials for
**[The Story Of Your Project](https://www.youtube.com/watch?v=7x6C8_FXEK0)**, a Git
tutorial given to the Research Software Engineering (RSE) community at UW-Madison on
Oct 26, 2026.

The tutorial builds up a working knowledge of Git from first principles, then showcases
how to use Git as a communication tool to deliberately shape a project's history so
that it communicates clearly to others. It closes with a look at real-world development on
[Vertebrate](https://github.com/glue-lab/vertebrate), an open-source project.

## How to use this repo

Each markdown file below corresponds to one chapter of the video. It records the commands
the chapter covered in a format that makes them easier to try on your own, and it provides
some notes on what's happening in each.

Just as the commands from the video do, the files in this repository build on each other:
run them in order in a scratch directory and you'll recreate the examples from the talk.
You'll need:

- `git`, for everything
- a GitHub account with an SSH key, from 1.9 onward (and optionally a GitLab account for
  1.10)
- Python 3, from 2.1 onward

Section 3 reads real pull requests on GitHub and needs no account.

Commit hashes, dates, and names in the example output will differ from yours: they depend
on who made each commit and when. Wherever a file shows `<commit>` or `<hash>`, use one
from your own `git log`.

## Modules

| | Module | Video |
|---|---|---|
| | **Introduction** | [0:00](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=0s) |
| | **Before We Begin** | [2:02](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=122s) |
| **1** | **Overview** | |
| 1.1 | [Git Is A Program](01-overview/01-git-is-a-program.md) | [2:56](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=176s) |
| 1.2 | [A Repository Is A Directory](01-overview/02-a-repository-is-a-directory.md) | [4:17](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=257s) |
| 1.3 | [… That Contains .git](01-overview/03-that-contains-dot-git.md) | [5:26](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=326s) |
| 1.4 | [Let's Add Files](01-overview/04-lets-add-files.md) | [7:27](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=447s) |
| 1.5 | [Git Tracks Changes](01-overview/05-git-tracks-changes.md) | [8:43](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=523s) |
| 1.6 | [Git Saves Changes](01-overview/06-git-saves-changes.md) | [12:44](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=764s) |
| 1.7 | [Git Is Version Control](01-overview/07-git-is-version-control.md) | [15:12](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=912s) |
| 1.8 | [… Which Enables Time Travel](01-overview/08-which-enables-time-travel.md) | [18:45](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1125s) |
| 1.9 | [Versions Can Live Elsewhere](01-overview/09-versions-can-live-elsewhere.md) | [20:25](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1225s) |
| 1.10 | [… Anywhere, Actually](01-overview/10-anywhere-actually.md) | [23:35](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1415s) |
| 1.11 | [A Clone Is A Local Copy](01-overview/11-a-clone-is-a-local-copy.md) | [26:17](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1577s) |
| 1.12 | [… Just Like Any Other](01-overview/12-just-like-any-other.md) | [30:54](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1854s) |
| 1.13 | [Versions Can Be Shared](01-overview/13-versions-can-be-shared.md) | [32:12](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=1932s) |
| 1.14 | [… And Updated Anywhere](01-overview/14-and-updated-anywhere.md) | [34:15](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2055s) |
| 1.15 | [This Is How You Collaborate!](01-overview/15-this-is-how-you-collaborate.md) | [35:28](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2128s) |
| **2** | **Storytelling with Git** | |
| 2.0 | [Storytelling with Git](02-storytelling-with-git/00-storytelling-with-git.md) | [37:29](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2249s) |
| 2.1 | [Choose Your Own Adventure](02-storytelling-with-git/01-choose-your-own-adventure.md) | [38:51](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2331s) |
| 2.2 | [Get Your Story Straight](02-storytelling-with-git/02-get-your-story-straight.md) | [46:40](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=2800s) |
| 2.3 | [Control The Narrative: Backups & Undoing Commits](02-storytelling-with-git/03-control-the-narrative-backups-and-undoing-commits.md) | [51:37](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3097s) |
| 2.4 | [Control The Narrative: Condensing Debug Commits](02-storytelling-with-git/04-control-the-narrative-condensing-debug-commits.md) | [55:32](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3332s) |
| 2.5 | [Control The Narrative: What If It's Too Late?](02-storytelling-with-git/05-control-the-narrative-what-if-its-too-late.md) | [1:04:30](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=3870s) |
| 2.6 | [Control The Narrative: Force Pushing](02-storytelling-with-git/06-control-the-narrative-force-pushing.md) | [1:10:12](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4212s) |
| **3** | **Real-World Usage** | |
| 3.0 | [Real-World Usage: Vertebrate](03-real-world-usage/00-real-world-usage-vertebrate.md) | [1:10:34](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4234s) |
| 3.1 | [Reviewing a Pull Request (linting)](03-real-world-usage/01-reviewing-a-pull-request.md) | [1:11:38](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4298s) |
| 3.2 | [Opening a Pull Request (testing)](03-real-world-usage/02-opening-a-pull-request.md) | [1:17:23](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4643s) |
| 3.3 | [When Rebasing Gets Messy](03-real-world-usage/03-when-rebasing-gets-messy.md) | [1:19:57](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=4797s) |
| | **Thank You & Resources** | [1:26:06](https://www.youtube.com/watch?v=7x6C8_FXEK0&t=5166s) |

## Resources

- [Git Carpentry Materials: Version Control with Git](https://swcarpentry.github.io/git-novice/index.html)
- [How to Write a Git Commit Message](https://chris.beams.io/git-commit)
- [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [Stack Overflow go-to for `git rebase --onto`](https://stackoverflow.com/questions/29914052/how-to-git-rebase-a-branch-with-the-onto-command)
