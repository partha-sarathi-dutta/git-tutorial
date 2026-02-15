# 🚀 Git Tutorial - Complete Guide to Version Control Mastery

<div align="center">

![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)

**A comprehensive, production-ready guide to Git and version control workflows**

[Getting Started](#-getting-started) • [Core Concepts](#-core-concepts) • [Advanced Topics](#-advanced-topics) • [Best Practices](#-best-practices) • [Contributing](#-contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Why This Tutorial?](#-why-this-tutorial)
- [Getting Started](#-getting-started)
- [Core Concepts](#-core-concepts)
- [Essential Commands](#-essential-commands)
- [Branching Strategies](#-branching-strategies)
- [Advanced Topics](#-advanced-topics)
- [Best Practices](#-best-practices)
- [Common Workflows](#-common-workflows)
- [Troubleshooting](#-troubleshooting)
- [Resources](#-resources)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

This repository serves as a **comprehensive guide** to Git version control, designed for developers at all levels—from beginners taking their first steps to experienced engineers looking to master advanced workflows used at companies like Google, Microsoft, Meta, and Amazon.

### What You'll Learn

- ✅ Fundamental Git concepts and architecture
- ✅ Essential commands for daily development
- ✅ Professional branching strategies (Git Flow, GitHub Flow, Trunk-Based Development)
- ✅ Advanced techniques: rebasing, cherry-picking, bisecting
- ✅ Collaboration workflows and code review best practices
- ✅ Troubleshooting and recovery from common mistakes
- ✅ Performance optimization and repository management

---

## 💡 Why This Tutorial?

Unlike basic Git guides, this tutorial focuses on:

🎯 **Real-World Scenarios** - Learn through practical examples used in production environments  
🏗️ **Industry Standards** - Follow best practices from leading tech companies  
🔧 **Hands-On Approach** - Every concept includes executable examples  
📊 **Visual Learning** - Diagrams and illustrations for complex workflows  
🚀 **Career-Ready Skills** - Master the Git workflows used by professional teams

---

## 🚀 Getting Started

### Prerequisites

- Basic command-line knowledge
- Git installed on your system ([Download Git](https://git-scm.com/downloads))

### Installation Verification

```bash
# Check Git version
git --version

# Configure your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --list
```

### Your First Repository

```bash
# Initialize a new repository
git init my-project
cd my-project

# Create your first file
echo "# My Project" > README.md

# Stage and commit
git add README.md
git commit -m "Initial commit"
```

---

## 📚 Core Concepts

### The Three States

Git has three main states that your files can reside in:

1. **Modified** - You've changed the file but haven't committed it yet
2. **Staged** - You've marked a modified file to go into your next commit
3. **Committed** - The data is safely stored in your local database

```
Working Directory  →  Staging Area  →  Git Repository
     (Modified)         (Staged)        (Committed)
```

### The Git Workflow

```bash
# 1. Make changes to files (Working Directory)
echo "New feature" >> feature.txt

# 2. Stage changes (Staging Area)
git add feature.txt

# 3. Commit changes (Repository)
git commit -m "Add new feature"

# 4. Push to remote (Remote Repository)
git push origin main
```

---

## 🛠️ Essential Commands

### Repository Setup

```bash
# Clone an existing repository
git clone https://github.com/username/repository.git

# Initialize a new repository
git init

# Add a remote repository
git remote add origin https://github.com/username/repository.git
```

### Daily Workflow

```bash
# Check status
git status

# Add files to staging
git add <file>              # Add specific file
git add .                   # Add all changes
git add -p                  # Interactive staging

# Commit changes
git commit -m "Message"     # Commit with message
git commit -am "Message"    # Add and commit tracked files
git commit --amend          # Modify last commit

# View history
git log                     # Full history
git log --oneline           # Compact view
git log --graph --all       # Visual branch history
```

### Branching

```bash
# Create and switch branches
git branch feature-name     # Create branch
git checkout feature-name   # Switch to branch
git checkout -b feature     # Create and switch

# Modern syntax (Git 2.23+)
git switch feature-name     # Switch to branch
git switch -c feature       # Create and switch

# List branches
git branch                  # Local branches
git branch -a               # All branches
git branch -r               # Remote branches

# Delete branches
git branch -d feature       # Delete merged branch
git branch -D feature       # Force delete
```

### Merging and Rebasing

```bash
# Merge
git merge feature-branch    # Merge into current branch
git merge --no-ff feature   # Create merge commit

# Rebase
git rebase main             # Rebase current branch onto main
git rebase -i HEAD~3        # Interactive rebase last 3 commits

# Abort operations
git merge --abort
git rebase --abort
```

### Remote Operations

```bash
# Fetch and pull
git fetch origin            # Download remote changes
git pull origin main        # Fetch and merge
git pull --rebase origin main  # Fetch and rebase

# Push
git push origin main        # Push to remote
git push -u origin feature  # Push and set upstream
git push --force-with-lease # Safer force push
```

---

## 🌿 Branching Strategies

### Git Flow

**Best for:** Projects with scheduled releases

```
main (production)
  ↓
develop (integration)
  ↓
feature/* (new features)
release/* (release preparation)
hotfix/* (urgent fixes)
```

```bash
# Start a feature
git checkout -b feature/user-auth develop

# Finish a feature
git checkout develop
git merge --no-ff feature/user-auth
git branch -d feature/user-auth
```

### GitHub Flow

**Best for:** Continuous deployment

```
main (always deployable)
  ↓
feature/* (short-lived branches)
```

```bash
# Create feature branch
git checkout -b feature/add-login main

# Work, commit, push
git push -u origin feature/add-login

# Create Pull Request → Review → Merge → Deploy
```

### Trunk-Based Development

**Best for:** High-velocity teams (Google, Facebook)

```
main (trunk)
  ↓
short-lived feature branches (< 1 day)
```

```bash
# Small, frequent commits to main
git checkout -b quick-fix main
# Make changes
git commit -m "Fix: resolve login issue"
git push origin quick-fix
# Immediate PR and merge
```

---

## 🔥 Advanced Topics

### Interactive Rebase

```bash
# Rewrite last 5 commits
git rebase -i HEAD~5

# Options in interactive mode:
# pick   - use commit
# reword - edit commit message
# edit   - amend commit
# squash - combine with previous
# drop   - remove commit
```

### Cherry-Picking

```bash
# Apply specific commit to current branch
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick <hash1> <hash2>

# Cherry-pick without committing
git cherry-pick -n <hash>
```

### Stashing

```bash
# Save work in progress
git stash
git stash save "WIP: feature description"

# List stashes
git stash list

# Apply stash
git stash apply           # Keep stash
git stash pop             # Apply and remove

# Apply specific stash
git stash apply stash@{2}
```

### Bisect (Binary Search for Bugs)

```bash
# Start bisecting
git bisect start
git bisect bad           # Current commit is bad
git bisect good <hash>   # Known good commit

# Git will checkout commits for testing
# After each test:
git bisect good          # or
git bisect bad

# Finish
git bisect reset
```

### Submodules

```bash
# Add submodule
git submodule add https://github.com/user/repo.git path/to/submodule

# Clone with submodules
git clone --recursive <repo-url>

# Update submodules
git submodule update --init --recursive
```

---

## ✨ Best Practices

### Commit Messages

Follow the **Conventional Commits** specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples:**

```bash
git commit -m "feat(auth): add OAuth2 login support"
git commit -m "fix(api): resolve null pointer in user endpoint"
git commit -m "docs(readme): update installation instructions"
```

### Branch Naming

```bash
# Feature branches
feature/user-authentication
feature/payment-integration

# Bug fixes
fix/login-error
bugfix/memory-leak

# Hotfixes
hotfix/critical-security-patch

# Releases
release/v1.2.0
```

### .gitignore Best Practices

```gitignore
# Dependencies
node_modules/
vendor/

# Build outputs
dist/
build/
*.exe

# Environment files
.env
.env.local

# IDE files
.vscode/
.idea/
*.swp

# OS files
.DS_Store
Thumbs.db

# Logs
*.log
logs/
```

### Security

```bash
# Never commit sensitive data
# If you accidentally commit secrets:

# Remove from history
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch path/to/secret" \
  --prune-empty --tag-name-filter cat -- --all

# Modern alternative (faster)
git filter-repo --path path/to/secret --invert-paths

# Force push (coordinate with team!)
git push origin --force --all
```

---

## 🔄 Common Workflows

### Feature Development

```bash
# 1. Update main branch
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b feature/new-dashboard

# 3. Work and commit
git add .
git commit -m "feat(dashboard): add user analytics"

# 4. Keep branch updated
git fetch origin
git rebase origin/main

# 5. Push and create PR
git push -u origin feature/new-dashboard
```

### Code Review Process

```bash
# Reviewer: Checkout PR branch
git fetch origin pull/123/head:pr-123
git checkout pr-123

# Test changes
npm test

# Request changes or approve
# Author: Address feedback
git add .
git commit -m "fix: address review comments"
git push origin feature/new-dashboard
```

### Release Process

```bash
# 1. Create release branch
git checkout -b release/v1.2.0 develop

# 2. Update version numbers
# Edit package.json, version files, etc.
git commit -am "chore: bump version to 1.2.0"

# 3. Merge to main
git checkout main
git merge --no-ff release/v1.2.0
git tag -a v1.2.0 -m "Release version 1.2.0"

# 4. Merge back to develop
git checkout develop
git merge --no-ff release/v1.2.0

# 5. Push everything
git push origin main develop --tags
```

---

## 🆘 Troubleshooting

### Undo Changes

```bash
# Discard working directory changes
git checkout -- <file>
git restore <file>          # Modern syntax

# Unstage files
git reset HEAD <file>
git restore --staged <file> # Modern syntax

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert a commit (create new commit)
git revert <commit-hash>
```

### Resolve Merge Conflicts

```bash
# When merge conflict occurs:
# 1. Check conflicted files
git status

# 2. Open files and resolve conflicts
# Look for markers: <<<<<<<, =======, >>>>>>>

# 3. Stage resolved files
git add <resolved-file>

# 4. Complete merge
git commit
```

### Recover Lost Commits

```bash
# View reflog (history of HEAD)
git reflog

# Recover lost commit
git checkout <commit-hash>
git cherry-pick <commit-hash>

# Recover deleted branch
git checkout -b recovered-branch <commit-hash>
```

### Clean Repository

```bash
# Remove untracked files (dry run)
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Remove ignored files too
git clean -fdx
```

---

## 📖 Resources

### Official Documentation
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

### Interactive Learning
- [Learn Git Branching](https://learngitbranching.js.org/)
- [Git Immersion](http://gitimmersion.com/)
- [Visualizing Git](http://git-school.github.io/visualizing-git/)

### Books
- **Pro Git** by Scott Chacon (Free online)
- **Git Pocket Guide** by Richard E. Silverman
- **Version Control with Git** by Jon Loeliger

### Cheat Sheets
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-addition`)
3. **Commit** your changes (`git commit -m 'feat: add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-addition`)
5. **Open** a Pull Request

### Contribution Guidelines

- Follow the existing code style
- Write clear commit messages (Conventional Commits)
- Add examples for new concepts
- Update documentation as needed
- Test your changes thoroughly

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🌟 Acknowledgments

- Git community for excellent documentation
- Contributors who help improve this tutorial
- Developers worldwide who make open source amazing

---

<div align="center">

**Made with ❤️ for developers by developers**

⭐ **Star this repo** if you found it helpful!

[Report Bug](https://github.com/partha-sarathi-dutta/git-tutorial/issues) • [Request Feature](https://github.com/partha-sarathi-dutta/git-tutorial/issues) • [Discussions](https://github.com/partha-sarathi-dutta/git-tutorial/discussions)

</div>