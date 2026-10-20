
# 07 - Advanced Git

## 📌 Overview

Advanced Git commands help developers manage changes, recover files, move commits, and maintain a clean project history.

In this module, you will learn:

- Git Stash
- Git Restore
- Git Revert
- Git Reset
- Git Cherry-Pick
- Git Rebase
- Git Tags
- Git Reflog

---

## 1. Git Stash

### What is Git Stash?

`git stash` temporarily saves changes in your working directory without requiring a commit.

It is useful when you need to switch branches but are not ready to commit your current work.

### Save changes

```bash
git stash
```

### Save with a message

```bash
git stash push -m "Work in progress"
```

### View saved stashes

```bash
git stash list
```

### Restore the latest stash and keep it saved

```bash
git stash apply
```

### Restore the latest stash and remove it from the stash list

```bash
git stash pop
```

### Delete a stash

```bash
git stash drop stash@{0}
```

### Example

You are working on a login page but suddenly need to fix a bug on another branch.

```bash
git stash push -m "Login page changes"
git switch main
```

After completing the bug fix, return to your branch and restore your work.

```bash
git switch feature-login
git stash pop
```

**Note:** Stashing is not a replacement for committing important work. Commit valuable changes regularly.

---

## 2. Git Restore

### What is Git Restore?

`git restore` restores file contents from a known state.

### Discard unstaged changes in a file

```bash
git restore filename.txt
```

This discards uncommitted changes to that file. Those changes may be difficult or impossible to recover.

### Unstage a file

```bash
git restore --staged filename.txt
```

This removes the file from the staging area but keeps its working-directory changes.

### Restore all unstaged tracked-file changes

```bash
git restore .
```

**Warning:** Review your changes before running restore commands.

---

## 3. Git Revert

### What is Git Revert?

`git revert` creates a new commit that reverses the changes introduced by an earlier commit.

It is generally a safe choice for undoing changes that have already been pushed to a shared branch.

### View commit history

```bash
git log --oneline
```

Example:

```text
a1b2c3d Add payment feature
d4e5f6a Add login feature
```

### Revert a commit

```bash
git revert a1b2c3d
```

Replace `a1b2c3d` with the actual commit hash you want to undo.

### Push the revert

```bash
git push
```

**Important:** Revert does not erase the original commit. It creates another commit that reverses its changes.

---

## 4. Git Reset

### What is Git Reset?

`git reset` moves the current branch pointer to another commit. Depending on the option used, it can also change the staging area and working directory.

### Soft reset

```bash
git reset --soft HEAD~1
```

Moves the current branch back one commit while keeping the changes staged.

### Mixed reset

```bash
git reset --mixed HEAD~1
```

Moves the current branch back one commit and unstages the changes while keeping them in the working directory.

This is the default reset mode.

```bash
git reset HEAD~1
```

### Hard reset

```bash
git reset --hard HEAD~1
```

Moves the branch back one commit and discards the affected tracked-file changes in the working directory and staging area.

**Danger:** `--hard` can permanently discard work. Use it only when you understand the consequences and have backed up anything important.

### Reset vs Revert

| Command | Purpose |
|---|---|
| `git reset` | Moves the branch pointer |
| `git revert` | Creates a commit that reverses another commit |
| `git reset --soft` | Keeps changes staged |
| `git reset --mixed` | Keeps changes but unstages them |
| `git reset --hard` | Discards affected tracked-file changes |

**Best practice:** Prefer `git revert` for undoing commits on shared branches. Avoid resetting commits that other collaborators may already have based work on.

---

## 5. Git Cherry-Pick

### What is Git Cherry-Pick?

`git cherry-pick` applies the changes from a specific commit to your current branch.

### Example scenario

You fixed a bug on `feature-login` and want that fix on `main` without merging the entire feature branch.

### Steps

First, view the commit history:

```bash
git log --oneline
```

Switch to the destination branch:

```bash
git switch main
```

Apply the required commit:

```bash
git cherry-pick COMMIT_HASH
```

Replace `COMMIT_HASH` with the actual commit hash.

If the operation succeeds, push the branch:

```bash
git push
```

### If a conflict occurs

1. Open the conflicted files.
2. Resolve the conflict markers.
3. Stage the resolved files.
4. Continue the cherry-pick.

```bash
git add .
git cherry-pick --continue
```

To cancel an in-progress cherry-pick:

```bash
git cherry-pick --abort
```

---

## 6. Git Rebase

### What is Git Rebase?

`git rebase` reapplies commits on top of another base commit. It can create a more linear project history.

### Example

Update your feature branch with the latest commits from `main`.

```bash
git switch feature-login
git fetch origin
git rebase origin/main
```

### If a conflict occurs

1. Open the conflicted files.
2. Resolve each conflict.
3. Stage the resolved files.
4. Continue the rebase.

```bash
git add .
git rebase --continue
```

To cancel an in-progress rebase:

```bash
git rebase --abort
```

### Rebase vs Merge

| Feature | Merge | Rebase |
|---|---|---|
| Main purpose | Combines branch histories | Replays commits on a new base |
| History | May create a merge commit | Usually creates a linear history |
| Existing commits | Preserves existing commit identities | Replayed commits get new hashes |
| Shared branches | Generally safe | Requires extra care |

**Important:** Avoid rebasing commits that other people are already using unless your team has agreed on the workflow. Rebase rewrites commit history.

---

## 7. Git Tags

### What are Git Tags?

Tags label specific commits, commonly to mark software releases.

### Create a lightweight tag

```bash
git tag v1.0.0
```

### Create an annotated tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0 release"
```

Annotated tags store additional metadata, including a message and tagger information.

### List tags

```bash
git tag
```

### View tag details

```bash
git show v1.0.0
```

### Push one tag to GitHub

```bash
git push origin v1.0.0
```

### Push all local tags

```bash
git push origin --tags
```

### Delete a local tag

```bash
git tag -d v1.0.0
```

### Delete a remote tag

```bash
git push origin --delete v1.0.0
```

**Best practice:** Use consistent version names, such as `v1.0.0`, `v1.1.0`, and `v2.0.0`.

---

## 8. Git Reflog

### What is Git Reflog?

`git reflog` records updates to local references, such as branch movements and recent commit positions.

It can help locate commits that seem lost after certain operations.

### View the reflog

```bash
git reflog
```

Example:

```text
a1b2c3d HEAD@{0}: commit: Add dashboard
d4e5f6a HEAD@{1}: reset: moving to HEAD~1
```

### Inspect an earlier state

```bash
git show HEAD@{1}
```

### Recover a commit safely

If you identify the commit you want to recover, create a recovery branch from its hash:

```bash
git branch recovery-branch COMMIT_HASH
```

Replace `COMMIT_HASH` with the actual hash from your reflog.

Then inspect the branch:

```bash
git switch recovery-branch
git log --oneline
```

**Note:** Reflog is local and entries expire over time. It is not a substitute for backups or pushing important commits to a remote repository.

---

## 9. Useful Advanced Git Commands

### Show the current branch

```bash
git branch --show-current
```

### Show the difference between working files and the last commit

```bash
git diff
```

### Show staged changes

```bash
git diff --staged
```

### Show a compact commit history

```bash
git log --oneline --graph --decorate --all
```

### Fetch updates without merging them

```bash
git fetch origin
```

### Show remote repository URLs

```bash
git remote -v
```

### Check repository status

```bash
git status
```

---

## 10. Practical Exercises

Complete these exercises in a test repository.

### Exercise 1: Stash

- Create a file named `notes.txt`.
- Add some text.
- Run `git stash push -m "Practice stash"`.
- Check the stash list.
- Restore the changes using `git stash pop`.

### Exercise 2: Restore

- Modify a tracked file.
- Run `git diff`.
- Discard the changes using `git restore filename.txt`.
- Confirm the result using `git status`.

### Exercise 3: Revert

- Create a new commit.
- Find its hash using `git log --oneline`.
- Revert the commit.
- Inspect the new commit in the history.

### Exercise 4: Tags

- Create an annotated tag named `v1.0.0`.
- Inspect it using `git show v1.0.0`.
- Push it to your GitHub repository.

### Exercise 5: Reflog

- View the recent reflog entries.
- Find a recent commit hash.
- Create a recovery branch from that hash.
- Inspect the recovered branch.

---

## 11. Knowledge Check

1. Which command temporarily saves uncommitted changes?
2. What is the difference between `git revert` and `git reset`?
3. Which command applies a single commit to another branch?
4. Why should you be careful when using `git rebase` on shared branches?
5. What is the purpose of Git tags?
6. Which command can help you locate a previous commit after a reset?
7. How do you unstage a file without deleting its changes?
8. How do you push a single tag to GitHub?

### Answers

1. `git stash`
2. Revert creates a new reversing commit; reset moves the branch pointer.
3. `git cherry-pick`
4. Rebase rewrites commit history and changes commit hashes.
5. Tags mark specific commits, often for releases.
6. `git reflog`
7. `git restore --staged filename.txt`
8. `git push origin TAG_NAME`

---

## Summary

In this module, you learned how to:

- Temporarily save changes with stash.
- Restore or unstage files.
- Undo commits using revert and reset.
- Apply selected commits with cherry-pick.
- Rebase branches.
- Create and push tags.
- Recover commit references using reflog.

**Next Module:** [08 - GitHub Features](../08-GitHub-Features/README.md)
