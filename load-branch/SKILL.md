---
name: load-branch
description: Loads context from a branch's progress markdown file
---
1. Detects the current git branch using `git rev-parse --abbrev-ref HEAD`
2. Slugify the current branch name  
3. Check if there is an existing markdown file named {slugified-current-branch-name}_progress.md in `docs/`. 
4. If there is such a file, read it and load it into context.