# qbash

qbash builds and runs automations, called tasks. Describe a job in chat and qbash writes the task and saves it to your qbash account, where it can run on a schedule or when you ask. From the same conversation, Claude can run your tasks and read their results, and change a task later.

Claude can also search and update the memory folders you can access in qbash. Apps you connected in qbash, such as Google Drive or HubSpot, are available to Claude once you allow each account.

## What this plugin adds

- The qbash MCP server at `https://mcp.qbash.com/mcp`.
- A skill that explains to Claude how qbash tasks, memories and connected apps work together.

Claude sends each tool call to that address over HTTPS, and qbash runs the work on its own servers.

## Install in Claude Code

```
/plugin install qbash --marketplace qbashdev/qbash-plugin
```

## Before you start

You need a qbash account, and you can create one in the sign-in window. When you connect, qbash asks you to sign in and pick the organization Claude works in. Claude then has your own qbash permissions in that organization. You can remove its access at any time from Signed-in apps on your qbash MCP server page.

## Your data

Tool calls send qbash what you ask for: task descriptions and inputs, memory text, and the operations you run on connected apps. qbash keeps your tasks, runs and memories in your account. When a task or tool call uses a connected app, qbash calls that app with the account you connected. The [privacy policy](https://qbash.com/privacy) and [terms](https://qbash.com/terms) cover how qbash handles this data.

## Help

Ask Claude to contact qbash support, or reach the team at [qbash.com/contact](https://qbash.com/contact).
