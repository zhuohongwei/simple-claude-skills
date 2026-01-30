# claude-skills

My experiment with writing claude skills that might be useful.

## Available Skills

| Skill | Description |
|-------|-------------|
| `load-branch` | Loads context from a branch's progress markdown file |
| `save-branch` | Saves session context to a branch's progress file for seamless continuation |
| `summarize-branch` | Creates a permanent summary of the branch's work when complete |

## Installation
- Copy the skill folders into `~/.claude/skills` directory
- Restart claude cli if needed
- Try asking claude to `save branch` prior to ending a session. It should pick up the save-branch skill automatically.