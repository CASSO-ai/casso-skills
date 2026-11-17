# Installing casso-skills

casso-skills is a folder of plain Markdown skills. There is nothing to build or run. Before you install, read [the README](README.md), above all [scaling the workflow](README.md#7-scaling-the-workflow).

## Steps

1. Get the casso-skills repository: clone it, or download it as an archive.
2. Copy the folders under `skills/` into the place your agent looks for skills. Copy all of them, or only the ones you want. Keep each folder whole, because `SKILL.md` and `RUBRIC.md` belong together.
3. Copy `GENERIC-RUBRIC.md` along with them. Reviewers use it for any skill without a rubric of its own.
4. Check that each copied `SKILL.md` still starts with its `name` and `description` lines. Your agent reads the description to decide when a skill applies.

## Where the skills go

| Tool | Where skills go |
|------|-----------------|
| Claude Code | `~/.claude/skills/` for all your projects, or `.claude/skills/` inside one project |
| Cursor | `.cursor/skills/` in your project, or your project's skills folder |
| Codex, Grok, GitHub Copilot, Antigravity, OpenCode | The skills folder set in that tool's configuration |

## Check it worked

Ask your agent to "use casso-skills-cr" on a one-line change. It should write a change request file and list open questions for you, rather than start writing code. Then try one full step by hand, as in [dispatching one step by hand](README.md#8-dispatching-one-step-by-hand).

## Updating

Copy the newer skill folders over the old ones. What changed in each version is in the repository's [Releases](../../releases).
