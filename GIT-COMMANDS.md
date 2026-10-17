
# Git Commands — Complete Reference Guide

A practical reference for essential Git commands, from basic version control to advanced workflows.

## 1. Installation and Version

### Check Git Version

```bash
git --version
```

Displays the installed Git version.

### Display Git Help

```bash
git help
git help commit
git commit -h
```

Displays general help, detailed documentation, or concise command options.

---

## 2. Git Configuration

### Set Global Username

```bash
git config --global user.name "Your Name"
```

Sets the author name used in commits by default.

### Set Global Email

```bash
git config --global user.email "you@example.com"
```

Sets the author email used in commits by default.

### View Configuration

```bash
git config --global --list
git config --list
```

Displays global configuration or the effective configuration, respectively.

### Set Configuration for One Repository

```bash
git config user.name "Project Author"
git config user.email "project@example.com"
```

Run these commands inside the repository to set repository-specific values.

### Remove a Global Configuration Value

```bash
git config --global --unset user.name
```

Removes the global username setting. Use this only when you intend to change or remove it.

**Important:** Git author configuration is not the same as GitHub authentication.

---

## 3. Repository Initialization

### Initialize a Repository

```bash
git init
```

Creates a Git repository in the current directory.

### Check Repository Status

```bash
git status
```

Shows the current branch, staged changes, unstaged changes, and untracked files.

### Find the Repository Root

```bash
git rev-parse --show-toplevel
```

Displays the root directory of the current repository.

### Clone an Existing Repository

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

Downloads a repository and its history into a new local directory.

---

## 4. Adding and Committing Changes

### Stage One File

```bash
git add README.md
```

Stages changes to the specified file.

### Stage All Changes in the Current Directory

```bash
git add .
```

Stages new files and changes under the current directory, subject to Git's ignore rules.

### Commit Staged Changes

```bash
git commit -m "Add course introduction"
```

Creates a commit from the staged changes.

### Stage Tracked Changes and Commit

```bash
git commit -am "Update documentation"
```

Stages modifications and deletions to tracked files and commits them. It does not automatically include new, untracked files.

### View Commit History

```bash
git log
git log --oneline
git log --oneline --graph --all
```

Displays the full history, a compact history, or a graph of visible branch histories.

---

## 5. Inspecting Changes

### View Unstaged Changes

```bash
git diff
```

Shows changes that have not been staged.

### View Staged Changes

```bash
git diff --staged
```

Shows the changes prepared for the next commit.

### Compare Two Commits

```bash
git diff COMMIT_A COMMIT_B
```

Compares the file contents between two commits.

### Show a Specific Commit

```bash
git show COMMIT_ID
```

Displays details and changes associated with a commit.

### List Tracked Files

```bash
git ls-files
```

Lists files currently tracked by Git.

---

## 6. Branch Management

### List Local Branches

```bash
git branch
```

Lists local branches and identifies the current branch.

### Create a Branch

```bash
git branch feature-login
```

Creates a branch without switching to it.

### Switch Branches

```bash
git switch feature-login
```

Switches to an existing branch.

### Create and Switch to a Branch

```bash
git switch -c feature-login
```

Creates a new branch and switches to it.

### Delete a Merged Branch

```bash
git branch -d feature-login
```

Deletes a local branch when Git considers it safe to delete.

### Merge a Branch

```bash
git switch main
git merge feature-login
```

Merges the specified branch into the current branch, which is `main` in this example.

**Note:** Save or otherwise protect important work before switching branches or merging.

---

## 7. Connecting to GitHub

### Add a Remote

```bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
```

Adds a remote repository named `origin`.

### List Remotes

```bash
git remote -v
```

Displays configured remote names and URLs.

### Change a Remote URL

```bash
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```

Updates the URL associated with `origin`.

### Remove a Remote

```bash
git remote remove origin
```

Removes the local remote configuration. It does not delete the GitHub repository.

### Push a Branch for the First Time

```bash
git push -u origin main
```

Pushes the local `main` branch and sets its upstream tracking branch.

### Push Later Changes

```bash
git push
```

Pushes commits to the configured upstream branch when one is available.

### Fetch Remote Changes

```bash
git fetch origin
```

Downloads remote references and objects without integrating them into the current branch.

### Pull Remote Changes

```bash
git pull
```

Fetches changes and integrates them into the current branch according to the configured pull strategy.

### List Remote Branches

```bash
git branch -r
```

Lists known remote-tracking branches.

---

## 8. Undoing and Restoring Changes

### Unstage a File

```bash
git restore --staged README.md
```

Removes the file from the staging area without discarding its working-directory edits.

### Discard Unstaged Changes to a File

```bash
git restore README.md
```

Restores the file from the index, discarding its unstaged edits.

**Warning:** This can permanently discard uncommitted work in that file.

### Create a New Commit That Reverses an Earlier Commit

```bash
git revert COMMIT_ID
```

Creates a new commit that reverses the changes introduced by the specified commit.

### Reset the Latest Commit but Keep Changes Staged

```bash
git reset --soft HEAD~1
```

Moves the current branch back one commit while keeping the changes staged.

### Reset the Latest Commit and Unstage Changes

```bash
git reset --mixed HEAD~1
```

Moves the branch back one commit and leaves the changes in the working directory unstaged.

### Hard Reset

```bash
git reset --hard HEAD~1
```

Moves the branch back one commit and resets tracked working-tree and index contents.

**Warning:** This can destroy uncommitted work and make commits harder to recover. Understand the consequences before using it.

---

## 9. Stashing Changes

### Save Work Temporarily

```bash
git stash push -m "Work in progress"
```

Stores tracked working-tree and staged changes in a stash.

### Include Untracked Files

```bash
git stash push -u -m "Save new files too"
```

Includes untracked files in the stash.

### List Stashes

```bash
git stash list
```

Lists saved stashes.

### Apply the Latest Stash

```bash
git stash apply
```

Restores the latest stash without removing it from the stash list.

### Apply and Remove the Latest Stash

```bash
git stash pop
```

Applies the latest stash and removes it from the list if application succeeds.

### Delete a Stash

```bash
git stash drop
```

Removes the latest stash entry.

---

## 10. Tags and Releases

### Create a Tag

```bash
git tag v1.0.0
```

Creates a lightweight tag at the current commit.

### Create an Annotated Tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
```

Creates a tag with metadata and a message.

### Push a Tag

```bash
git push origin v1.0.0
```

Pushes the specified tag to the remote.

### Push All Tags

```bash
git push origin --tags
```

Pushes local tags that are not already present on the remote.

---

## 11. Merge Conflict Commands

### Check Conflicted Files

```bash
git status
```

Identifies files that need conflict resolution.

### Resolve a Conflict

1. Open the conflicted file.
2. Inspect the conflicting sections.
3. Choose or combine the correct changes.
4. Remove conflict markers.
5. Save the file.

### Stage the Resolved File

```bash
git add filename
```

Marks the file as resolved after you have edited it.

### Complete a Merge

```bash
git commit
```

Creates the merge commit when required by the merge operation.

**Important:** If the merge was started incorrectly, use `git merge --abort` when appropriate to return to the pre-merge state.

---

## 12. Useful Maintenance Commands

### Remove Untracked Files Preview

```bash
git clean -n
```

Previews untracked files that a clean operation would remove.

### Remove Untracked Files

```bash
git clean -f
```

Deletes untracked files. This operation can permanently remove files.

### Check Ignored Files

```bash
git status --ignored
```

Displays ignored files as well as ordinary status information.

### Show Recent Reference Movements

```bash
git reflog
```

Displays recent movements of local references, useful for investigating some lost-commit situations.

---

## 13. Recommended Daily Workflow

```bash
git status
git add .
git diff --staged
git commit -m "Describe the changes"
git push
```

Use `git diff --staged` to review what you are about to commit.

If you are collaborating with others, fetch and integrate remote changes when appropriate before pushing.

---

## 14. Safety Rules

1. Check `git status` before changing repository state.
2. Write meaningful commit messages.
3. Review staged changes before committing.
4. Avoid `git reset --hard` unless you understand its consequences.
5. Do not force-push shared branches without coordination.
6. Never commit passwords, API keys, private keys, or access tokens.
7. Use `.gitignore` for generated files and local configuration.
8. Back up important work before risky history operations.
9. Remember that deleting a local remote configuration does not delete the hosted repository.
10. Practice unfamiliar commands in a test repository first.

---

## 15. Practice Tasks

1. Initialize a repository.
2. Create a README file.
3. Stage and commit the file.
4. Make another change and inspect it with `git diff`.
5. Create a feature branch.
6. Make a commit on that branch.
7. Merge the branch into `main`.
8. Connect the repository to GitHub.
9. Push the repository.
10. Clone it into another directory.

---

**Learning tip:** Understanding when and why to use a command is more important than memorizing its syntax.
