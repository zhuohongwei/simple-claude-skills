---
name: recommit
description: Reorganize the current branch's commits into clean, incremental, standalone commits that are easy to review
---
1. Detects the current git branch using `git rev-parse --abbrev-ref HEAD`
2. Determine the base branch (usually `main`) by finding the merge base
3. Read all commits on this branch since it diverged from the base branch using `git log` and `git diff` for each commit
4. Analyze the commits and plan a reorganization into clean, incremental, standalone commits where:
   - Each commit represents a single logical change
   - Each commit builds on the previous and compiles/works on its own
   - Commit messages are clear and descriptive
   - Related changes are grouped together (e.g. a refactor separate from a feature, tests with their implementation)
   - The final state of the code is identical to the current branch tip
5. Present the proposed commit plan to the user for approval before proceeding
6. Once approved, execute the reorganization:
   - Soft reset to the merge base: `git reset --soft <merge-base>`
   - For each planned commit, selectively stage the relevant files/hunks and commit with the planned message
   - Verify the final tree matches the original branch tip using `git diff <original-tip> HEAD` (should be empty)
7. Force push the reorganized branch: `git push --force-with-lease`
8. Slugify the current branch name
9. Check if there is an existing progress file named {slugified-current-branch-name}-progress.md in `docs/`
10. If the progress file exists, update it to reflect the new commit structure; if it doesn't exist, create one summarizing the reorganized commits
