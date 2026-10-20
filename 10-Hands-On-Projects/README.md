
# 10 - Hands-On Git & GitHub Projects

## 📌 Overview

The best way to learn Git and GitHub is by building practical projects. This module contains five hands-on projects designed to help you practice version control, branching, collaboration, and repository management.

## Projects Included

1. Personal Portfolio Repository
2. Feature Branch Workflow
3. Team Collaboration Project
4. Open-Source Contribution Simulation
5. Release Management Project

---

# Project 1: Personal Portfolio Repository

## Objective

Create a professional GitHub repository that documents your skills, projects, and learning progress.

## Step 1: Create the project folder

```bat
mkdir GitHub-Portfolio
cd GitHub-Portfolio
```

## Step 2: Initialize Git

```bash
git init
```

## Step 3: Create project files

```bat
echo # My Developer Portfolio > README.md
echo My skills and projects. > ABOUT.md
echo # My Projects > PROJECTS.md
```

## Step 4: Stage and commit

```bash
git add .
git commit -m "Create portfolio repository"
```

## Step 5: Create a GitHub repository

1. Open GitHub.
2. Create a repository named `GitHub-Portfolio`.
3. Do not initialize it with another README if you already created one locally.

## Step 6: Connect the remote

Replace `YOUR-USERNAME` with your GitHub username.

```bash
git remote add origin https://github.com/YOUR-USERNAME/GitHub-Portfolio.git
git branch -M main
git push -u origin main
```

## Expected Result

Your local project is available on GitHub with a README and documentation files.

---

# Project 2: Feature Branch Workflow

## Objective

Learn how to develop a feature on a separate branch and merge it into `main`.

## Step 1: Open your project

```bash
git switch main
git pull origin main
```

## Step 2: Create a feature branch

```bash
git switch -c feature-contact-page
```

## Step 3: Create a file

Create `contact.md` and add:

```markdown
# Contact

Add your professional contact links here.
```

## Step 4: Commit the feature

```bash
git add contact.md
git commit -m "Add contact page documentation"
```

## Step 5: Push the branch

```bash
git push -u origin feature-contact-page
```

## Step 6: Open a Pull Request

1. Open the repository on GitHub.
2. Create a Pull Request from `feature-contact-page` into `main`.
3. Review the changes.
4. Merge the Pull Request.

## Step 7: Update your local main branch

```bash
git switch main
git pull origin main
```

## Expected Result

You have completed a feature branch workflow using GitHub Pull Requests.

---

# Project 3: Team Collaboration

## Objective

Simulate a collaborative project where multiple developers contribute documentation.

## Team Roles

| Team Member | Responsibility |
|---|---|
| Developer 1 | Project overview |
| Developer 2 | Installation instructions |
| Developer 3 | Feature documentation |
| Developer 4 | Testing instructions |

## Step 1: Clone the shared repository

Each authorized team member should clone the same repository.

```bash
git clone https://github.com/OWNER/TEAM-PROJECT.git
cd TEAM-PROJECT
```

Replace `OWNER` and `TEAM-PROJECT` with the actual repository details.

## Step 2: Create an individual branch

For example, Developer 1 can run:

```bash
git switch -c docs/project-overview
```

Developer 2 can use:

```bash
git switch -c docs/installation
```

## Step 3: Make changes

Each developer creates or edits the files assigned to them.

## Step 4: Commit changes

```bash
git add .
git commit -m "Add project documentation"
```

Use a commit message that describes the actual changes.

## Step 5: Push the branch

```bash
git push -u origin docs/project-overview
```

Each developer must push their own branch name.

## Step 6: Review and merge

Open a Pull Request on GitHub. Review the changes and merge them when ready.

## Expected Result

Each developer contributes independently, while the team integrates changes through Pull Requests.

---

# Project 4: Open-Source Contribution Simulation

## Objective

Practice the process used to contribute to open-source projects.

## Step 1: Select a repository

Choose a public repository that welcomes contributions. Read its contribution guidelines and license.

## Step 2: Fork the repository

Click **Fork** on GitHub.

## Step 3: Clone your fork

```bash
git clone https://github.com/YOUR-USERNAME/PROJECT.git
cd PROJECT
```

## Step 4: Add the original repository

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/PROJECT.git
```

Check the remote configuration:

```bash
git remote -v
```

## Step 5: Create a branch

```bash
git switch -c docs/improve-readme
```

## Step 6: Make a useful change

For example:

- Correct a documentation error.
- Improve installation instructions.
- Add a missing usage example.
- Fix a broken link.

## Step 7: Commit and push

```bash
git add .
git commit -m "Improve project documentation"
git push -u origin docs/improve-readme
```

## Step 8: Open a Pull Request

Open a Pull Request from your fork to the original repository, following its contribution guidelines.

## Expected Result

You understand how forks, branches, and Pull Requests work together in open-source development.

---

# Project 5: Release Management

## Objective

Create a versioned release using Git tags and GitHub Releases.

## Step 1: Check your project status

```bash
git status
```

Commit any intended changes before creating the release.

## Step 2: Create an annotated tag

```bash
git tag -a v1.0.0 -m "First stable release"
```

## Step 3: Inspect the tag

```bash
git show v1.0.0
```

## Step 4: Push the tag

```bash
git push origin v1.0.0
```

## Step 5: Create a GitHub Release

1. Open the repository on GitHub.
2. Navigate to **Releases**.
3. Select **Draft a new release**.
4. Choose the `v1.0.0` tag.
5. Add a title and release notes.
6. Publish the release.

## Example Release Notes

```markdown
# Version 1.0.0

## Features
- Initial project structure.
- Added project documentation.
- Added installation instructions.

## Improvements
- Improved README formatting.

## Installation
Follow the instructions in README.md.
```

Only include features that are actually present in your project.

## Expected Result

Your project has a tagged version and a published GitHub Release.

---

# Additional Practice Challenges

Complete these challenges after finishing the five projects.

## Challenge 1: Branch Management

- Create two feature branches.
- Make separate commits.
- Merge the branches using Pull Requests.
- Delete the merged remote branches if they are no longer needed.

## Challenge 2: Conflict Resolution

- Create two branches.
- Modify the same line in a file differently.
- Merge one branch into the other.
- Resolve the conflict and complete the merge.

Use a test repository so you do not accidentally damage important work.

## Challenge 3: Stashing

```bash
git stash push -m "Temporary experiment"
git stash list
git stash pop
```

Explain when stashing is useful.

## Challenge 4: Git History

```bash
git log --oneline --graph --decorate --all
```

Identify the commits, branches, and merge points.

## Challenge 5: Documentation Quality

Improve a repository by adding:

- A professional README.
- Installation instructions.
- Usage examples.
- Screenshots where useful.
- Contribution guidelines.
- A license when appropriate.

---

# Project Submission Checklist

Use this checklist to evaluate your work.

- [ ] Repository created successfully.
- [ ] README contains a project overview.
- [ ] Changes committed with meaningful messages.
- [ ] Feature branch created and pushed.
- [ ] Pull Request created and reviewed.
- [ ] Merge conflict exercise completed.
- [ ] GitHub Release created.
- [ ] Project documentation updated.
- [ ] No passwords, API keys, or other secrets committed.
- [ ] Repository is available on GitHub.

---

# Final Learning Outcomes

After completing these projects, you should be able to:

- Initialize and manage Git repositories.
- Connect local projects to GitHub.
- Create branches and manage commits.
- Push changes to remote repositories.
- Collaborate through Pull Requests.
- Resolve merge conflicts.
- Contribute through forks.
- Create tags and releases.
- Maintain professional project documentation.

**Next Module:** [11 - Git & GitHub MCQs](../11-Git-GitHub-MCQs/README.md)
