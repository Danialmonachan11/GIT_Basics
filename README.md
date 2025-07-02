# 🚀 Git Commands Reference Guide

Your complete reference for Git workflows - from beginner to everyday use!

## 📋 Table of Contents
- [Initial Setup](#-initial-setup)
- [Creating Repositories](#-creating-repositories)
- [Basic Workflow](#-basic-workflow)
- [GitHub Integration](#-github-integration)
- [Branching & Merging](#-branching--merging)
- [Viewing History](#-viewing-history)
- [Undoing Changes](#-undoing-changes)
- [Collaboration](#-collaboration)
- [Useful Tips](#-useful-tips)
- [Troubleshooting](#-troubleshooting)

---

## 🔧 Initial Setup

### First-time Git configuration
```bash
# Set your identity (do this once)
git config --global user.name "Your Name"
git config --global user.email "your.email@company.com"

# Optional: Set default editor
git config --global core.editor "code"  # For VS Code
git config --global core.editor "notepad"  # For Notepad (Windows)

# Check your configuration
git config --list
```

### SSH Setup for GitHub (Recommended)
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@company.com"

# Copy public key to clipboard (Windows)
type %USERPROFILE%\.ssh\id_ed25519.pub | clip

# Copy public key to clipboard (Mac/Linux)
cat ~/.ssh/id_ed25519.pub | pbcopy

# Then go to GitHub → Settings → SSH and GPG keys → New SSH key
```

---

## 📁 Creating Repositories

### Option 1: Start Locally, Add to GitHub Later
```bash
# Navigate to your project folder
cd my-project

# Initialize Git repository
git init

# Add all files
git add .

# First commit
git commit -m "Initial commit"

# Connect to GitHub (create repo on GitHub first)
git remote add origin https://github.com/USERNAME/REPO-NAME.git
git branch -M main
git push -u origin main
```

### Option 2: Clone from GitHub
```bash
# Clone existing repository
git clone https://github.com/USERNAME/REPO-NAME.git

# Clone to specific folder
git clone https://github.com/USERNAME/REPO-NAME.git my-folder-name

# Clone private repository
git clone https://github.com/USERNAME/PRIVATE-REPO.git
```

---

## ⚡ Basic Workflow

### Daily Git Commands
```bash
# Check status (what's changed)
git status

# See what's changed in files
git diff

# Add specific files
git add filename.py
git add folder/

# Add all changes
git add .

# Commit with message
git commit -m "Add new feature: anomaly detection"

# Add and commit in one step
git commit -am "Quick fix for bug"

# Push to GitHub
git push

# Pull latest changes from GitHub
git pull
```

### Staging Area Workflow
```bash
# See what's staged for commit
git status

# Unstage a file (remove from staging)
git reset filename.py

# Unstage all files
git reset

# Add only part of a file (interactive)
git add -p filename.py
```

---

## 🌐 GitHub Integration

### Creating GitHub Repository

#### Public Repository
```bash
# 1. Create repo on GitHub.com (don't initialize with README)
# 2. Connect your local repo
git remote add origin https://github.com/USERNAME/repo-name.git
git branch -M main
git push -u origin main
```

#### Private Repository  
```bash
# 1. Create repo on GitHub.com (check "Private" box)
# 2. Same commands as public
git remote add origin https://github.com/USERNAME/repo-name.git
git branch -M main
git push -u origin main
```

### Working with Remotes
```bash
# See remote repositories
git remote -v

# Add a remote
git remote add origin https://github.com/USERNAME/repo.git

# Change remote URL
git remote set-url origin https://github.com/USERNAME/new-repo.git

# Remove remote
git remote remove origin
```

---

## 🌿 Branching & Merging

### Basic Branching
```bash
# See all branches
git branch

# Create new branch
git branch feature-name

# Switch to branch
git checkout feature-name

# Create and switch in one command
git checkout -b feature-name

# Switch back to main
git checkout main

# Delete branch (locally)
git branch -d feature-name

# Delete branch (force)
git branch -D feature-name
```

### Merging
```bash
# Switch to main branch
git checkout main

# Merge feature branch into main
git merge feature-name

# Delete merged branch
git branch -d feature-name

# Push updated main to GitHub
git push
```

### Working with Remote Branches
```bash
# See all branches (including remote)
git branch -a

# Create local branch from remote
git checkout -b feature-name origin/feature-name

# Push new branch to GitHub
git push -u origin feature-name

# Delete remote branch
git push origin --delete feature-name
```

---

## 📜 Viewing History

### Commit History
```bash
# See commit history
git log

# See compact history
git log --oneline

# See last 5 commits
git log -5

# See history with file changes
git log --stat

# See visual branch history
git log --graph --oneline

# Search commits by message
git log --grep="bug fix"

# See changes by specific author
git log --author="Your Name"
```

### Viewing Changes
```bash
# See changes in last commit
git show

# See changes in specific commit
git show commit-hash

# See changes between commits
git diff commit1-hash commit2-hash

# See changes in a specific file
git log -p filename.py
```

---

## ↩️ Undoing Changes

### Undoing Uncommitted Changes
```bash
# Discard changes in specific file
git checkout -- filename.py

# Discard all uncommitted changes
git checkout -- .

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd
```

### Undoing Commits
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Undo last 3 commits (keep changes)
git reset --soft HEAD~3

# Revert a commit (creates new commit)
git revert commit-hash
```

### Fixing Mistakes
```bash
# Fix last commit message
git commit --amend -m "New commit message"

# Add forgotten file to last commit
git add forgotten-file.py
git commit --amend --no-edit

# Unstage file from last commit
git reset HEAD~1 filename.py
```

---

## 👥 Collaboration

### Getting Updates
```bash
# Get latest changes
git pull

# Fetch without merging
git fetch
git merge origin/main

# Update all branches
git fetch --all
```

### Handling Conflicts
```bash
# When merge conflicts occur:
# 1. Open conflicted files
# 2. Look for <<<<<<< markers
# 3. Edit to resolve conflicts
# 4. Remove conflict markers
# 5. Add resolved files
git add resolved-file.py
git commit -m "Resolve merge conflict"
```

### Stashing Changes
```bash
# Save work-in-progress
git stash

# Save with message
git stash push -m "Work on feature X"

# See stash list
git stash list

# Apply last stash
git stash pop

# Apply specific stash
git stash apply stash@{1}

# Delete stash
git stash drop stash@{1}
```

---

## 💡 Useful Tips

### Aliases (Make Git Easier)
```bash
# Set up useful shortcuts
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'

# Now you can use:
git st        # instead of git status
git co main   # instead of git checkout main
```

### Ignore Files
```bash
# Create .gitignore file
echo "*.log" >> .gitignore
echo "node_modules/" >> .gitignore
echo ".venv/" >> .gitignore

# Common .gitignore patterns:
*.log           # Ignore all .log files
*.tmp           # Ignore temporary files
.env            # Ignore environment files
__pycache__/    # Ignore Python cache
.DS_Store       # Ignore Mac system files
```

### Quick Commands
```bash
# See file changes since last commit
git diff HEAD filename.py

# See who changed what in a file
git blame filename.py

# Find when a bug was introduced
git bisect start

# See repository statistics
git shortlog -sn

# See remote repository info
git remote show origin
```

---

## 🆘 Troubleshooting

### Common Issues & Solutions

#### Authentication Problems
```bash
# If GitHub asks for password repeatedly:
git config --global credential.helper store

# Or use SSH instead of HTTPS
git remote set-url origin git@github.com:USERNAME/repo.git
```

#### "Your branch is ahead of origin/main"
```bash
# Push your commits
git push
```

#### "Your branch is behind origin/main"
```bash
# Pull latest changes
git pull
```

#### Accidentally committed to wrong branch
```bash
# Move last commit to correct branch
git checkout correct-branch
git cherry-pick main
git checkout main
git reset --hard HEAD~1
```

#### Accidentally committed large file
```bash
# Remove from last commit
git rm --cached large-file.zip
git commit --amend --no-edit

# Remove from repository history (use carefully!)
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch large-file.zip' --prune-empty --tag-name-filter cat -- --all
```

#### Reset to match GitHub exactly
```bash
git fetch origin
git reset --hard origin/main
```

---

## 🎯 Workflow Examples

### Feature Development Workflow
```bash
# 1. Start new feature
git checkout main
git pull
git checkout -b feature-user-authentication

# 2. Work on feature
git add .
git commit -m "Add login form"
git commit -m "Add password validation"

# 3. Push to GitHub
git push -u origin feature-user-authentication

# 4. Create Pull Request on GitHub

# 5. After PR is merged, cleanup
git checkout main
git pull
git branch -d feature-user-authentication
```

### Hotfix Workflow
```bash
# 1. Create hotfix branch from main
git checkout main
git pull
git checkout -b hotfix-critical-bug

# 2. Fix the bug
git add .
git commit -m "Fix critical security vulnerability"

# 3. Push and create urgent PR
git push -u origin hotfix-critical-bug

# 4. After merge, cleanup
git checkout main
git pull
git branch -d hotfix-critical-bug
```

### Release Workflow
```bash
# 1. Create release branch
git checkout main
git pull
git checkout -b release-v1.2.0

# 2. Update version numbers, finalize
git add .
git commit -m "Prepare release v1.2.0"

# 3. Create tag
git tag -a v1.2.0 -m "Release version 1.2.0"

# 4. Push tag
git push origin v1.2.0

# 5. Merge back to main
git checkout main
git merge release-v1.2.0
git push
```

---

## 📚 Quick Reference Card

```bash
# Setup
git init                    # Initialize repository
git clone <url>            # Clone repository

# Basic workflow  
git status                 # Check status
git add <file>            # Stage file
git add .                 # Stage all files
git commit -m "message"   # Commit changes
git push                  # Push to remote
git pull                  # Pull from remote

# Branching
git branch                # List branches
git checkout <branch>     # Switch branch
git checkout -b <branch>  # Create and switch
git merge <branch>        # Merge branch

# History
git log                   # View history
git diff                  # See changes
git show <commit>         # Show commit details

# Undo
git reset --soft HEAD~1   # Undo commit (keep changes)
git reset --hard HEAD~1   # Undo commit (discard changes)
git checkout -- <file>   # Discard file changes
```

---

**Keep this reference handy for all your Git needs!** 🚀

*Pro tip: Bookmark this file and refer to it whenever you need a quick Git command!* 
