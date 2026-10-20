
# 09 - Git Troubleshooting

## 📌 Overview

Git errors are common when working with branches, remote repositories, commits, and GitHub authentication. Understanding these errors helps developers solve problems quickly and safely.

In this module, you will learn how to fix:

- Git is not recognized
- `fatal: not a git repository`
- Rejected Git pushes
- Merge conflicts
- Authentication errors
- Remote origin errors
- Uncommitted changes blocking branch switching
- Detached HEAD
- Accidentally deleted or lost commits
- Large file push failures

---

## 1. Git Is Not Recognized

### Error

```text
'git' is not recognized as an internal or external command
```

### Cause

Git may not be installed, or its executable directory may not be included in the Windows PATH.

### Solution

Check whether Git is available:

```bat
git --version
```

If Git is installed but not recognized:

1. Install Git for Windows if necessary.
2. Ensure Git is included in the system PATH.
3. Restart VS Code and the terminal.
4. Run the version command again.

Official download: https://git-scm.com/downloads

---

## 2. Fatal: Not a Git Repository

### Error

```text
fatal: not a git repository (or any of the parent directories): .git
```

### Cause

The terminal is outside the Git repository, or the current folder has not been initialized as a repository.

### Solution A: Open the correct folder

```bat
cd "C:\Users\Vimal\Git-GitHub-Master-Course"
git status
```

### Solution B: Initialize a new repository

Use this only if the current project is not already a Git repository.

```bat
git init
```

Then check:

```bat
git status
```

**Note:** Do not run `git init` repeatedly in random folders. First confirm that you are inside the intended project directory.

---

## 3. Git Push Rejected

### Error

```text
! [rejected] main -> main (fetch first)
error: failed to push some refs
```

### Cause

The remote repository contains commits that your local branch does not have.

### Solution

First, check your status:

```bat
git status
```

Commit any intended local changes, then fetch the remote history:

```bat
git fetch origin
```

If your branch is `main`, integrate the remote changes:

```bat
git pull --rebase origin main
```

If Git reports conflicts, resolve them before continuing.

Then push:

```bat
git push origin main
```

**Important:** Avoid force-pushing to shared branches unless you fully understand the impact and have permission to rewrite remote history.

---

## 4. Merge Conflicts

### What is a merge conflict?

A conflict occurs when Git cannot automatically combine changes from different branches.

### Example

```text
<<<<<<< HEAD
Welcome to Git
=======
Welcome to GitHub
>>>>>>> feature-docs
```

### How to fix it

1. Open the conflicted file in VS Code.
2. Choose the correct content or combine both versions.
3. Remove the conflict markers.
4. Save the file.
5. Stage the resolved file.

```bat
git add README.md
```

If you were merging:

```bat
git commit
```

If you were rebasing:

```bat
git rebase --continue
```

Use the command appropriate to the operation in progress.

### Cancel an operation

Cancel an unfinished merge:

```bat
git merge --abort
```

Cancel an unfinished rebase:

```bat
git rebase --abort
```

---

## 5. Authentication Failed

### Error

```text
remote: Invalid username or password
fatal: Authentication failed
```

### Cause

GitHub no longer accepts ordinary account passwords for Git over HTTPS. Authentication may require a browser-based sign-in, a supported credential manager, or a personal access token.

### Solution

1. Check the repository URL:

```bat
git remote -v
```

2. If you use HTTPS, authenticate using the sign-in prompt or credential manager.
3. If a token is required, use a properly scoped personal access token and keep it secret.
4. Never paste tokens into source code or commit them to GitHub.

Official documentation:

https://docs.github.com/en/authentication

### Alternative: SSH

Configure an SSH key with GitHub and use an SSH remote URL if that suits your workflow.

---

## 6. Remote Origin Already Exists

### Error

```text
error: remote origin already exists.
```

### Cause

A remote named `origin` is already configured.

### Solution

Check the current remote:

```bat
git remote -v
```

If it points to the correct repository, no change is needed.

If the URL is incorrect, update it:

```bat
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```

Replace the placeholders with your actual GitHub username and repository name.

Verify:

```bat
git remote -v
```

---

## 7. Nothing to Commit

### Message

```text
nothing to commit, working tree clean
```

### Meaning

Git has no detected changes to commit.

### Check your status

```bat
git status
```

If you expected changes:

- Save your files in VS Code.
- Check whether the files are inside the repository.
- Check whether the changes were already committed.
- Check whether `.gitignore` excludes the files.

Do not repeatedly run `git commit` when there are no changes to commit.

---

## 8. Uncommitted Changes Prevent Branch Switching

### Error

```text
error: Your local changes would be overwritten by checkout
```

### Cause

Switching branches would overwrite changes in your working directory.

### Option A: Commit the changes

```bat
git add .
git commit -m "Save current work"
```

### Option B: Temporarily stash the changes

```bat
git stash push -m "Temporary work"
```

Switch branches:

```bat
git switch main
```

Restore your changes when appropriate:

```bat
git stash pop
```

### Option C: Keep editing

If you do not want to commit or stash, finish your current work before switching.

---

## 9. Detached HEAD

### What does it mean?

A detached HEAD means Git is checked out at a specific commit rather than at a local branch.

You can inspect the code, but commits made in this state are not automatically attached to a normal branch.

### Check the current state

```bat
git status
```

### Return to an existing branch

```bat
git switch main
```

### Preserve commits made in detached HEAD

If you have commits you want to keep, create a branch at the current commit before switching:

```bat
git switch -c recovery-branch
```

This creates a branch that points to your current commit.

---

## 10. Accidentally Deleted or Lost a Commit

### Cause

A reset, branch deletion, or other operation may make a commit difficult to find.

### Step 1: Inspect the reflog

```bat
git reflog
```

### Step 2: Find the required commit hash

Review the entries and identify the commit you want to recover.

### Step 3: Create a recovery branch

```bat
git branch recovery-branch COMMIT_HASH
```

Replace `COMMIT_HASH` with the actual commit hash.

### Step 4: Inspect the recovery branch

```bat
git switch recovery-branch
git log --oneline
```

**Important:** Reflog entries are local and can expire. Push or back up important work.

---

## 11. Large File Push Failed

### Possible error

```text
remote: error: File exceeds the maximum allowed size
```

### Cause

GitHub enforces file-size limits for ordinary Git repository files. Large files may need a different storage approach.

### Solution

1. Identify the large file.
2. Determine whether it belongs in the repository.
3. If it is a generated file, cache, or build artifact, consider excluding it with `.gitignore`.
4. If the file is required and appropriate for Git LFS, configure Git Large File Storage.
5. If the file should not be committed, remove it from the relevant commit history when necessary.

Example `.gitignore` entries:

```gitignore
node_modules/
.venv/
__pycache__/
dist/
build/
.env
```

Only ignore files that should not be tracked. If a file is already tracked, adding it to `.gitignore` does not automatically remove it from Git history.

Official documentation:

https://docs.github.com/en/repositories/working-with-files/managing-large-files

---

## 12. Git Push Fails With HTTP 408

### Error

```text
RPC failed; HTTP 408
fatal: the remote end hung up unexpectedly
```

### Possible causes

- Unstable internet connection.
- A large push.
- A network proxy or timeout.
- Large files in the repository.

### Troubleshooting steps

Check the repository status:

```bat
git status
```

Check the latest commits:

```bat
git log --oneline -5
```

Check for large files and confirm that generated files or dependencies are not accidentally included.

Try pushing again when the connection is stable:

```bat
git push
```

If the problem continues, inspect the error details and identify the large files or network issue rather than changing Git configuration blindly.

---

## 13. File Is Missing From GitHub

### Possible causes

- The file was not saved.
- The file was not staged.
- The file was ignored.
- The commit was not pushed.
- The file is in another folder.

### Solution

Check the repository status:

```bat
git status
```

Stage the intended file:

```bat
git add README.md
```

Commit it:

```bat
git commit -m "Add README documentation"
```

Push the current branch:

```bat
git push
```

For a file in a subfolder, use its relative path, such as:

```bat
git add "09-Git-Troubleshooting/README.md"
```

---

## 14. Useful Diagnostic Commands

Use these commands before attempting risky fixes.

| Command | Purpose |
|---|---|
| `git status` | Check working directory and staging state |
| `git log --oneline -5` | View recent commits |
| `git branch` | List local branches |
| `git branch -a` | List local and remote-tracking branches |
| `git remote -v` | Check configured remotes |
| `git diff` | Inspect unstaged changes |
| `git diff --staged` | Inspect staged changes |
| `git reflog` | Inspect recent local reference movements |
| `git fetch origin` | Download remote updates without integrating them |

---

## 15. Safe Troubleshooting Workflow

When an error appears, follow this sequence:

```text
Git Error
    |
    v
Read the Full Error Message
    |
    v
Run git status
    |
    v
Check Branch and Remote
    |
    v
Identify the Root Cause
    |
    v
Back Up Important Changes
    |
    v
Apply the Appropriate Fix
    |
    v
Verify With git status
    |
    v
Commit and Push When Ready
```

### Golden rules

- Read the full error before acting.
- Do not delete `.git` to fix ordinary Git problems.
- Avoid `git reset --hard` unless you understand what will be discarded.
- Avoid force-pushing to shared branches without authorization.
- Never commit passwords, tokens, or private keys.
- Back up important work before history-rewriting operations.

---

## 16. Practical Exercises

### Exercise 1: Remote configuration

Run:

```bat
git remote -v
```

Identify the fetch and push URLs.

### Exercise 2: Working tree inspection

Modify a Markdown file and run:

```bat
git status
git diff
```

Observe the difference between the working directory and the latest commit.

### Exercise 3: Staging and committing

```bat
git add .
git diff --staged
git commit -m "Practice Git troubleshooting"
```

### Exercise 4: Recover a commit reference

```bat
git reflog
```

Find a recent commit and create a recovery branch from its hash.

### Exercise 5: Resolve a conflict

In a test repository, modify the same line on two branches, then merge them and resolve the resulting conflict.

---

## 17. Knowledge Check

1. What does `fatal: not a git repository` mean?
2. Why might GitHub reject a push?
3. How do you inspect a configured remote?
4. What is a merge conflict?
5. How can you temporarily save uncommitted changes?
6. What is detached HEAD?
7. Which command helps locate previous local commit references?
8. Why should you avoid force-pushing to shared branches?
9. Does `.gitignore` automatically untrack an already tracked file?
10. What should you do before using a destructive Git command?

### Answers

1. The current directory is not inside a recognized Git repository.
2. The remote may contain commits that are missing locally, or another push restriction may apply.
3. `git remote -v`
4. Git cannot automatically combine conflicting changes.
5. `git stash`
6. HEAD points directly to a commit rather than a local branch.
7. `git reflog`
8. It may overwrite remote history that collaborators rely on.
9. No.
10. Inspect the state and back up important changes.

---

## Summary

In this module, you learned how to diagnose and fix:

- Git installation and repository errors.
- Rejected pushes.
- Merge conflicts.
- Authentication and remote errors.
- Uncommitted changes.
- Detached HEAD.
- Lost commits.
- Large-file and HTTP push failures.

**Next Module:** [10 - Hands-On Projects](../10-Hands-On-Projects/README.md)
