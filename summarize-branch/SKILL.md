---
name: summarize-branch
description: Summarize the current branch's work into a permanent markdown document
---
1. Detect the current git branch using `git rev-parse --abbrev-ref HEAD`
2. Slugify the current branch name
3. Ensure the `docs/summaries/` directory exists
4. Create a summary file at `docs/summaries/{slugified-branch-name}_summary.md`
5. Summarize the branch's work with a focus on permanent documentation:
   - What was built or changed (features, fixes, refactors)
   - Key decisions made and their rationale
   - Important files or architecture affected
   - Any gotchas or lessons learned
6. Check if a transient progress file exists at `docs/{slugified-branch-name}_progress.md`
   - If it exists, ask the user if they want to delete it since the branch work is now summarized