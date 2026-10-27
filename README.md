# qbash plugin

The qbash plugin for Claude and for ChatGPT and Codex. Both connect to the official qbash MCP server at `https://mcp.qbash.com/mcp`, where people sign in with their qbash account. The repository holds only the plugin manifests, a skill and the logo.

## Layout

| Folder | For | Submitted through |
| --- | --- | --- |
| `claude/` | Claude (chat, Cowork and Claude Code) | claude.ai/directory/manage, as a plugin bundle with the plugin path `claude` |
| `openai/` | ChatGPT and Codex | platform.openai.com/plugins, as a ZIP of the folder's contents |
| `.claude-plugin/marketplace.json` | Claude Code | `/plugin marketplace add qbashdev/qbash-plugin`, for installing before the directory listing is live |

The skill in `claude/skills/qbash/SKILL.md` and `openai/skills/qbash/SKILL.md` is the same file. Change both together.

## Install in Claude Code

```
/plugin marketplace add qbashdev/qbash-plugin
/plugin install qbash@qbash
```

## Build the OpenAI ZIP

```
cd openai && zip -r ../qbash-openai.zip . -x '.*' && cd ..
```

Upload `qbash-openai.zip` on platform.openai.com/plugins. Reviewer credentials and the demo video link go in the dashboard, never in this repository.

## Release a new version

1. Raise `version` in `claude/.claude-plugin/plugin.json` and `openai/plugin.json`.
2. Merge to `main`. The Claude directory picks up the new commit from the tracked branch.
3. Build a new OpenAI ZIP and upload it to the existing plugin.

Changes to the qbash tools themselves ship with the qbash server and need no new version here.
