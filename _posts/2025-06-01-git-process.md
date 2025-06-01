---
title: "Git Process"
date: 2025-06-01
categories: [Git, Software Development]
tags: [Version Control]
layout: single
---

# Mastering Git Workflow and Commands for Beginners

Git is a powerful tool for version control, allowing developers to track changes, collaborate efficiently, and manage codebases effectively. Whether you're working on a personal project or collaborating with a team, understanding a structured Git workflow is essential. In this guide, I'll walk you through a step-by-step Git workflow for managing branches and commits, followed by how to set up a new project in Replit or VS Code using a GitHub repository. I'll also consolidate key Git commands for quick reference.

## Step 1: Setting Up a New Project in your IDE (VS code or others) from a GitHub Repo

VS Code is a fantastic platform for coding in the browser, and connecting it to a GitHub repository makes version control seamless. Here's how to set up a new project in Replit from a GitHub repo.

### Create a GitHub Repository

1. Go to GitHub and create a new repository
2. Mark it private if desired, add a description, and invite collaborators under Settings > Collaborators
3. Initialize it with a README or leave it empty for now

### Set Up Replit

In your VS code project, open the shell (Ctrl+back-tick) and run these commands to initialize Git and connect to your GitHub repo:

```bash
git init
git config --global user.name "<your-github-username>"
git config --global user.email "<your-github-email>"
git add .
git commit -m "Initial commit"
git remote add origin https://<your-PAT>@github.com/<username>/<repository>.git
git push -u origin main
```

- Replace `<your-PAT>` with a Personal Access Token from GitHub (Settings > Developer settings > Personal access tokens > Generate new token)
- Replace `<username>` and `<repository>` with your GitHub username and repo name

### Verify on GitHub

Refresh your GitHub repository page to confirm the main branch and files are pushed.

**Tip:** Generate a PAT with repo scope for full access. Store it securely, as it acts like a password.

## Step 2: Setting Up a New Feature Branch

When working on new functionality, always create a dedicated branch to keep your changes isolated from the main codebase. This ensures the main branch remains stable while you experiment or develop.

### Switch to the Main Branch

Start by ensuring you're on the main branch, which typically holds the latest stable code:

```bash
git checkout main
```

### Fetch and Merge Updates

Pull the latest changes from the remote repository to keep your local main branch up to date:

```bash
git fetch origin main
git merge origin/main
```

### Create a New Branch

Create a branch for your new feature, replacing `<new-branch-name>` with a descriptive name (e.g., `add-login-page`):

```bash
git checkout -b <new-branch-name>
```

This workflow ensures your new branch starts with the latest code from main, avoiding conflicts later.

## Step 3: Committing Changes Regularly

As you work on your feature, commit significant changes to your local branch. Regular commits make it easier to track progress and revert mistakes if needed.

### Commit Changes

After making changes, commit them with a clear message describing what you did:

```bash
git commit -m "Add user authentication endpoint"
```

**Tip:** Write concise, meaningful commit messages (e.g., "Fix login form validation") to make your project history clear and professional.

## Step 4: Syncing with Remote Daily

To avoid conflicts and stay aligned with team changes, sync your branch with the remote main branch at the start of each workday.

### Commit Your Work

Save any local changes to your branch:

```bash
git commit -m "Update login form styling"
```

### Fetch and Merge Updates

Pull the latest changes from main and merge them into your branch:

```bash
git fetch origin main
git merge origin/main
```

### Resolve Conflicts

If conflicts arise, Git will pause the merge and highlight conflicting files. Open these files, resolve the conflicts manually, then stage and commit the resolved changes:

```bash
git add .
git commit -m "Resolve merge conflicts"
```

### Test Functionality

Always test your code after merging to ensure nothing breaks.

This daily sync keeps your branch up to date and minimizes merge issues when you're ready to submit your work.

## Step 5: Pushing Changes and Cleaning Up

Before pushing your branch to the remote repository, ensure it's up to date with main. After pushing, create a pull request (PR) and clean up your local branches.

### Commit and Sync

Commit any final changes, then fetch and merge updates from main:

```bash
git commit -m "Complete login feature"
git fetch origin main
git merge origin/main
```

### Resolve Conflicts and Test

As before, resolve any conflicts and verify your code works.

### Push Your Branch

Stage all changes, commit, and push your branch to the remote repository:

```bash
git add .
git commit -m "Final changes for login feature"
git push --set-upstream origin <new-branch-name>
```

### Create a Pull Request

Go to your GitHub repository, navigate to the Pull Requests tab, and create a PR for your branch. Avoid merging it yourself—let a team member review it.

### Clean Up Locally

After the PR is merged, switch to main, delete your feature branch, and update main:

```bash
git checkout main
git branch -d <new-branch-name>
git fetch origin main
git merge origin/main
```

### Start a New Branch (Optional)

If you're starting another feature, create a new branch:

```bash
git checkout -b <another-branch-name>
```

**Note:** Use `git branch -D <branch-name>` to force-delete a branch if it has unmerged changes.


## Step 6: Essential Git Commands Cheat Sheet

Here's a consolidated list of key Git commands for quick reference:

### Branch Management

**Switch Branches:**
```bash
git checkout <branch-name>
```

**Create and Switch to a New Branch:**
```bash
git checkout -b <branch-name>
```

**Check Current Branch:**
```bash
git branch
```

### Working with Changes

**Check Unstaged Changes:**
```bash
git status
```

**Stage All Changes:**
```bash
git add .
```

**Commit Changes Locally:**
```bash
git commit -m "Your commit message"
```

### Remote Operations

**Push to Remote (First Time):**
```bash
git push --set-upstream origin <branch-name>
```

**Subsequent Pushes:**
```bash
git push origin <branch-name>
```

**Remove a Remote:**
```bash
git remote remove origin
```

**Add a New Remote:**
```bash
git remote add origin https://<PAT>@github.com/<username>/<repository>.git
```

**Verify Remote:**
```bash
git remote -v
```

### Utility Commands

**Rename Branch to main:**
```bash
git branch -M main
```

**Get Help:**
```bash
git --help
```

**Store Credentials:**
```bash
git config credential.helper store
```

**Stash Changes:**
```bash
git stash <file>
```

**Remove File from Repo:**
```bash
git rm <file>
```

**Apply Latest Stash:**
```bash
git stash pop
```

**Fetch from Remote Branch:**
```bash
git fetch origin <branch-name>
```

**Merge Fetched Data:**
```bash
git merge origin/<branch-name>
```

## Final Thoughts

Mastering Git workflows is a game-changer for developers. By creating feature branches, committing regularly, syncing with the remote repository, and cleaning up after merging, you'll maintain a clean and collaborative codebase. Integrating Git with VS code further simplifies development by letting you code and manage version control in one place. Use the cheat sheet above as a quick reference, and soon, these commands will become second nature.

Happy coding, and let me know in the comments if you have questions or tips to share!