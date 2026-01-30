## **Overview**

- **Git** tracks changes to files over time
- **GitHub** hosts repositories online
- **Repository** = project folder with `.git` directory
- **Commit** = saved snapshot of your files
- **Branch** = parallel version for working on features
- **Pull request** = request to merge a branch

**The daily workflow:**

```
git switch -c feature-name      # Create branch

# ... make changes ...
git add .                       # Stage changes
git commit -m "Description"     # Commit
git push                        # Push to GitHub

# Create PR on GitHub, merge, then:
git switch master
git pull
```

**When things break:**

```
git reset --hard origin/master    # Nuclear option
```

**Git has three states for your files:**

1. **Working directory** - Files as you edit them
2. **Staging area** - Changes you’re preparing to commit
3. **Committed** - Saved in Git history

```
Edit files → git add → git commit → git push
```

### **Create a new SSH key and add it to GitHub**

1. Go to [github.com](https://github.com/ "https://github.com/") → Sign in
2. Click your profile picture (top right) → **Settings**
3. Click **SSH and GPG keys** (left sidebar)
4. Click **New SSH key**
5. Title: “My Linux VM” (or whatever helps you remember)
6. Paste your public key
7. Click **Add SSH key**

### **Commit Message Tips**

- Keep them short (under 50 characters for the first line)
- Say **what** you did, not **how**
- Good: “Add user authentication”
- Bad: “Changed myscript lines 47-89”

Real teams often follow [Conventional Commits.](https://www.conventionalcommits.org/en/v1.0.0/ "https://www.conventionalcommits.org/en/v1.0.0/")

### **Why Use Branches?**

- `master` represents your working, stable code
- New features go in separate branches
- If the feature breaks, master is still fine
- Merge when the feature is ready and tested

```
git switch -c add-feature
```

### **Pull Requests**

A **pull request** (PR) is a request to merge your branch into master. It’s done on GitHub, not via Git commands.

(This is not completely true: you can review and merge Pull Requests using the GitHub CLI, but that is outside the scope of this course).

### **Why Pull Requests?**

- Code review - others can see and comment on your changes
- Discussion - have conversations about the implementation
- Quality control - don’t merge broken code
- History - see why changes were made

### **Create a Pull Request**

1. Go to your repository on GitHub
2. You’ll see a banner: “add-feature had recent pushes” with a **Compare & pull request** button
3. Click it
4. Add a title: “Add new feature section”
5. Add a description explaining what you did
6. Click **Create pull request**

### **Merge the Pull Request**

In a team, someone would review your code first. For now:

1. Click **Merge pull request**
2. Click **Confirm merge**
3. Click **Delete branch** (keeps things clean)

### **Definitions**

- **Repository (repo):** A project folder tracked by Git.
- **Commit:** A saved snapshot of your files at a point in time.
- **Branch:** A parallel version of your repository.
- **Master:** The primary branch representing stable code.
- **Remote:** A repository on a server (like GitHub).
- **Origin:** The default name for your GitHub remote.
- **Pull Request (PR):** A request to merge one branch into another.
- **Clone:** Download a complete copy of a repository.
- **HEAD:** Pointer to your current location in Git history.
