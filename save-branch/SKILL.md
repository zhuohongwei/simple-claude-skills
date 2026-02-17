---
name: save-branch
description: Save session context to a branch's progress markdown file
---
1. Detects the current git branch using `git rev-parse --abbrev-ref HEAD`
2. Slugify the current branch name  
3. Check if there is an existing markdown file named {slugified-current-branch-name}_progress.md in `docs/`.
4. If there isn't such a file, create one following the convention {slugified-current-branch-name}-progress.md.
5. Summarize the session's contents, determine which is relevant and critical for handing off a new session for seamless continuation, and add it to the file.