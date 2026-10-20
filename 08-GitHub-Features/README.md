
# 08 - GitHub Features

## 📌 Overview

GitHub is a cloud-based platform for hosting Git repositories and collaborating with developers.

In this module, you will learn:

- GitHub Issues
- Pull Requests
- Forks
- Stars and Watch
- GitHub Releases
- GitHub Discussions
- GitHub Projects
- GitHub Notifications
- GitHub README profiles
- GitHub Actions overview

---

## 1. GitHub Issues

### What are GitHub Issues?

GitHub Issues help teams track bugs, feature requests, improvements, and tasks.

### Common uses

- Report a bug.
- Request a new feature.
- Track project tasks.
- Discuss a problem with team members.

### Create an issue

1. Open your GitHub repository.
2. Select the **Issues** tab.
3. Click **New issue**.
4. Enter a title and description.
5. Add labels or assign the issue if needed.
6. Click **Create**.

### Example issue

**Title:** Fix login page validation

**Description:**

```text
Problem:
The login form accepts an empty password.

Expected result:
The form should display a validation message.

Tasks:
- Validate the password field.
- Display an error message.
- Test the login form.
```

### Useful issue labels

- `bug` — Something is not working.
- `enhancement` — A feature improvement.
- `documentation` — Documentation changes.
- `good first issue` — A suitable task for new contributors.
- `help wanted` — Extra help is welcome.

---

## 2. Pull Requests

### What is a Pull Request?

A Pull Request (PR) proposes changes from one branch into another branch. Team members can review the changes before they are merged.

### Typical workflow

1. Create a feature branch.
2. Make your changes.
3. Commit and push the branch.
4. Open a Pull Request on GitHub.
5. Review the changes.
6. Resolve feedback or conflicts.
7. Merge the Pull Request when approved.

### Example commands

Create a feature branch:

```bash
git switch -c feature-login
```

Make your changes, then stage and commit them:

```bash
git add .
git commit -m "Add login feature"
```

Push the branch:

```bash
git push -u origin feature-login
```

Then open your repository on GitHub and create a Pull Request.

### What should a Pull Request contain?

- A clear title.
- A summary of the changes.
- The reason for the changes.
- Testing details.
- Screenshots when useful.
- Related issue references.

### Example Pull Request description

```markdown
## Summary
Added login form validation.

## Changes
- Added required-field validation.
- Added error messages.
- Improved form feedback.

## Testing
- Tested empty fields.
- Tested valid credentials.

## Related Issue
Closes #12
```

Replace `12` with the actual issue number.

---

## 3. Forks

### What is a fork?

A fork is your own GitHub copy of another repository. It lets you experiment or contribute without directly changing the original repository.

### How to fork a repository

1. Open the repository you want to contribute to.
2. Click **Fork**.
3. Select your GitHub account.
4. Create the fork.

### Clone your fork

Copy the URL of your fork, then run:

```bash
git clone https://github.com/YOUR-USERNAME/REPOSITORY.git
```

Replace the placeholders with your username and repository name.

Enter the folder:

```bash
cd REPOSITORY
```

### Connect the original repository

Add the original repository as an `upstream` remote:

```bash
git remote add upstream https://github.com/ORIGINAL-OWNER/REPOSITORY.git
```

Check the remotes:

```bash
git remote -v
```

### Fetch changes from the original repository

```bash
git fetch upstream
```

If the original repository uses `main`, update your local `main` branch with:

```bash
git switch main
git merge upstream/main
```

This assumes your local `main` branch exists and has no conflicting local changes.

### Contribution workflow

```text
Original Repository
        |
        v
      Fork
        |
        v
      Clone
        |
        v
Create Feature Branch
        |
        v
Make Changes and Commit
        |
        v
Push to Your Fork
        |
        v
Open Pull Request
```

---

## 4. Stars and Watch

### Stars

Starring a repository is a way to bookmark it and show appreciation.

**Use Stars to:**
- Save useful projects.
- Discover interesting repositories.
- Recognize developers' work.

### Watch

Watching a repository controls which notifications you receive about activity in that repository.

Depending on your notification settings, you can choose to receive notifications about different kinds of activity.

**Remember:** Starring and watching are different features.

---

## 5. GitHub Releases

### What is a Release?

A GitHub Release packages a specific version of a project and provides release notes and optional downloadable assets.

Releases are often associated with Git tags.

### Create a release tag

```bash
git tag -a v1.0.0 -m "First stable release"
```

Push the tag:

```bash
git push origin v1.0.0
```

### Create a release on GitHub

1. Open your repository.
2. Go to **Releases**.
3. Select **Draft a new release**.
4. Choose the tag `v1.0.0`.
5. Add a release title.
6. Write release notes.
7. Publish the release.

### Example release notes

```markdown
# Version 1.0.0

## Features
- Initial project setup.
- Added login functionality.
- Added input validation.

## Fixes
- Fixed form validation issues.

## Installation
Follow the installation instructions in README.md.
```

Only list features and fixes that actually exist in your project.

---

## 6. GitHub Discussions

### What are Discussions?

GitHub Discussions provides a space for conversations that do not necessarily need to be tracked as bugs or tasks.

### Common uses

- Ask questions.
- Share ideas.
- Discuss announcements.
- Help other developers.
- Collect community feedback.

### Issues vs Discussions

| Feature | Issues | Discussions |
|---|---|---|
| Main purpose | Track actionable work | Community conversations |
| Bug reports | Common use | Usually not the primary use |
| Feature tasks | Common use | Useful for early-stage ideas |
| Questions | Possible | Often a better fit |

Discussions must be enabled for the repository to use this feature.

---

## 7. GitHub Projects

### What is GitHub Projects?

GitHub Projects helps teams plan and track work using tables, boards, and roadmaps.

### Example project board

| Task | Status | Priority |
|---|---|---|
| Create login page | Done | High |
| Add dashboard | In Progress | High |
| Write documentation | Todo | Medium |
| Add unit tests | Todo | High |

### Typical workflow

1. Open the repository or organization.
2. Create a Project.
3. Choose a table or board layout.
4. Add issues and pull requests.
5. Organize tasks by status and priority.
6. Track progress as work is completed.

### Suggested statuses

- Todo
- In Progress
- In Review
- Done

---

## 8. GitHub Notifications

Notifications help you follow activity related to repositories, issues, Pull Requests, and discussions.

### Common notification events

- Someone mentions you.
- Someone requests your review.
- A Pull Request receives feedback.
- An issue you follow is updated.

### Manage notifications

1. Open GitHub.
2. Open the notifications inbox.
3. Review unread activity.
4. Mark items as read or manage subscriptions.
5. Adjust notification preferences in GitHub settings.

Use notification settings to avoid unnecessary updates while keeping track of important work.

---

## 9. GitHub Profile README

### What is a Profile README?

A Profile README appears on your GitHub profile and introduces you to other developers.

To create one, create a public repository whose name exactly matches your GitHub username, then add a `README.md` file to it.

### Example profile README

```markdown
# Hi, I'm Your Name 👋

## About Me
- Software developer and lifelong learner.
- Interested in web development and AI.
- Building practical projects and improving my skills.

## Technologies
- Python
- Java
- JavaScript
- HTML and CSS
- Git and GitHub

## Current Goals
- Build real-world applications.
- Contribute to open-source projects.
- Improve problem-solving skills.

## Connect With Me
- GitHub: https://github.com/YOUR-USERNAME
```

Replace the example details with your actual skills, projects, and links.

### Profile improvement tips

- Pin your best repositories.
- Add meaningful project descriptions.
- Keep project READMEs updated.
- Include setup instructions.
- Show real projects and contributions.

---

## 10. GitHub Actions Overview

### What are GitHub Actions?

GitHub Actions automates workflows in a repository. It can run tests, check code quality, build applications, and perform deployments.

### Example use cases

- Run tests when code is pushed.
- Check code when a Pull Request is opened.
- Build a project automatically.
- Deploy an application after an approved workflow.

### Example workflow

Create this file:

`.github/workflows/hello.yml`

```yaml
name: Hello Workflow

on:
  push:
  workflow_dispatch:

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - name: Display a message
        run: echo "Hello from GitHub Actions!"
```

### What happens?

- `name` gives the workflow a name.
- `on` defines when it runs.
- `push` triggers it when commits are pushed.
- `workflow_dispatch` allows a manual run.
- `jobs` contains the work to execute.
- `runs-on` selects the runner environment.
- `steps` lists the commands or actions.

GitHub Actions workflows require valid YAML syntax and repository permissions. This example only prints a message; it does not test or deploy an application.

---

## 11. Practical Exercises

### Exercise 1: Create an Issue

- Open your repository.
- Create an issue titled `Improve README documentation`.
- Add a description and label.

### Exercise 2: Open a Pull Request

- Create a branch called `feature-documentation`.
- Update your README.
- Commit and push your changes.
- Open a Pull Request on GitHub.

### Exercise 3: Fork a Repository

- Fork a public repository.
- Clone your fork.
- Add the original repository as `upstream`.
- Fetch upstream changes.

### Exercise 4: Create a Release

- Create an annotated tag called `v1.0.0`.
- Push the tag.
- Draft a GitHub Release using that tag.

### Exercise 5: Create a Project Board

- Create a GitHub Project.
- Add three tasks.
- Track their progress using Todo, In Progress, and Done.

### Exercise 6: Create a Profile README

- Create a repository named exactly after your GitHub username.
- Add a README.
- Describe your skills and projects.

---

## 12. Knowledge Check

1. What is the purpose of a GitHub Issue?
2. What is a Pull Request?
3. What is the difference between a fork and a clone?
4. What does starring a repository do?
5. Why are GitHub Releases useful?
6. When would you use Discussions instead of Issues?
7. What can GitHub Projects help you manage?
8. What is a GitHub Profile README?
9. What does GitHub Actions automate?
10. Why should Pull Requests be reviewed before merging?

### Answers

1. To track bugs, tasks, and feature requests.
2. A proposal to merge changes from one branch into another.
3. A fork creates a GitHub copy; a clone downloads a repository to your computer.
4. It bookmarks a repository and shows appreciation.
5. They package project versions with notes and optional assets.
6. For general questions, ideas, and community conversations.
7. Tasks, issues, Pull Requests, and project progress.
8. A README displayed on your GitHub profile.
9. Workflows such as tests, builds, and deployments.
10. To check correctness, quality, and potential problems before integration.

---

## Summary

In this module, you learned about:

- Issues and Pull Requests.
- Forks and upstream repositories.
- Stars and Watch.
- Releases and version tags.
- Discussions and Projects.
- Notifications.
- Profile READMEs.
- GitHub Actions.

**Next Module:** [09 - Git Workflows](../09-Git-Workflows/README.md)
