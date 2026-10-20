
# 12 - Git & GitHub Interview Preparation

## 📌 Overview

This module prepares students and developers for Git and GitHub interviews through theoretical questions, practical commands, scenario-based questions, and real-world troubleshooting.

### Topics Covered

- Git fundamentals
- Git commands
- Branching and merging
- GitHub collaboration
- Advanced Git
- Troubleshooting
- Scenario-based questions
- Practical interview tasks

---

# Section 1: Git Fundamentals

### 1. What is Git?

Git is a distributed version control system used to track changes in files and coordinate development among multiple developers.

### 2. What is version control?

Version control records changes to files over time so developers can review history, compare versions, and collaborate.

### 3. What is the difference between Git and GitHub?

Git is version-control software. GitHub is a platform that hosts Git repositories and provides collaboration tools such as Pull Requests and Issues.

### 4. What is a repository?

A repository contains project files and the version-control data used to track their history.

### 5. What is a distributed version control system?

It is a system in which each clone normally contains the repository's history, allowing developers to work locally and synchronize changes later.

### 6. What is a commit?

A commit records a snapshot of changes in the repository history, along with metadata such as the author, timestamp, and commit message.

### 7. What is the `.git` directory?

It stores Git's repository data, including objects, references, and configuration for the local repository.

### 8. What is the working directory?

The working directory contains the checked-out project files that you view and edit.

### 9. What is the staging area?

The staging area, also called the index, holds changes selected for inclusion in the next commit.

### 10. What is HEAD?

HEAD identifies the current checkout, usually the current branch or, in detached HEAD state, a specific commit.

---

# Section 2: Basic Git Commands

### 11. How do you initialize a repository?

```bash
git init
```

### 12. How do you check Git's version?

```bash
git --version
```

### 13. How do you check repository status?

```bash
git status
```

### 14. How do you stage a file?

```bash
git add filename.txt
```

### 15. How do you commit staged changes?

```bash
git commit -m "Add project documentation"
```

### 16. How do you view commit history?

```bash
git log --oneline
```

### 17. How do you clone a repository?

```bash
git clone REPOSITORY_URL
```

Replace `REPOSITORY_URL` with the actual repository URL.

### 18. How do you check configured remote URLs?

```bash
git remote -v
```

### 19. How do you push commits?

```bash
git push origin main
```

This assumes the branch is named `main` and the remote is named `origin`.

### 20. How do you download and integrate remote changes?

```bash
git pull origin main
```

By default, Git typically fetches and merges. Configuration or command options can change the integration method.

---

# Section 3: Branching and Merging

### 21. What is a branch?

A branch is a movable reference to a commit that supports an independent line of development.

### 22. How do you create a branch?

```bash
git branch feature-login
```

### 23. How do you switch branches?

```bash
git switch feature-login
```

### 24. How do you create and switch to a branch in one command?

```bash
git switch -c feature-login
```

### 25. What is merging?

Merging integrates changes from one branch into another branch.

### 26. What is a merge conflict?

A merge conflict occurs when Git cannot automatically reconcile changes, requiring a developer to resolve the affected files.

### 27. What is the difference between merge and rebase?

- **Merge:** Integrates branch histories and may create a merge commit.
- **Rebase:** Replays commits on a new base and creates new commit identities for the replayed commits.

### 28. How do you delete a merged local branch?

```bash
git branch -d feature-login
```

### 29. What is a detached HEAD?

HEAD points directly to a commit instead of a local branch. Commits created in this state should be preserved on a branch if you need to keep them.

### 30. How do you view local and remote-tracking branches?

```bash
git branch -a
```

---

# Section 4: GitHub Collaboration

### 31. What is a Pull Request?

A Pull Request proposes changes from one branch or repository into another and provides a place for review and discussion.

### 32. What is a fork?

A fork is a separate GitHub repository based on another repository, commonly used for contributions without direct write access.

### 33. What is the difference between fork and clone?

- **Fork:** Creates a separate repository under a GitHub account.
- **Clone:** Copies a repository to a local computer.

### 34. What is an upstream remote?

It commonly refers to the original repository from which a fork was created.

Example:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/PROJECT.git
```

### 35. What is a GitHub Issue?

An Issue tracks bugs, tasks, feature requests, or other project discussions.

### 36. What is a code review?

A code review is the process of examining proposed changes for correctness, quality, security, maintainability, and consistency.

### 37. What is a protected branch?

A protected branch has rules that restrict certain operations, such as requiring Pull Request reviews or status checks before merging.

### 38. What is a GitHub Release?

A Release publishes a project version with release notes and optional downloadable assets, often associated with a Git tag.

### 39. What is GitHub Actions?

GitHub Actions automates workflows such as testing, building, and deploying applications.

### 40. What is a README file?

A README explains a repository's purpose, setup, usage, features, and other important project information.

---

# Section 5: Advanced Git Questions

### 41. What is `git stash`?

It temporarily saves local modifications so you can return to them later.

```bash
git stash push -m "Temporary changes"
```

### 42. What is the difference between `git revert` and `git reset`?

- `git revert` creates a new commit that reverses changes from an earlier commit.
- `git reset` moves the current branch reference and, depending on the mode, may also change the index and working tree.

### 43. What does `git cherry-pick` do?

It applies the changes introduced by a selected commit to the current branch.

```bash
git cherry-pick COMMIT_HASH
```

### 44. What is `git reflog`?

It displays recent local reference movements and can help locate commits after certain operations.

```bash
git reflog
```

### 45. What is a Git tag?

A tag identifies a specific commit, commonly to mark a software release.

```bash
git tag -a v1.0.0 -m "First stable release"
```

### 46. What does `git fetch` do?

It downloads remote updates without automatically integrating them into the current branch.

```bash
git fetch origin
```

### 47. What is a shallow clone?

A shallow clone downloads a limited portion of repository history rather than the full history.

```bash
git clone --depth 1 REPOSITORY_URL
```

### 48. What is `.gitignore`?

It specifies intentionally untracked files and paths that Git should ignore.

Example:

```gitignore
node_modules/
.venv/
__pycache__/
.env
```

### 49. What is an annotated tag?

An annotated tag is a Git object that includes metadata such as a tagger, date, and message. It is often used for releases.

### 50. What is a Git hook?

A Git hook is a script that runs when a supported Git event occurs, such as before a commit or after a merge.

---

# Section 6: Scenario-Based Interview Questions

## Scenario 1: Your push is rejected

**Question:** You run `git push`, but Git says the remote contains work that you do not have locally. What do you do?

**Answer:**

First, inspect the working tree and remote state.

```bash
git status
git fetch origin
```

If the remote branch is `main`, integrate its changes using the team's preferred merge or rebase workflow.

```bash
git pull --rebase origin main
git push origin main
```

Resolve conflicts if necessary before continuing. Avoid force-pushing as a first response.

## Scenario 2: You committed to the wrong branch

**Question:** You accidentally committed a feature to `main`, but it should be on a feature branch.

**Answer:**

If the commit is still at HEAD and you want to preserve it, create a branch pointing to the commit.

```bash
git branch feature-login
```

Then coordinate how to restore `main` based on whether the commit has been shared. If the commit was already pushed or other people depend on it, avoid rewriting shared history without agreement.

## Scenario 3: You need to switch branches with uncommitted changes

**Question:** Git refuses to switch branches because your changes would be overwritten.

**Answer:**

If the changes are ready, commit them:

```bash
git add .
git commit -m "Save current work"
```

Alternatively, stash them:

```bash
git stash push -m "Temporary work"
git switch main
```

Restore them when appropriate:

```bash
git stash pop
```

## Scenario 4: You accidentally deleted a commit

**Question:** How can you find a commit after a reset?

**Answer:**

Inspect the reflog:

```bash
git reflog
```

Identify the desired commit hash, then create a recovery branch:

```bash
git branch recovery-branch COMMIT_HASH
```

## Scenario 5: Two developers modified the same line

**Question:** How do you resolve the merge conflict?

**Answer:**

1. Open the conflicted file.
2. Review both versions.
3. Combine or select the correct changes.
4. Remove conflict markers.
5. Stage the resolved file.
6. Complete the merge or rebase operation.

For a merge:

```bash
git add filename.txt
git commit
```

For a rebase:

```bash
git add filename.txt
git rebase --continue
```

## Scenario 6: You committed a secret API key

**Question:** What should you do?

**Answer:**

1. Revoke or rotate the exposed credential immediately.
2. Remove the secret from the code and replace it with secure configuration.
3. Remove it from repository history if appropriate.
4. Coordinate the cleanup with collaborators.
5. Review logs and access for possible misuse.

Deleting the secret in a later commit does not remove it from earlier commits.

## Scenario 7: Your local branch is behind the remote

**Question:** What should you do before pushing?

**Answer:**

Fetch the latest changes, inspect the branch state, integrate the remote changes, and then push.

```bash
git fetch origin
git status
```

Choose the appropriate merge or rebase workflow before pushing.

## Scenario 8: You want to undo a pushed commit

**Question:** Which command is generally safer on a shared branch?

**Answer:**

Use `git revert` to create a new commit that reverses the earlier changes.

```bash
git revert COMMIT_HASH
git push
```

---

# Section 7: Practical Interview Tasks

Complete these tasks in a test repository.

### Task 1: Repository Setup

- Initialize a repository.
- Create a README.
- Stage and commit the file.
- Connect a GitHub remote.
- Push the main branch.

### Task 2: Branch Management

- Create a feature branch.
- Make a change.
- Commit and push it.
- Open a Pull Request.

### Task 3: Merge Conflict Resolution

- Create two branches.
- Change the same line differently.
- Merge the branches.
- Resolve the conflict.

### Task 4: Commit Recovery

- Inspect the commit history.
- Read the reflog.
- Create a recovery branch from a known commit.

### Task 5: Release Creation

- Create an annotated tag.
- Push the tag.
- Create a GitHub Release using that tag.

---

# Section 8: Quick Command Reference

| Command | Purpose |
|---|---|
| `git init` | Initialize a repository |
| `git clone URL` | Clone a repository |
| `git status` | Inspect the working tree |
| `git add .` | Stage eligible changes under the current directory |
| `git commit -m "Message"` | Commit staged changes |
| `git log --oneline` | View compact commit history |
| `git branch` | List local branches |
| `git switch -c branch-name` | Create and switch to a branch |
| `git merge branch-name` | Merge a branch into the current branch |
| `git rebase branch-name` | Rebase onto the specified base |
| `git fetch origin` | Fetch remote updates |
| `git pull` | Fetch and integrate remote updates |
| `git push` | Push commits to a remote |
| `git stash` | Temporarily save local changes |
| `git restore file.txt` | Discard unstaged changes in a tracked file |
| `git restore --staged file.txt` | Unstage a file |
| `git revert HASH` | Create a commit that reverses another commit |
| `git reflog` | Inspect recent local reference movements |
| `git remote -v` | Show remote URLs |
| `git tag` | List tags |

---

# Final Interview Preparation Checklist

- [ ] Understand Git's distributed version-control model.
- [ ] Explain the working directory, staging area, and repository.
- [ ] Know common Git commands and their purposes.
- [ ] Understand branching, merging, and rebasing.
- [ ] Explain Pull Requests, forks, and code reviews.
- [ ] Resolve a merge conflict in practice.
- [ ] Understand safe recovery and undo operations.
- [ ] Know how to avoid committing secrets.
- [ ] Practice pushing code to GitHub.
- [ ] Complete the practical tasks in a test repository.

## Final Learning Outcome

After completing this module, learners should be prepared to explain Git and GitHub concepts, demonstrate common commands, troubleshoot typical errors, and discuss collaboration workflows in technical interviews.

---

**Congratulations!** You have completed the planned 12-module Git & GitHub course structure.
