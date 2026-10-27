# Relier Mail plugin for Claude Code

This plugin connects Claude Code to Relier Mail. Claude can then read your Relier projects and email. It uses your own Claude subscription. The plugin is read-only. It cannot send, change, or delete email.

## Install

1. Add the marketplace: `claude plugin marketplace add d6u/relier-mail-claude-plugin`
2. Install the plugin: `claude plugin install relier-mail`
3. Run `/mcp` in Claude Code and select the authenticate option for `relier-mail`.

Sign-in uses OAuth in your browser. The plugin stores no password and no secret.

## Contents

| Item | Use |
| - | - |
| MCP server `relier-mail` | Connects to `https://mail-api.relier.ai/mcp` |
| Skill `relier-mail` | Guides Claude to use the tools in the correct order |

See the [connector documentation](https://github.com/d6u/relier-mail-claude-plugin#readme) for the tools, the limits, and the security notes.
