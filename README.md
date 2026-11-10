# Biddle plugins

Biddle keeps a private list of the work you ask your coding agent for, and where each piece stands in GitHub. Only you see it. An item is done when GitHub shows it merged into the default branch, never because an agent said so.

## Claude Code

```sh
claude plugin marketplace add Liouville-Labs/claude-plugins
claude plugin install biddle@askbiddle
```

Then run `/biddle:setup` in Claude Code. The plugin bundles:

- Biddle's MCP server (`https://api.askbiddle.ai/mcp`); sign in from `/mcp`.
- The `biddle-work-tracking` skill: when your agent records a piece of work, and the rule that finished is not done.
- A hook (`bin/biddle-sync`) on `Stop`, `PreCompact` and `SessionEnd` that reports your branches with commits not in the default branch.

Update with `claude plugin update biddle@askbiddle`.

## Codex and Cursor

```sh
npx @askbiddle/agent-setup codex
npx @askbiddle/agent-setup cursor
```

## What the hook sends

For a repository whose `origin` is on github.com and in your workspace's GitHub installation: the repository name, the default branch, and for each local branch with commits not in it, the branch name, head sha, whether it was pushed, ahead and behind counts, the last commit date, and whether it is checked out. Never the transcript, file contents, diffs, commit messages or paths. The hook needs Node 18 or later and a personal access token with **Action items** (Biddle Settings > Agent access), saved by `biddle-sync --login` to `~/.config/biddle/credentials` (mode 0600).

[Privacy](https://askbiddle.ai/privacy) · [Terms](https://askbiddle.ai/terms)
