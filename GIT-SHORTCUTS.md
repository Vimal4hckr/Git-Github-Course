# Git & GitHub Shortcuts
### Work Faster with Version Control 🚀

A quick-reference guide to essential Git commands for repository setup, daily workflows, branching, undoing changes, stashing, remote repositories, and debugging.

---

## 1. Repository & Setup Shortcuts

| Command | Description |
|---|---|
| `git init` | Initialize a new repository |
| `git clone <url>` | Clone a repository |
| `git status` | Check the status of files |
| `git config --global user.name "Name"` | Set your global username |
| `git config --global user.email "email"` | Set your global email |
| `git config --list` | View Git configuration |

## 2. Basic Workflow Shortcuts

| Command | Description |
|---|---|
| `git add .` | Stage eligible changes under the current directory |
| `git add <file>` | Stage a specific file |
| `git commit -m "message"` | Commit staged changes |
| `git commit -am "message"` | Stage and commit changes to tracked files |
| `git push` | Push commits to the configured remote |
| `git pull` | Fetch and integrate remote changes |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |

**Note:** `git commit -am` does not automatically include new, untracked files.

## 3. Branching Shortcuts

| Command | Description |
|---|---|
| `git branch` | List local branches |
| `git branch <name>` | Create a new branch |
| `git switch <name>` | Switch to a branch |
| `git switch -c <name>` | Create and switch to a new branch |
| `git checkout <name>` | Switch branches using the older checkout command |
| `git checkout -b <name>` | Create and switch to a branch |
| `git merge <branch>` | Merge a branch into the current branch |
| `git branch -d <name>` | Delete a safely merged local branch |

## 4. Undo & Restore Shortcuts

| Command | Description |
|---|---|
| `git restore <file>` | Discard unstaged changes in a tracked file |
| `git restore .` | Discard unstaged changes in tracked files under the current directory |
| `git restore --staged <file>` | Unstage a file while keeping its edits |
| `git reset --soft HEAD~1` | Undo the latest commit while keeping changes staged |
| `git reset --mixed HEAD~1` | Undo the latest commit while keeping changes unstaged |
| `git reset --hard HEAD~1` | Move back one commit and discard affected tracked-file changes |
| `git revert <commit>` | Create a new commit that reverses an earlier commit |
| `git clean -fd` | Remove untracked files and directories |

⚠️ **Caution:** `git reset --hard` and `git clean -fd` can permanently discard work. Review `git status` first and back up anything important.

## 5. Stash Shortcuts

| Command | Description |
|---|---|
| `git stash` | Stash supported local modifications |
| `git stash list` | List saved stashes |
| `git stash apply` | Apply the latest stash and keep it saved |
| `git stash pop` | Apply the latest stash and remove it if successful |
| `git stash drop` | Remove the latest stash |
| `git stash push -m "message"` | Save a stash with a descriptive message |

## 6. Remote Repository Shortcuts (GitHub)

| Command | Description |
|---|---|
| `git remote -v` | View configured remote URLs |
| `git remote add origin <url>` | Add a remote named `origin` |
| `git fetch origin` | Fetch remote updates without integrating them |
| `git push -u origin <branch>` | Push a branch and set its upstream |
| `git pull origin <branch>` | Fetch and integrate changes from a remote branch |
| `git push origin --delete <branch>` | Delete a remote branch |

**Tip:** `origin` is a conventional remote name. Replace it if your remote uses a different name.

## 7. Useful History & Debugging Shortcuts

| Command | Description |
|---|---|
| `git log --oneline` | View compact commit history |
| `git log --graph --oneline --all` | View commit history as a graph |
| `git diff` | Inspect working-tree changes |
| `git show <commit>` | View details of a commit |
| `git blame <file>` | See who last changed each line |
| `git bisect start` | Begin a binary search through commit history |
| `git reflog` | Inspect recent local reference movements |
| `git log -5 --oneline` | View the five latest commits |

### Example: Find a bug with Git Bisect

```bash
git bisect start
git bisect bad
git bisect good <known-good-commit>
```

Git checks commits between the known-good and bad states. Test each checked-out revision and mark it with:

```bash
git bisect good
```

or:

```bash
git bisect bad
```

Continue until Git identifies the commit that introduced the problem. Then finish with:

```bash
git bisect reset
```

## 8. Tags & Releases

| Command | Description |
|---|---|
| `git tag` | List tags |
| `git tag v1.0.0` | Create a lightweight tag |
| `git tag -a v1.0.0 -m "Release"` | Create an annotated tag |
| `git show v1.0.0` | Inspect a tag |
| `git push origin v1.0.0` | Push a specific tag |
| `git push origin --tags` | Push local tags to the remote |

## 9. Quick Daily Workflow

Use this sequence when working on an existing project:

```bash
git status
git pull
git switch -c feature-name
# Make your changes
git add .
git commit -m "Describe your changes"
git push -u origin feature-name
```

Open a Pull Request on GitHub to propose merging the feature branch into the target branch.

If the branch already exists, switch to it rather than creating it again. Follow your team's preferred synchronization and review process.

---

## 10. Best Practices

- Write meaningful commit messages.
- Check `git status` before committing.
- Create separate branches for independent features.
- Review changes before staging and committing.
- Pull or fetch remote changes regularly.
- Never commit passwords, tokens, or API keys.
- Avoid rewriting shared history without team agreement.
- Back up important work before destructive commands.

---

**Better Version Control. Better Code. Better Collaboration.**

*Keep learning. Keep building. Keep committing!* 🚀