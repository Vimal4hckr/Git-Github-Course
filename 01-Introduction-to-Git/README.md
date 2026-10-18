
# Module 01: Introduction to Git

## 1. Learning Objectives

After completing this module, you will be able to:

- Define Git and version control.
- Explain why developers use Git.
- Differentiate Git and GitHub.
- Understand repositories, commits, branches, and remotes.
- Explain the basic Git workflow.
- Identify real-world applications of Git.

---

## 2. What Is Git?

Git is a free, open-source, distributed version control system used to track changes in files and source code.

It allows developers to record project history, compare changes, restore earlier versions, and work on different features independently.

### Example

Imagine you are developing a website.

On Monday, you create a homepage.

On Tuesday, you add a navigation bar.

On Wednesday, you accidentally delete some important code.

Without version control, recovering the previous code may be difficult.

With Git, you can inspect earlier commits and recover the required changes.

### Key Features of Git

- Tracks changes to files.
- Maintains a history of commits.
- Supports branching and merging.
- Enables offline work on local repositories.
- Helps developers collaborate.
- Supports recovery from many common mistakes.

---

## 3. What Is Version Control?

Version control is a system that records changes to files over time so that developers can understand, compare, and manage different versions of their work.

### Why Is Version Control Important?

Without version control, developers may create confusing copies such as:

- project-final
- project-final-new
- project-final-updated
- project-final-latest

This approach makes it difficult to identify the correct version.

A version control system keeps a structured history of changes.

### Benefits

1. Change tracking
2. Version history
3. Collaboration
4. Error recovery
5. Feature development
6. Accountability
7. Easier code review

---

## 4. Types of Version Control Systems

### 4.1 Local Version Control

Changes and version history are managed on a single computer.

**Limitation:** Collaboration and centralized sharing are not built into the basic model.

### 4.2 Centralized Version Control

A central server stores the main version history, and users work with that server.

Examples include Subversion (SVN) and CVS.

**Limitation:** The central server is an important dependency for many operations.

### 4.3 Distributed Version Control

Each clone normally contains the repository's history, allowing many operations to be performed locally.

Examples include Git and Mercurial.

**Advantage:** Developers can commit and inspect history locally without requiring a network connection for every operation.

---

## 5. What Is GitHub?

GitHub is an online platform for hosting Git repositories and collaborating on software projects.

It provides tools that help developers share code, review changes, manage tasks, and coordinate development.

### Common GitHub Features

- Remote repositories
- Pull requests
- Issues
- Code reviews
- Project boards
- Releases
- GitHub Actions
- Repository access controls
- Profile and contribution history

### Example

A developer creates a project on a laptop and tracks its history with Git.

The developer then pushes the repository to GitHub so teammates can access it, review changes, and contribute.

---

## 6. Git vs GitHub

| Git | GitHub |
|---|---|
| Version control system | Online development and collaboration platform |
| Installed software | Primarily a hosted web service with related tools |
| Tracks changes and commits | Hosts repositories and supports collaboration |
| Works with local repositories | Provides remote repositories |
| Uses commands such as `git commit` | Provides pull requests, issues, and code reviews |
| Can be used offline for local work | Network access is normally needed for remote operations |

**Remember:** Git and GitHub are related, but they are not the same thing.

You can use Git without GitHub. You can also host Git repositories on other services or your own server.

---

## 7. Important Git Terminology

### 7.1 Repository

A repository is a collection of project files and Git metadata that records the project's version history.

### 7.2 Working Directory

The working directory contains the files you view and edit.

### 7.3 Staging Area

The staging area holds changes selected for the next commit.

### 7.4 Commit

A commit records a snapshot of the staged changes, together with metadata such as its author and message.

### 7.5 Branch

A branch is a movable reference to a commit. Branches allow developers to work on features or fixes independently.

### 7.6 Merge

A merge integrates changes from another branch into the current branch.

### 7.7 Remote

A remote is a named reference to another repository, commonly hosted on GitHub.

### 7.8 Clone

Cloning creates a local repository from an existing repository, normally including its history.

### 7.9 Push

Push sends local commits to a remote repository.

### 7.10 Pull

Pull fetches remote changes and integrates them into the current branch.

---

## 8. Understanding the Git Workflow

A typical Git workflow contains three main areas.

### Step 1: Working Directory

Create or edit project files.

### Step 2: Staging Area

Select changes using `git add`.

### Step 3: Repository

Record the staged changes using `git commit`.

### Example Commands

```bash
git status
git add README.md
git diff --staged
git commit -m "Add project introduction"
git log --oneline
```

### What Happens?

1. `git status` checks the current state.
2. `git add README.md` stages changes to the file.
3. `git diff --staged` lets you review staged changes.
4. `git commit` records the staged changes.
5. `git log --oneline` displays recent commit history.

These commands work with a repository that has already been initialized using `git init` or created using `git clone`.

---

## 9. Real-World Applications of Git

### Web Development

Track changes to HTML, CSS, JavaScript, and application source code.

### Mobile Development

Manage Android, iOS, and cross-platform application code.

### Data Science and AI

Version notebooks, scripts, configuration files, and documentation. Large datasets and generated model files may require separate storage strategies.

### Team Projects

Allow multiple developers to develop features in separate branches and review changes before merging.

### Open-Source Development

Contribute fixes, documentation, and new features through public repositories and pull requests.

### DevOps

Maintain source code, infrastructure definitions, deployment scripts, and CI/CD workflows.

---

## 10. Common Misconceptions

**Misconception 1:** Git requires an internet connection for every operation.

**Correction:** Most local Git operations work offline.

**Misconception 2:** GitHub and Git are identical.

**Correction:** Git is the version control system; GitHub is a platform that hosts Git repositories and adds collaboration features.

**Misconception 3:** Every saved file is automatically committed.

**Correction:** Changes must be staged and committed to enter normal Git history.

**Misconception 4:** A commit automatically uploads code to GitHub.

**Correction:** A commit is local until its commits are pushed to a remote repository.

**Misconception 5:** Branches create separate copies of the entire project every time.

**Correction:** Branches are references to commits. Git manages shared objects efficiently.

---

## 11. Practical Exercise

### Task 1: Answer the Following

1. What is Git?
2. Define version control.
3. What is the difference between Git and GitHub?
4. What is a repository?
5. What is a commit?
6. What is a branch?
7. What is the purpose of the staging area?
8. What is the difference between push and pull?
9. Can Git be used without GitHub?
10. Why is version control important in team projects?

### Task 2: Observe Git

Open a terminal inside your existing learning repository and execute:

```bash
git --version
git status
git log --oneline
```

Write down what each command displays.

If the repository has no commits yet, `git log` will report that the current branch has no commits.

---

## 12. Knowledge Check

1. Which tool tracks changes to source code?
   - A. Git
   - B. HTML
   - C. CSS
   - D. Chrome

2. Which platform commonly hosts Git repositories online?
   - A. Notepad
   - B. GitHub
   - C. Calculator
   - D. Paint

3. Which command stages changes?
   - A. `git push`
   - B. `git add`
   - C. `git log`
   - D. `git clone`

4. Which command records staged changes?
   - A. `git commit`
   - B. `git status`
   - C. `git branch`
   - D. `git remote`

5. Which command sends local commits to a remote repository?
   - A. `git init`
   - B. `git diff`
   - C. `git push`
   - D. `git status`

### Answers

1. A — Git
2. B — GitHub
3. B — `git add`
4. A — `git commit`
5. C — `git push`

---

## 13. Module Summary

In this module, you learned:

- What Git is and why it is used.
- The purpose of version control.
- The three broad types of version control systems.
- How Git differs from GitHub.
- Important Git terminology.
- The basic working directory, staging, and commit workflow.
- Practical applications and common misconceptions.

**Next Module:** Installation and Setup — installing Git, configuring your identity, and preparing VS Code for Git operations.
