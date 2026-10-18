
# Module 02: Git Installation and Setup

## 1. Learning Objectives

After completing this module, you will be able to:

- Install Git on Windows.
- Verify the Git installation.
- Understand Git Bash, PowerShell, and the VS Code terminal.
- Configure your Git username and email.
- Understand global and local Git configurations.
- Verify your configuration.
- Troubleshoot common installation problems.

---

## 2. What Is Git Installation?

Git must be installed on your computer before you can use its commands in a terminal.

Once installed, you can use Git through:

- Visual Studio Code terminal
- Windows PowerShell
- Git Bash
- Windows Command Prompt

You do not need to install Git separately for each project.

---

## 3. Install Git on Windows

### Step 1: Open the Official Website

Visit:

https://git-scm.com/downloads

### Step 2: Download Git

Select Windows and download the appropriate installer.

### Step 3: Run the Installer

Open the downloaded installer and follow the setup wizard.

For a beginner, the default installation options are generally suitable. Review the PATH and terminal integration options carefully.

### Step 4: Complete Installation

Finish the installation process.

### Step 5: Open a New Terminal

Open PowerShell, Git Bash, or the VS Code terminal.

If a terminal was already open during installation, close it and open a new one so it can detect the updated PATH.

---

## 4. Verify Git Installation

Execute:

```bash
git --version
```

### Purpose

Displays the installed Git version.

### Example Output

```text
git version 2.x.x
```

The exact version depends on your installation.

### If the Command Is Not Recognized

1. Confirm that Git was installed successfully.
2. Close and reopen the terminal.
3. Check whether Git was added to PATH.
4. Restart VS Code if necessary.
5. Reinstall Git if the installation is incomplete.

---

## 5. Understanding Git Bash

Git Bash provides a Bash-compatible terminal environment on Windows, along with Git command-line tools.

Example:

```bash
pwd
ls
mkdir demo-project
cd demo-project
```

### Common Uses

- Running Git commands.
- Using Bash-style commands.
- Following tutorials written for Linux or macOS terminals.
- Running shell scripts compatible with Bash.

---

## 6. Understanding PowerShell

PowerShell is a command-line shell and scripting environment available on Windows.

Example:

```powershell
Get-Location
Get-ChildItem
New-Item -ItemType Directory demo-project
Set-Location demo-project
```

### Common Uses

- Managing Windows files and folders.
- Running Git commands.
- Automating tasks.
- Executing PowerShell scripts.

Git commands such as `git status`, `git add`, and `git commit` work in both PowerShell and Git Bash.

**Important:** Some file-management commands differ between shells. Make sure you use the correct syntax for your terminal.

---

## 7. Using Git in VS Code

### Step 1

Open Visual Studio Code.

### Step 2

Open your project folder.

### Step 3

Select:

Terminal → New Terminal

### Step 4

Check Git:

```bash
git --version
```

### Step 5

Check your current directory:

```bash
git rev-parse --show-toplevel
```

The last command works only when the current directory is inside a Git repository.

### Step 6

Check the repository status:

```bash
git status
```

If the directory is not yet a Git repository, initialize it with `git init` when appropriate.

---

## 8. Configure Your Git Username

Git records author information in commits.

Execute:

```bash
git config --global user.name "Your Name"
```

Replace `Your Name` with the name you want recorded as the commit author.

### Example

```bash
git config --global user.name "Vimal"
```

### Explanation

- `git config` manages Git configuration.
- `--global` applies the setting to your user account across repositories by default.
- `user.name` specifies the commit author's name.

---

## 9. Configure Your Git Email

Execute:

```bash
git config --global user.email "you@example.com"
```

Replace the example email with your preferred commit author email.

### Example

```bash
git config --global user.email "your-email@example.com"
```

If you want your commits linked to your GitHub profile, use an email associated with your GitHub account or the private noreply email provided by GitHub.

**Important:** This configures commit author information. It does not sign you in to GitHub or authenticate a push.

---

## 10. Verify Git Configuration

### Display Global Configuration

```bash
git config --global --list
```

### Display Effective Configuration

```bash
git config --list
```

The second command can display values from multiple configuration levels.

### Check the Username

```bash
git config user.name
```

### Check the Email

```bash
git config user.email
```

Review the output to ensure the correct values are configured.

---

## 11. Global vs Local Configuration

### Global Configuration

Applies to your user account across repositories unless overridden.

```bash
git config --global user.name "Vimal"
```

### Local Configuration

Applies to the current repository.

First, move into the project directory and ensure it is a Git repository.

```bash
git config --local user.name "Project Author"
git config --local user.email "project@example.com"
```

Local values override global values for the corresponding settings in that repository.

### When Should You Use Each?

- Global: When you normally use the same author identity for your projects.
- Local: When a particular repository needs a different author identity.

---

## 12. Other Useful Configuration Commands

### List Configuration with Its Source

```bash
git config --list --show-origin
```

Shows configuration values and the files from which they were loaded.

### Set the Default Initial Branch Name

```bash
git config --global init.defaultBranch main
```

New repositories initialized with `git init` will use `main` as their initial branch, unless another option overrides it.

### Remove a Global Username Setting

```bash
git config --global --unset user.name
```

Use this only when you intend to remove that setting.

### Open Git Configuration in an Editor

```bash
git config --global --edit
```

Opens the global configuration file in the configured editor.

---

## 13. Git Installation vs GitHub Authentication

These are two separate tasks.

### Git Installation

Installs the Git software on your computer.

### Git Configuration

Sets options such as your commit author name and email.

### GitHub Authentication

Verifies that you have permission to access a remote repository.

GitHub authentication can use browser-based sign-in through a credential manager, SSH keys, or other supported methods.

For HTTPS Git operations, your regular GitHub account password is not accepted as a Git password.

---

## 14. Common Errors and Solutions

### Error 1: git Is Not Recognized

**Possible cause:** Git is missing from PATH or the terminal has not refreshed its environment.

**Solution:** Verify the installation, open a new terminal, and check PATH configuration.

### Error 2: Author Identity Unknown

**Possible cause:** Git username or email is not configured.

**Solution:**

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Error 3: Permission Denied

**Possible cause:** The account or authentication method does not have the required access.

**Solution:** Check your authentication method and repository permissions.

### Error 4: Repository Not Found

**Possible causes:**

- Incorrect repository URL.
- Repository does not exist.
- Repository is private and you lack access.

**Solution:** Verify the remote URL and your access permissions.

### Error 5: Wrong Author Email

**Possible cause:** Git is using an incorrect configured email.

**Solution:** Update the relevant global or local configuration. Remember that changing configuration affects future commits, not the author information already recorded in existing commits.

---

## 15. Practical Exercises

### Exercise 1: Verify Installation

Run:

```bash
git --version
```

Record the version displayed.

### Exercise 2: Configure Git

Set your username and email.

### Exercise 3: Verify Configuration

Run:

```bash
git config --global --list
```

Confirm that your values are correct.

### Exercise 4: Use VS Code Terminal

Open your learning repository and run:

```bash
git status
git rev-parse --show-toplevel
```

Record the output of both commands.

### Exercise 5: Understand Configuration Levels

Inside a test repository, configure a local username and compare it with the global username.

```bash
git config --global user.name
git config --local user.name
```

The local command requires a Git repository with a local configuration.

---

## 16. Knowledge Check

1. Which command displays the installed Git version?
   - A. `git check`
   - B. `git --version`
   - C. `git install`
   - D. `git start`

2. Which option configures Git settings for your user account?
   - A. `--local`
   - B. `--global`
   - C. `--branch`
   - D. `--remote`

3. Which command displays global Git configuration?
   - A. `git config --global --list`
   - B. `git show files`
   - C. `git branch --global`
   - D. `git remote --list`

4. Does configuring `user.name` authenticate you to GitHub?
   - A. Yes
   - B. No

5. Which terminal can run Git commands on Windows?
   - A. PowerShell
   - B. Git Bash
   - C. VS Code terminal
   - D. All of the above

### Answers

1. B — `git --version`
2. B — `--global`
3. A — `git config --global --list`
4. B — No
5. D — All of the above

---

## 17. Module Summary

In this module, you learned:

- How to install and verify Git.
- How to use Git through VS Code.
- The differences between Git Bash and PowerShell.
- How to configure your username and email.
- Global and local Git settings.
- How to diagnose common installation and configuration errors.
- Why Git configuration and GitHub authentication are different.

**Next Module:** Basic Git Commands — initializing repositories, tracking files, staging changes, committing snapshots, and inspecting history.
