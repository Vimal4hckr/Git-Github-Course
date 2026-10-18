
# Module 03: Basic Git Commands

## 1. Learning Objectives

After completing this module, you will be able to:

- Initialize a Git repository.
- Check the status of files.
- Stage changes for a commit.
- Create commits with meaningful messages.
- Inspect commit history.
- Compare file changes.
- Understand the working directory, staging area, and repository.
- Complete a basic Git workflow independently.

---

## 2. Understanding the Git Workflow

Git tracks changes through three main areas.

### 2.1 Working Directory

The working directory contains your project files. You create, edit, and delete files here.

### 2.2 Staging Area

The staging area contains changes selected for the next commit.

The `git add` command stages changes.

### 2.3 Repository

The repository stores committed snapshots and their history.

The `git commit` command records the staged changes.

### Basic Workflow

Working Directory → Staging Area → Local Repository

Commands:

- `git add` — stages changes.
- `git commit` — records staged changes.

---

## 3. The `git init` Command

### Definition

The `git init` command initializes a new Git repository in the current directory.

### Syntax

```bash
git init
```

### Example

Create a new project directory and enter it:

```bash
mkdir git-practice
cd git-practice
git init
```

Git creates the repository metadata required to track the project.

### Initialize with a Specific Branch Name

```bash
git init -b main
```

This initializes a repository with `main` as its initial branch.

### Important Notes

- `git init` does not upload files to GitHub.
- It does not automatically commit your files.
- You can use it to start tracking an existing project.
- Avoid initializing a new repository inside another repository unless you intentionally want a nested repository.

---

## 4. The `git status` Command

### Definition

The `git status` command displays the current state of your repository.

### Syntax

```bash
git status
```

### It Helps You Identify

- The current branch.
- Changes that are not staged.
- Changes that are staged.
- Untracked files.
- Whether the working tree is clean.

### Example

```bash
git status
```

If you create a new file, Git may report it under untracked files.

After staging the file, Git reports it under changes to be committed.

### Why Is It Important?

Check `git status` frequently, especially before staging, committing, switching branches, or pushing.

---

## 5. The `git add` Command

### Definition

The `git add` command stages changes so they can be included in the next commit.

### Stage One File

```bash
git add README.md
```

### Stage Multiple Files

```bash
git add README.md ROADMAP.md
```

### Stage All Changes in the Current Directory

```bash
git add .
```

This stages new files and changes under the current directory, subject to ignore rules.

### Stage All Changes Across the Working Tree

```bash
git add -A
```

This stages additions, modifications, and deletions throughout the working tree.

### Important Notes

- `git add` does not create a commit.
- `git add` does not upload files to GitHub.
- Review the staged changes before committing.
- If you edit a file again after staging it, you may need to stage it again to include the latest changes.

---

## 6. The `git commit` Command

### Definition

A commit records a snapshot of staged changes in the repository history.

### Syntax

```bash
git commit -m "Commit message"
```

### Example

```bash
git commit -m "Add Git command examples"
```

### What Makes a Good Commit Message?

A good commit message explains the change clearly.

Examples:

```text
Add introduction to Git
Explain repository initialization
Fix installation instructions
Add branching exercises
Update Git command reference
```

Avoid unclear messages such as:

```text
update
changes
final
test
```

### Important Notes

- A commit normally includes staged changes.
- A commit is created locally.
- A commit does not automatically upload anything to GitHub.
- Use `git push` to send commits to a remote repository.

---

## 7. The `git log` Command

### Definition

The `git log` command displays commit history.

### Display Full History

```bash
git log
```

### Display Compact History

```bash
git log --oneline
```

### Display a Graph of Branch History

```bash
git log --oneline --graph --all
```

### What Information Does Git Log Show?

- Commit identifier.
- Author information.
- Date.
- Commit message.

### Why Is It Useful?

It helps developers understand previous changes, identify commits, and investigate project history.

---

## 8. The `git diff` Command

### Definition

The `git diff` command compares file contents and helps you understand changes.

### View Unstaged Changes

```bash
git diff
```

Shows changes in tracked files that have not been staged.

### View Staged Changes

```bash
git diff --staged
```

Shows the changes prepared for the next commit.

### Compare Two Commits

```bash
git diff COMMIT_A COMMIT_B
```

Replace the placeholders with actual commit identifiers.

### Understand the Output

Lines beginning with `-` indicate removed content.

Lines beginning with `+` indicate added content.

Reviewing a diff helps you catch accidental edits before committing.

---

## 9. Practical Example: First Git Repository

Follow these steps in a practice directory.

### Step 1: Create a Directory

```bash
mkdir git-first-project
cd git-first-project
```

### Step 2: Initialize Git

```bash
git init -b main
```

### Step 3: Create a File

Create a file named `README.md` containing:

```markdown
# My First Git Project

I am learning Git and GitHub.
```

### Step 4: Check Status

```bash
git status
```

You should see the new file listed as untracked.

### Step 5: Stage the File

```bash
git add README.md
```

### Step 6: Review Staged Changes

```bash
git diff --staged
```

### Step 7: Commit the File

```bash
git commit -m "Add initial project README"
```

### Step 8: Check Status Again

```bash
git status
```

If there are no remaining changes, Git should report that the working tree is clean.

### Step 9: View Commit History

```bash
git log --oneline
```

You should see your new commit.

---

## 10. Making a Second Commit

### Step 1: Edit the README

Add this line:

```text
This project helps me understand version control.
```

### Step 2: Check Changes

```bash
git status
git diff
```

### Step 3: Stage the Change

```bash
git add README.md
```

### Step 4: Review the Staged Change

```bash
git diff --staged
```

### Step 5: Commit

```bash
git commit -m "Expand project introduction"
```

### Step 6: Review History

```bash
git log --oneline
```

You should now see two commits.

---

## 11. Common Beginner Mistakes

### Mistake 1: Forgetting to Stage Files

**Problem:** You run `git commit`, but your new changes are not included.

**Solution:**

```bash
git status
git add filename
git commit -m "Describe the change"
```

### Mistake 2: Expecting `git add` to Upload Files

**Problem:** You stage files but cannot see them on GitHub.

**Solution:** Commit the changes and push the relevant commits to the remote repository.

### Mistake 3: Committing the Wrong Changes

**Problem:** Unwanted content is included in the next commit.

**Solution:** Review:

```bash
git status
git diff --staged
```

before committing.

### Mistake 4: Running `git log` Before the First Commit

**Problem:** Git reports that the current branch has no commits.

**Solution:** Create the first commit before expecting normal commit history.

### Mistake 5: Assuming Git Tracks Every File Automatically

**Problem:** New files are not included in commits.

**Solution:** Stage the required files with `git add`. Also check whether ignore rules exclude them.

---

## 12. Practical Assignments

### Assignment 1: Repository Creation

1. Create a directory called `student-profile`.
2. Initialize a Git repository.
3. Create a `README.md` file.
4. Stage the file.
5. Commit it.
6. Verify the commit using `git log --oneline`.

### Assignment 2: Multiple Commits

1. Create a file called `skills.md`.
2. Add three programming skills.
3. Stage and commit the file.
4. Add two more skills.
5. Create another commit.
6. Compare the commit history.

### Assignment 3: Change Inspection

1. Create a text file.
2. Commit it.
3. Modify the file.
4. Run `git diff`.
5. Stage the change.
6. Run `git diff --staged`.
7. Commit the change.

### Assignment 4: Repository Investigation

Answer the following:

1. What is the difference between `git add` and `git commit`?
2. What does `git status` display?
3. Why should you review `git diff --staged`?
4. What is a clean working tree?
5. Does a commit automatically upload code to GitHub?

---

## 13. Knowledge Check

### Question 1

Which command initializes a Git repository?

A. `git start`

B. `git init`

C. `git create`

D. `git new`

### Question 2

Which command stages a file?

A. `git push`

B. `git log`

C. `git add`

D. `git commit`

### Question 3

Which command creates a commit?

A. `git commit`

B. `git status`

C. `git branch`

D. `git diff`

### Question 4

Which command displays a compact commit history?

A. `git status`

B. `git log --oneline`

C. `git init`

D. `git add`

### Question 5

Which command displays staged changes?

A. `git diff`

B. `git diff --staged`

C. `git status --branch`

D. `git init`

### Answers

1. B — `git init`
2. C — `git add`
3. A — `git commit`
4. B — `git log --oneline`
5. B — `git diff --staged`

---

## 14. Module Summary

In this module, you learned:

- How to initialize a repository.
- How to check repository status.
- How to stage files.
- How to create commits.
- How to inspect commit history.
- How to compare changes.
- How to complete a basic Git workflow.
- How to identify common beginner mistakes.

**Next Module:** GitHub and Remote Repositories — creating a GitHub repository, connecting local Git to GitHub, and using `git push`, `git pull`, `git fetch`, and `git clone`.
