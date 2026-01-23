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

## Notes

WIP
