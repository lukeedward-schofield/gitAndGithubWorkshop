# Git & GitHub Workshop

A quick reference for getting started with Git and GitHub — covering installation, essential commands, branching, naming conventions, and helpful resources.

## Table of Contents

- [Prerequisites & Installation](#prerequisites--installation)
- [First-Time Setup](#first-time-setup)
- [Basic Git Commands](#basic-git-commands)
- [Branch Commands](#branch-commands)
- [Naming Conventions](#naming-conventions)
- [Resources](#resources)

## Prerequisites & Installation

### 1. Install Git

#### Windows

- Download the installer from [git-scm.com/download/win](https://git-scm.com/download/win).
- Run the installer and accept the defaults (Git Bash is included).
- Verify the installation:
  ```bash
  git --version
  ```

#### macOS

- **Using Homebrew** (recommended):
  ```bash
  brew install git
  ```
- **Or** install the Xcode Command Line Tools:
  ```bash
  xcode-select --install
  ```
- Verify the installation:
  ```bash
  git --version
  ```

#### Linux

- **Debian / Ubuntu:**
  ```bash
  sudo apt update && sudo apt install git
  ```
- **Fedora:**
  ```bash
  sudo dnf install git
  ```
- **Arch:**
  ```bash
  sudo pacman -S git
  ```
- Verify the installation:
  ```bash
  git --version
  ```

### 2. Create a GitHub Account

- Sign up at [github.com](https://github.com/join).
- (Optional) Install [GitHub Desktop](https://desktop.github.com/) for a graphical interface.

### 3. Set Up Authentication (SSH)

Generate an SSH key and add it to your GitHub account so you can push without typing your password each time.

```bash
# Generate a new SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Start the ssh-agent
eval "$(ssh-agent -s)"

# Add your key to the agent
ssh-add ~/.ssh/id_ed25519

# Copy the public key, then paste it at github.com/settings/keys
cat ~/.ssh/id_ed25519.pub
```

Add the copied key under **GitHub → Settings → SSH and GPG keys → New SSH key**.

## First-Time Setup

Configure your identity (used in every commit):

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"

# Set the default branch name to main
git config --global init.defaultBranch main

# Set your preferred editor (optional)
git config --global core.editor "code --wait"

# View all settings
git config --list
```

## Basic Git Commands

| Command | Description |
| --- | --- |
| `git init` | Initialize a new Git repository in the current folder. |
| `git clone <url>` | Copy a remote repository to your machine. |
| `git status` | Show the state of the working directory and staging area. |
| `git add <file>` | Stage a specific file for the next commit. |
| `git add .` | Stage all changed files. |
| `git commit -m "message"` | Save staged changes with a message. |
| `git log` | View commit history. |
| `git log --oneline` | View a compact, one-line-per-commit history. |
| `git diff` | Show unstaged changes. |
| `git pull` | Fetch and merge changes from the remote. |
| `git push` | Upload local commits to the remote. |
| `git remote -v` | List configured remote repositories. |
| `git restore <file>` | Discard changes in the working directory. |
| `git reset <file>` | Unstage a file while keeping the changes. |

### A Typical Workflow

```bash
git clone git@github.com:user/repo.git   # Get the project
cd repo
git checkout -b feature/my-change        # Create a branch
# ... make your edits ...
git add .                                # Stage changes
git commit -m "feat: add my change"      # Commit
git push -u origin feature/my-change     # Push to GitHub
# ... open a Pull Request on GitHub ...
```

## Branch Commands

| Command | Description |
| --- | --- |
| `git branch` | List all local branches. |
| `git branch <name>` | Create a new branch. |
| `git checkout <name>` | Switch to an existing branch. |
| `git checkout -b <name>` | Create a new branch and switch to it. |
| `git switch <name>` | Switch branches (newer alternative to checkout). |
| `git switch -c <name>` | Create and switch to a new branch. |
| `git merge <name>` | Merge the named branch into the current branch. |
| `git branch -d <name>` | Delete a branch (safe — blocks if unmerged). |
| `git branch -D <name>` | Force-delete a branch. |
| `git push origin <name>` | Push a branch to the remote. |
| `git push origin --delete <name>` | Delete a branch on the remote. |

## Naming Conventions

### Branch Names

Use lowercase, hyphen-separated words with a category prefix:

| Prefix | Use For | Example |
| --- | --- | --- |
| `feature/` | New features | `feature/user-login` |
| `bugfix/` | Bug fixes | `bugfix/header-overflow` |
| `hotfix/` | Urgent production fixes | `hotfix/payment-crash` |
| `docs/` | Documentation changes | `docs/update-readme` |
| `chore/` | Maintenance / tooling | `chore/upgrade-deps` |

**Tips:**
- Keep names short and descriptive.
- Use hyphens (`-`), not spaces or underscores.
- Optionally include an issue number: `feature/42-user-login`.

### Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) style:

```
<type>: <short summary>
```

| Type | Meaning |
| --- | --- |
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no code change |
| `refactor` | Code change that isn't a fix or feature |
| `test` | Adding or fixing tests |
| `chore` | Build process or tooling changes |

**Good commit messages:**
- `feat: add password reset flow`
- `fix: prevent crash on empty input`
- `docs: clarify installation steps`

**Guidelines:**
- Use the imperative mood ("add", not "added").
- Keep the summary under ~50 characters.
- Capitalize consistently and skip the trailing period.

## Resources

- [Pro Git Book (free)](https://git-scm.com/book/en/v2)
- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [GitHub Skills (interactive courses)](https://skills.github.com/)
- [Learn Git Branching (visual game)](https://learngitbranching.js.org/)
- [Oh Sh*t, Git!?! (recovering from mistakes)](https://ohshitgit.com/)
- [Git Cheat Sheet (PDF)](https://education.github.com/git-cheat-sheet-education.pdf)
- [Conventional Commits](https://www.conventionalcommits.org/)
