
# Module 05: Branching and Merging in Git

## 1. Learning Objectives

After completing this module, you will be able to:

- Understand Git branches and why they are useful.
- List and create branches.
- Switch between branches.
- Rename and delete branches.
- Merge changes from one branch into another.
- Understand fast-forward and three-way merges.
- Identify and resolve merge conflicts.
- Follow a feature-branch workflow.

---

## 2. What Is a Branch in Git?

A branch is a movable reference to a commit in Git.

Branches allow developers to work on different features, bug fixes, or experiments without immediately changing the main development branch.

### Example

Imagine you are developing a student management system.

Your project contains:

- Login page
- Student dashboard
- Attendance module
- Report generation

Different developers can work on different features using separate branches.

Example branch names:

- `main`
- `feature-login`
- `feature-attendance`
- `feature-reports`
- `bugfix-login-error`

After development and review, the changes can be merged into the appropriate target branch.

---

## 3. What Is the Main Branch?

The main branch is commonly used as the primary branch of a repository.

It is often named `main`, although older repositories may use `master` or another name.

The main branch commonly contains the primary version of the project.

Teams may protect this branch and require pull requests or code reviews before changes can be merged.

---

## 4. Why Are Branches Important?

Branches help developers:

1. Develop features independently.
2. Fix bugs without disrupting unrelated work.
3. Experiment safely.
4. Review code before integration.
5. Collaborate with team members.
6. Organize changes into meaningful units.

### Real-World Example

A team is building an e-commerce website.

- Developer A works on the login feature.
- Developer B works on the shopping cart.
- Developer C fixes a payment-page bug.

Each developer can work on a separate branch. Their changes are integrated after appropriate testing and review.

---

## 5. List Branches

### List Local Branches

```bash
git branch
```

Displays local branches and marks the current branch with an asterisk.

### List Remote-Tracking Branches

```bash
git branch -r
```

Displays remote-tracking branches known to your local repository.

### List All Known Branches

```bash
git branch -a
```

Displays local and remote-tracking branches.

---

## 6. Create a Branch

### Syntax

```bash
git branch branch-name
```

### Example

```bash
git branch feature-login
```

This creates a branch named `feature-login`.

**Important:** Creating a branch does not automatically switch to it.

Verify the branch list:

```bash
git branch
```

---

## 7. Switch Between Branches

### Using `git switch`

```bash
git switch feature-login
```

This switches to an existing branch.

### Create and Switch in One Command

```bash
git switch -c feature-dashboard
```

This creates the branch and switches to it.

### Older Alternative: `git checkout`

```bash
git checkout feature-login
```

You can also create and switch branches with:

```bash
git checkout -b feature-dashboard
```

For everyday branch switching, `git switch` is generally clearer because it separates branch operations from other checkout operations.

---

## 8. Rename a Branch

### Rename the Current Branch

```bash
git branch -m new-branch-name
```

### Rename Another Local Branch

```bash
git branch -m old-branch-name new-branch-name
```

Renaming a local branch does not automatically rename the corresponding branch on GitHub.

---

## 9. Delete a Branch

### Delete a Merged Branch

```bash
git branch -d feature-login
```

Git normally refuses this deletion if the branch contains changes it considers unmerged.

### Force-Delete a Local Branch

```bash
git branch -D feature-login
```

**Warning:** This can remove a branch reference containing commits that have not been merged. Make sure important work is preserved before using it.

### Delete a Remote Branch

```bash
git push origin --delete feature-login
```

This requests deletion of the branch from the remote repository. Make sure the branch is no longer needed by your team.

---

## 10. What Is Merging?

Merging integrates changes from one branch into another.

The branch you currently have checked out is normally the target branch.

### Example

You have two branches:

- `main`
- `feature-login`

After completing and testing the login feature, you want to integrate it into `main`.

Run:

```bash
git switch main
git merge feature-login
```

The changes from `feature-login` are merged into `main`.

**Remember:** The branch you switch to first is the branch that receives the merge.

---

## 11. Understanding Fast-Forward Merge

A fast-forward merge is possible when the target branch has not advanced beyond the source branch's common history.

Git can move the target branch reference forward without creating a merge commit.

### Example

```bash
git switch main
git merge feature-login
```

If `main` has not diverged from `feature-login`, Git may perform a fast-forward merge.

A fast-forward merge does not create a separate merge commit.

---

## 12. Understanding Three-Way Merge

A three-way merge is commonly used when the source and target branches have diverged.

Git uses:

- The common ancestor commit.
- The latest target-branch commit.
- The latest source-branch commit.

Git combines the changes when possible.

A merge commit may be created to record the integration.

### Example

```bash
git switch main
git merge feature-login
```

If the branches have diverged, Git may create a merge commit.

If changes conflict, you must resolve the conflicts before completing the merge.

---

## 13. What Is a Merge Conflict?

A merge conflict occurs when Git cannot automatically reconcile overlapping changes.

For example, two developers modify the same lines of a file in different ways.

Git pauses the merge and asks you to resolve the conflict.

A conflict is a normal part of collaborative development. It does not necessarily mean the repository is damaged.

---

## 14. Practical Merge Conflict Example

### Step 1: Create a Test Repository

```bash
mkdir git-branch-practice
cd git-branch-practice
git init -b main
```

Create a file named `message.txt` containing:

```text
Welcome to Git
```

Stage and commit it:

```bash
git add message.txt
git commit -m "Add initial message"
```

### Step 2: Create a Feature Branch

```bash
git switch -c feature-message
```

Edit `message.txt` to contain:

```text
Welcome to Git - Feature Version
```

Commit the change:

```bash
git add message.txt
git commit -m "Update message in feature branch"
```

### Step 3: Return to Main

```bash
git switch main
```

Edit `message.txt` to contain:

```text
Welcome to Git - Main Version
```

Commit the change:

```bash
git add message.txt
git commit -m "Update message in main branch"
```

### Step 4: Merge the Feature Branch

```bash
git merge feature-message
```

Because both branches changed the same line differently, Git will typically report a merge conflict.

### Step 5: Inspect the Conflict

Open `message.txt`.

Git may show content similar to:

```text
<<<<<<< HEAD
Welcome to Git - Main Version
=======
Welcome to Git - Feature Version
>>>>>>> feature-message
```

Meaning:

- `<<<<<<< HEAD` begins the current branch's version.
- `=======` separates the two versions.
- `>>>>>>> feature-message` ends the incoming branch's version.

The exact labels can vary depending on the merge.

### Step 6: Resolve the Conflict

Choose the correct content or combine both versions.

For example:

```text
Welcome to Git
Main and feature changes have been reviewed.
```

Remove all conflict markers and save the file.

### Step 7: Stage the Resolved File

```bash
git add message.txt
```

### Step 8: Complete the Merge

```bash
git commit -m "Resolve message merge conflict"
```

### Step 9: Verify the Result

```bash
git status
git log --oneline --graph --all
```

The merge should now be complete.

---

## 15. Abort a Merge

If a merge is in progress and you decide not to continue, you can often return to the pre-merge state with:

```bash
git merge --abort
```

Use this while the merge is still in progress.

If you have already completed the merge commit, `git merge --abort` will not undo it. A later recovery operation depends on your current repository state.

Protect important uncommitted changes before attempting recovery.

---

## 16. Push a New Branch to GitHub

A new local branch is not automatically published to GitHub.

To publish it:

```bash
git push -u origin feature-login
```

The `-u` option configures upstream tracking for later pushes and pulls.

After the upstream is configured, you can normally use:

```bash
git push
```

to publish further commits on that branch.

---

## 17. Feature-Branch Workflow

A common workflow looks like this:

### Step 1: Update Main

```bash
git switch main
git pull
```

This assumes `main` tracks the appropriate remote branch and the working tree is ready for the update.

### Step 2: Create a Feature Branch

```bash
git switch -c feature-student-dashboard
```

### Step 3: Make Changes

Create or edit the required files.

### Step 4: Review Changes

```bash
git status
git diff
```

### Step 5: Stage and Commit

```bash
git add .
git diff --staged
git commit -m "Add student dashboard"
```

### Step 6: Push the Branch

```bash
git push -u origin feature-student-dashboard
```

### Step 7: Create a Pull Request

Open GitHub and create a pull request to propose merging the feature branch into the target branch.

Review, test, and merge the pull request according to your team's process.

### Step 8: Clean Up

After the changes are merged, switch back to the target branch and update it as appropriate.

Delete the feature branch only when it is no longer needed.

---

## 18. Common Branching Mistakes

### Mistake 1: Merging Into the Wrong Branch

**Solution:** Run `git branch --show-current` before merging.

### Mistake 2: Forgetting to Push a New Branch

**Solution:** Use `git push -u origin branch-name`.

### Mistake 3: Deleting Unmerged Work

**Solution:** Inspect the branch history and preserve important commits before deleting a branch.

### Mistake 4: Ignoring Merge Conflicts

**Solution:** Resolve each conflicted file, stage the resolution, and complete or abort the merge appropriately.

### Mistake 5: Working Directly on Main by Accident

**Solution:** Check the current branch before making changes and create a feature branch when appropriate.

---

## 19. Practical Assignments

### Assignment 1: Branch Creation

1. Initialize a repository.
2. Create a README file.
3. Commit it.
4. Create a branch named `feature-about`.
5. Switch to the new branch.
6. Make a change and commit it.

### Assignment 2: Branch Merging

1. Create a feature branch.
2. Add a new file.
3. Commit the file.
4. Switch to `main`.
5. Merge the feature branch.
6. Inspect the history using `git log --oneline --graph --all`.

### Assignment 3: Conflict Resolution

1. Create two branches.
2. Edit the same line differently in both branches.
3. Commit each change.
4. Merge the branches.
5. Resolve the conflict.
6. Verify that no conflict markers remain.

### Assignment 4: GitHub Branch Workflow

1. Create a feature branch.
2. Make and commit a change.
3. Push the branch to GitHub.
4. Open a pull request.
5. Review the proposed changes.

---

## 20. Knowledge Check

### Question 1

Which command creates a new branch and switches to it?

A. `git merge feature`

B. `git switch -c feature`

C. `git push feature`

D. `git status feature`

### Question 2

Which branch receives changes during a normal merge?

A. The branch you currently have checked out.

B. Always the oldest branch.

C. Always the remote branch.

D. Every branch automatically.

### Question 3

What is a merge conflict?

A. A Git installation failure.

B. A situation where Git cannot automatically reconcile changes.

C. A GitHub login error.

D. A deleted repository.

### Question 4

Which command lists local branches?

A. `git remote -v`

B. `git branch`

C. `git log`

D. `git diff`

### Question 5

Which command pushes a new local branch and configures upstream tracking?

A. `git merge origin`

B. `git init -u`

C. `git push -u origin branch-name`

D. `git status -u`

### Answers

1. B — `git switch -c feature`
2. A — The current branch.
3. B — Git cannot automatically reconcile the changes.
4. B — `git branch`
5. C — `git push -u origin branch-name`

---

## 21. Module Summary

In this module, you learned:

- What branches are and why they matter.
- How to create, switch, rename, and delete branches.
- How merging integrates changes.
- The difference between fast-forward and three-way merges.
- How to resolve merge conflicts.
- How to publish a branch to GitHub.
- How feature branches support collaboration.

**Next Module:** Collaboration — cloning, forking, pull requests, code reviews, and contributing to other developers' repositories.
