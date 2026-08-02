# Connections

This is the live connection registry for the vault. It records what the workspace can reach, through which approved route and with which permission boundary.

This is useful because sometimes if you set up connections to different tools, you need to keep a record of how you are connecting to those tools. Whether it's by a CLI or an MCP or a connection directly through Claude or GPT, etc., it needs to be documented, especially if you don't want to have to keep reminding your agent how to connect to these tools.

Read [[Recommended Connections]] for my initial connections. The recommended order is Slack, Google Calendar, Gmail, the advanced Google Workspace CLI route and Granola.

## Status meanings

- **Ready:** authenticated and successfully tested for the stated account or workspace.
- **Setup required:** recommended but not yet authenticated or tested.
- **Optional:** add only when the advanced capability is needed.
- **Unavailable:** considered but currently blocked, disabled or unsupported.

Documentation alone does not make a connection Ready. Record a successful live test without storing credentials or private configuration values.

## Registry

| Connection | Purpose | Account or workspace | Status | Approved route | Allowed without confirmation | Confirm before | Last verified | Notes |
|---|---|---|---|---|---|---|---|---|
| Slack | Retrieve decisions, commitments and discussion context |  | Setup required | Slack connector through Claude | Search and read after a live test | Sending, editing or scheduling messages; changing workspace settings |  | Record the exact Slack workspace and preserve stable message references |
| Google Calendar | Retrieve events and support meeting workflows |  | Setup required | Google Calendar connector through Claude | Search and read after a live test | Creating, moving, responding to or cancelling events |  | Preserve timezone and exact account scope |
| Gmail | Retrieve email evidence and create drafts |  | Setup required | Gmail connector through Claude | Search, read and draft after a live test | Label, move or delete actions; any alternative route that can send |  | Claude's native connector drafts but does not send; attachment content is not directly available |
| Google Workspace CLI | Advanced Workspace access and explicit multi-account routing |  | Optional | [Google Workspace Extension for Gemini CLI](https://github.com/gemini-cli-extensions/workspace) | Read-only operations after each account is tested | Sending, deleting, sharing, permission changes or switching account context |  | Record each Google account separately and verify the active account before acting |
| Granola | Retrieve meeting notes and summaries |  | Setup required | Granola connector through Claude or `https://mcp.granola.ai/mcp` | Search and retrieve after a live test | Recording, sharing, deleting or automatically reconciling canonical vault state |  | Meeting notes are evidence, not automatically current truth |

## Rules

1. Record the exact account or workspace scope before marking a connection Ready.
2. Record the canonical route and any documented fallback.
3. Separate read permission from write permission.
4. Require confirmation for external sends, deletions, permission changes and configuration changes.
5. Never store passwords, API keys, tokens, cookies, OAuth codes or secret-bearing URLs here.
6. Update `Last verified` only after a real live test.
7. Record each Google account as a separate row when using multiple inboxes.
8. Keep broad setup guidance in [[Recommended Connections]]; keep this file focused on actual connection state.
