
# 11 - Git & GitHub MCQs

## 📌 Overview

This module contains 50 multiple-choice questions covering Git fundamentals, Git commands, branching, merging, GitHub collaboration, troubleshooting, and advanced Git concepts.

**Total Questions:** 50  
**Options per Question:** 4  
**Correct Answers:** 1 per question

---

# Section 1: Git Fundamentals

### 1. What is Git?

A. A programming language  
B. A distributed version control system  
C. A database management system  
D. A web browser  

**Answer:** B — Git is a distributed version control system used to track changes in files.

### 2. Who created Git?

A. Bill Gates  
B. James Gosling  
C. Linus Torvalds  
D. Brendan Eich  

**Answer:** C — Linus Torvalds created Git in 2005.

### 3. What is the primary purpose of Git?

A. To design websites  
B. To track changes in source code  
C. To create databases  
D. To edit images  

**Answer:** B — Git records changes and helps developers manage project history.

### 4. Which command checks the installed Git version?

A. `git check`  
B. `git versioning`  
C. `git --version`  
D. `git install`  

**Answer:** C — `git --version` displays the installed Git version.

### 5. Which command initializes a new Git repository?

A. `git start`  
B. `git init`  
C. `git create`  
D. `git new`  

**Answer:** B — `git init` initializes a Git repository in the current directory.

### 6. What is a repository?

A. A collection of project files and their version history  
B. A programming framework  
C. A web browser  
D. An operating system  

**Answer:** A — A repository stores project files and version-control information.

### 7. Which command displays the current working-tree status?

A. `git history`  
B. `git status`  
C. `git show-all`  
D. `git check-status`  

**Answer:** B — `git status` shows changed, staged, and untracked files.

### 8. Which command displays commit history?

A. `git log`  
B. `git history-all`  
C. `git commits`  
D. `git track`  

**Answer:** A — `git log` displays the repository's commit history.

### 9. What does a commit represent?

A. A saved snapshot of tracked project changes  
B. A new Git installation  
C. A deleted repository  
D. A GitHub account  

**Answer:** A — A commit records a snapshot and metadata in the repository history.

### 10. Which command configures your Git username?

A. `git user set`  
B. `git config --global user.name "Your Name"`  
C. `git username`  
D. `git profile add`  

**Answer:** B — This command sets the global author name used for new commits.

---

# Section 2: Basic Git Commands

### 11. Which command stages a specific file?

A. `git commit file.txt`  
B. `git add file.txt`  
C. `git push file.txt`  
D. `git save file.txt`  

**Answer:** B — `git add` stages changes for the next commit.

### 12. Which command commits staged changes?

A. `git save`  
B. `git upload`  
C. `git commit -m "Message"`  
D. `git stage`  

**Answer:** C — `git commit -m` creates a commit with a message.

### 13. What does `git add .` generally do?

A. Deletes all files  
B. Stages changes under the current directory, subject to Git's tracking and ignore rules  
C. Pushes files to GitHub  
D. Creates a branch  

**Answer:** B — It stages eligible changes within the current directory and its subdirectories.

### 14. Which command shows unstaged changes to tracked files?

A. `git diff`  
B. `git status --push`  
C. `git branch`  
D. `git init`  

**Answer:** A — `git diff` shows changes between the working tree and the index for tracked files.

### 15. What does `git clone` do?

A. Deletes a repository  
B. Copies a repository to a local environment  
C. Creates a commit  
D. Renames a branch  

**Answer:** B — `git clone` creates a local copy of a repository.

### 16. Which command downloads remote changes without integrating them into the current branch?

A. `git merge`  
B. `git push`  
C. `git fetch`  
D. `git commit`  

**Answer:** C — `git fetch` downloads remote references and objects without merging them into your current branch.

### 17. Which command usually downloads and integrates changes from a remote branch?

A. `git pull`  
B. `git tag`  
C. `git stash`  
D. `git init`  

**Answer:** A — `git pull` fetches changes and then integrates them, usually by merge or rebase depending on configuration and options.

### 18. Which command uploads local commits to a remote repository?

A. `git pull`  
B. `git push`  
C. `git clone`  
D. `git restore`  

**Answer:** B — `git push` sends local commits to a remote repository.

### 19. What does `git stash` do?

A. Permanently deletes a branch  
B. Temporarily saves changes outside the normal working-tree changes  
C. Uploads commits to GitHub  
D. Creates a new remote repository  

**Answer:** B — Stash saves local modifications for later restoration.

### 20. Which command unstages a file while keeping its working-tree changes?

A. `git restore --staged file.txt`  
B. `git clean -fd`  
C. `git reset --hard`  
D. `git delete file.txt`  

**Answer:** A — It removes the file from the staging area without discarding its working-tree edits.

---

# Section 3: Branching and Merging

### 21. What is a Git branch?

A. A separate line of development  
B. A GitHub password  
C. A file extension  
D. A database table  

**Answer:** A — Branches let developers develop changes independently.

### 22. Which command lists local branches?

A. `git branches --all-local`  
B. `git branch`  
C. `git list`  
D. `git log-branch`  

**Answer:** B — `git branch` lists local branches.

### 23. Which command creates and switches to a new branch?

A. `git branch --move`  
B. `git checkout --delete`  
C. `git switch -c feature-login`  
D. `git commit -b feature-login`  

**Answer:** C — `git switch -c` creates a branch and switches to it.

### 24. What is merging?

A. Combining changes from different development histories  
B. Deleting commit history  
C. Installing Git  
D. Renaming a remote  

**Answer:** A — Merging integrates changes from one branch into another.

### 25. What is a merge conflict?

A. A successful push  
B. A situation where Git cannot automatically combine changes  
C. A new repository  
D. A GitHub notification  

**Answer:** B — Conflicts require the developer to resolve incompatible changes.

### 26. Which command merges `feature-login` into the current branch?

A. `git merge feature-login`  
B. `git push feature-login`  
C. `git clone feature-login`  
D. `git init feature-login`  

**Answer:** A — The named branch is merged into the currently checked-out branch.

### 27. What does `git rebase` do?

A. Replays commits on top of another base  
B. Deletes every remote branch  
C. Installs GitHub  
D. Creates an issue  

**Answer:** A — Rebase reapplies commits onto a new base and can produce a linear history.

### 28. What is a detached HEAD?

A. HEAD points directly to a commit rather than a local branch  
B. Git is not installed  
C. The remote repository is deleted  
D. The working directory is empty  

**Answer:** A — Detached HEAD means you have checked out a specific commit rather than a branch reference.

### 29. Which command deletes a local branch that has been safely merged?

A. `git branch -d branch-name`  
B. `git delete branch-name`  
C. `git remove branch-name`  
D. `git clean branch-name`  

**Answer:** A — `git branch -d` deletes a local branch when Git considers it safely merged.

### 30. Which command shows a compact commit history with a graph?

A. `git graph`  
B. `git log --oneline --graph --decorate --all`  
C. `git branch --graph-only`  
D. `git status --history`  

**Answer:** B — This command displays a compact history graph across local and remote-tracking references.

---

# Section 4: GitHub Fundamentals

### 31. What is GitHub?

A. A cloud platform for hosting Git repositories and collaboration  
B. A programming language  
C. A database engine  
D. An operating system  

**Answer:** A — GitHub hosts repositories and provides collaboration tools built around Git.

### 32. What is a Pull Request?

A. A request to merge proposed changes into another branch  
B. A command to install Git  
C. A way to delete all commits  
D. A local text editor  

**Answer:** A — Pull Requests let contributors propose, review, and discuss changes before merging.

### 33. What is a fork?

A. A personal GitHub copy of another repository  
B. A local commit  
C. A Git installation package  
D. A merge conflict  

**Answer:** A — A fork creates a separate GitHub repository based on another repository.

### 34. What is the purpose of GitHub Issues?

A. To track bugs, tasks, and feature requests  
B. To configure a computer's network  
C. To install Git  
D. To delete branches automatically  

**Answer:** A — Issues organize project tasks and discussions about work.

### 35. What does starring a repository do?

A. Deletes the repository  
B. Bookmarks it and expresses appreciation  
C. Grants administrator access  
D. Automatically merges Pull Requests  

**Answer:** B — Stars help users save and show appreciation for repositories.

### 36. What is a GitHub Release commonly used for?

A. Publishing a project version with release notes and optional assets  
B. Deleting a repository  
C. Creating a password  
D. Replacing Git commits  

**Answer:** A — Releases package specific versions of a project, often associated with Git tags.

### 37. What is the purpose of a README file?

A. To document and explain a project  
B. To store Git passwords  
C. To replace all source code  
D. To create a branch automatically  

**Answer:** A — A README introduces a project and explains its setup, usage, and other important details.

### 38. What does a `.gitignore` file do?

A. Specifies intentionally untracked files for Git to ignore  
B. Deletes all Git history  
C. Pushes files automatically  
D. Creates Pull Requests  

**Answer:** A — It tells Git which untracked files and paths to ignore.

### 39. What is GitHub Actions used for?

A. Automating workflows such as testing, building, and deployment  
B. Editing images only  
C. Creating Git commits manually  
D. Replacing Git itself  

**Answer:** A — GitHub Actions runs automated workflows based on defined events or manual triggers.

### 40. What is the difference between Git and GitHub?

A. They are exactly the same  
B. Git is version-control software; GitHub is a hosting and collaboration platform  
C. GitHub works only offline  
D. Git is a web browser  

**Answer:** B — Git manages version history; GitHub hosts repositories and provides collaboration features.

---

# Section 5: Advanced Git and Troubleshooting

### 41. Which command reverses a commit by creating a new commit?

A. `git revert COMMIT_HASH`  
B. `git branch COMMIT_HASH`  
C. `git clone COMMIT_HASH`  
D. `git stash COMMIT_HASH`  

**Answer:** A — `git revert` creates a new commit that reverses the selected commit's changes.

### 42. What does `git reset --soft HEAD~1` do?

A. Moves the current branch back one commit and keeps the changes staged  
B. Deletes the entire repository  
C. Pushes the previous commit  
D. Deletes all remote branches  

**Answer:** A — A soft reset moves the branch pointer while preserving changes in the index.

### 43. Which command can help find a commit after a reset?

A. `git reflog`  
B. `git clean`  
C. `git remote`  
D. `git init`  

**Answer:** A — Reflog records recent local reference movements and can help locate commits.

### 44. What does `git cherry-pick` do?

A. Applies the changes from a selected commit to the current branch  
B. Deletes all branches  
C. Creates a GitHub account  
D. Installs a package  

**Answer:** A — Cherry-pick applies an existing commit's changes to the current branch.

### 45. What is a Git tag commonly used for?

A. Marking a specific commit, often for a release  
B. Deleting files automatically  
C. Creating a Pull Request  
D. Renaming a GitHub account  

**Answer:** A — Tags identify particular commits, commonly corresponding to software versions.

### 46. What does `git remote -v` display?

A. Configured remote repository URLs  
B. All local files  
C. Every commit's source code  
D. Installed programming languages  

**Answer:** A — It displays the configured remote names and their fetch and push URLs.

### 47. Why might GitHub reject a push with `fetch first`?

A. The remote contains changes missing from the local branch  
B. Git is always offline  
C. The repository contains a README  
D. The branch has a commit message  

**Answer:** A — Integrate the remote changes appropriately before pushing again.

### 48. What should you do before using a destructive command such as `git reset --hard`?

A. Inspect your repository status and protect important changes  
B. Delete the remote repository  
C. Disable Git permanently  
D. Remove every branch  

**Answer:** A — Inspecting and backing up work helps prevent accidental data loss.

### 49. What does `git fetch origin` do?

A. Downloads updates from the `origin` remote without merging them into the current branch  
B. Deletes the origin remote  
C. Creates a new local repository  
D. Automatically resolves every conflict  

**Answer:** A — Fetch updates remote-tracking references and downloads required Git objects.

### 50. What is the recommended way to handle secrets such as API keys?

A. Commit them into a public repository  
B. Store them in source code comments  
C. Keep them out of version control and use appropriate secret management  
D. Publish them in the README  

**Answer:** C — Keep credentials out of the repository and use environment variables or an appropriate secret-management system.

---

# Answer Key

| Question | Answer | Question | Answer |
|---:|:---:|---:|:---:|
| 1 | B | 26 | A |
| 2 | C | 27 | A |
| 3 | B | 28 | A |
| 4 | C | 29 | A |
| 5 | B | 30 | B |
| 6 | A | 31 | A |
| 7 | B | 32 | A |
| 8 | A | 33 | A |
| 9 | A | 34 | A |
| 10 | B | 35 | B |
| 11 | B | 36 | A |
| 12 | C | 37 | A |
| 13 | B | 38 | A |
| 14 | A | 39 | A |
| 15 | B | 40 | B |
| 16 | C | 41 | A |
| 17 | A | 42 | A |
| 18 | B | 43 | A |
| 19 | B | 44 | A |
| 20 | A | 45 | A |
| 21 | A | 46 | A |
| 22 | B | 47 | A |
| 23 | C | 48 | A |
| 24 | A | 49 | A |
| 25 | B | 50 | C |

---

# Suggested Scoring

| Score | Performance |
|---|---|
| 45–50 | Excellent |
| 38–44 | Very Good |
| 30–37 | Good |
| 20–29 | Needs More Practice |
| 0–19 | Review the Fundamentals |

## Final Learning Outcomes

After completing this assessment, learners should be able to:

- Explain Git and GitHub fundamentals.
- Identify common Git commands.
- Understand branching and merging.
- Describe GitHub collaboration features.
- Recognize advanced Git operations.
- Apply safe troubleshooting practices.

**Next Module:** [12 - Interview Preparation](../12-Interview-Preparation/README.md)
