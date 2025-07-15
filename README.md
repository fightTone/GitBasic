# Git Basics Training Guide

## Prerequisites
- Install Git on your computer: https://git-scm.com/downloads
- Create a GitHub account: https://github.com
- Configure Git with your name and email:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 1. Create a Repository for a Project

### Option A: Create on GitHub first (Recommended)
1. Go to GitHub.com and click "New" or the "+" icon
2. Enter repository name and description
3. Choose public or private
4. Check "Add a README file"
5. Click "Create repository"
6. Clone to your local machine:
```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### Option B: Create locally first
```bash
mkdir your-project-name
cd your-project-name
git init
```

## 2. Initialize and Push from Existing Project Folder

If you have an existing project folder:

```bash
# Navigate to your project folder
cd /path/to/your/existing/project

# Initialize git repository
git init

# Add all files to staging
git add .

# Create first commit
git commit -m "Initial commit"

# Add remote repository (create empty repo on GitHub first)
git remote add origin https://github.com/yourusername/your-repo-name.git

# Push to GitHub
git push -u origin main
```

**Note:** If you get an error about 'master' vs 'main', rename your branch:
```bash
git branch -M main
```

## 3. Push Changes

After making changes to your files:

```bash
# Check what files have changed
git status

# Add specific files
git add filename.txt
# OR add all changed files
git add .

# Commit with a descriptive message
git commit -m "Add new feature: user authentication"

# Push to remote repository
git push
```

**Push to specific branch:**
```bash
git push origin branch-name
```

## 4. Pull Changes

Get the latest changes from remote repository:

```bash
# Pull from current branch
git pull

# Pull from specific branch
git pull origin main
```

**Best practice:** Always pull before starting work to get latest changes.

## 5. Check Status

```bash
# See current status of your working directory
git status

# Shows:
# - Modified files
# - New files (untracked)
# - Files ready to commit (staged)
# - Current branch
```

## 6. Create a Branch

Branches allow you to work on features without affecting the main code:

```bash
# Create and switch to new branch
git checkout -b feature/new-login-system

# OR using newer syntax
git switch -c feature/new-login-system

# List all branches
git branch

# Switch between branches
git checkout main
git checkout feature/new-login-system

# Push new branch to remote
git push -u origin feature/new-login-system
```

## 7. Stash Changes

Temporarily save changes without committing:

```bash
# Save current changes to stash
git stash

# Save with a message
git stash save "Work in progress on login feature"

# List all stashes
git stash list

# Apply most recent stash
git stash pop

# Apply specific stash
git stash apply stash@{1}

# Delete a stash
git stash drop stash@{1}
```

## 8. Logs and Diff

### View commit history:
```bash
# Show commit history
git log

# Show compact log
git log --oneline

# Show last 5 commits
git log -5

# Show commits with file changes
git log --stat
```

### View differences:
```bash
# Show changes in working directory (unstaged)
git diff

# Show changes in staging area
git diff --staged

# Compare two commits
git diff commit1 commit2

# Show changes in specific file
git diff filename.txt
```

## 9. Create Pull Request / Merge Request

### On GitHub:
1. Push your branch to GitHub
2. Go to your repository on GitHub
3. Click "Compare & pull request" button
4. Add title and description
5. Select reviewers if needed
6. Click "Create pull request"

### Command line merge (for your own repos):
```bash
# Switch to main branch
git checkout main

# Pull latest changes
git pull

# Merge your feature branch
git merge feature/new-login-system

# Push merged changes
git push

# Delete feature branch (optional)
git branch -d feature/new-login-system
```

---

# Bonus: Host Static Website on GitHub Pages (Free)

## 1. Using index.html

### Method 1: Simple HTML site
1. Create a repository named `yourusername.github.io`
2. Add your `index.html` file to the root
3. Push to GitHub
4. Your site will be available at `https://yourusername.github.io`

### Method 2: Project site
1. In any repository, create a `docs` folder or use root
2. Add your HTML files (must have `index.html`)
3. Go to repository Settings → Pages
4. Select source: "Deploy from a branch"
5. Choose `main` branch and `/docs` folder (or root)
6. Your site will be at `https://yourusername.github.io/repository-name`

## 2. React Project

### Step 1: Prepare your React app
```bash
# In your React project folder
npm run build
```

### Step 2: Deploy using gh-pages
```bash
# Install gh-pages package
npm install --save-dev gh-pages

# Add to package.json scripts:
"homepage": "https://yourusername.github.io/repository-name",
"predeploy": "npm run build",
"deploy": "gh-pages -d build"

# Deploy
npm run deploy
```

### Step 3: Enable GitHub Pages
1. Go to repository Settings → Pages
2. Select source: "Deploy from a branch"
3. Choose `gh-pages` branch
4. Your React app will be live at the homepage URL

### Alternative: Manual deployment
```bash
# Build your React app
npm run build

# Copy contents of build folder to a gh-pages branch
# Or copy to docs folder in main branch and enable Pages from there
```

---

## Common Git Commands Quick Reference

```bash
git init                    # Initialize repository
git clone <url>            # Clone repository
git add <file>             # Stage file
git add .                  # Stage all files
git commit -m "message"    # Commit changes
git push                   # Push to remote
git pull                   # Pull from remote
git status                 # Check status
git log                    # View history
git diff                   # View changes
git branch                 # List branches
git checkout <branch>      # Switch branch
git merge <branch>         # Merge branch
git stash                  # Stash changes
git stash pop              # Apply stash
```

## Tips for Success
- Always use descriptive commit messages
- Pull before starting work
- Create branches for new features
- Don't commit sensitive information (passwords, API keys)
- Use .gitignore file to exclude unwanted files
- Commit small, logical changes frequently

## Getting Help
- `git help <command>` - Get help for specific command
- `git --help` - General help
- GitHub Documentation: https://docs.github.com