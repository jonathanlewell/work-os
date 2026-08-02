---
type: note
topics:
  - connections
  - integrations
  - setup
organisations: []
people:
  - "[[Jonathan Lewell]]"
projects: []
created: 2026-08-02
updated: 2026-08-02
---

# Recommended Connections

The vault works without external services. For users who want connected work context, add these five connections in order.

## 1. Slack connector through Claude

Connect Slack through Claude to retrieve conversations, decisions and commitments without manually copying them into the vault.

Setup:

1. In Claude, open **Customize → Connectors**, or open **Connectors** from the plus menu in a chat.
2. Find Slack and connect the correct workspace.
3. Review the requested permissions and authenticate.
4. Record the exact workspace and permission boundary in [[System/connections|connections.md]].
5. Test a read-only search before relying on it.

Recommended boundary:

- allow searching and reading after a successful test;
- preserve stable message or thread references;
- confirm before sending, editing or scheduling messages;
- do not treat an informal Slack message as canonical truth when another record owns the fact.

## 2. Google Calendar connector through Claude

Connect Google Calendar directly through Claude for schedules, meeting preparation and date-aware planning.

Useful capabilities include:

- viewing events and accessible shared calendars;
- finding availability;
- preparing Meeting records with exact dates and participants;
- creating, updating or deleting events when explicitly approved.

Start with calendar retrieval. Confirm before creating, rescheduling, responding to or cancelling an event. Always preserve the event's timezone.

## 3. Gmail connector through Claude

Connect Gmail directly through Claude for email evidence, commitments and drafting.

Useful capabilities include:

- searching and reading messages;
- retrieving email metadata and thread context;
- creating drafts in Gmail;
- organising messages with labels when explicitly requested.

Claude's native Gmail connector can create drafts but does not send email. The user sends the final message from Gmail. Attachment metadata is available, but attachment contents are not directly exposed through the Gmail connector.

Start with search, reading and drafting. Confirm before changing labels, moving or deleting messages. Keep the source email as evidence rather than copying the entire mailbox into the vault.

## 4. Google Workspace CLI for multiple inboxes

When one-click Claude connectors are no longer enough, particularly when work spans multiple Google accounts or inboxes, progress to the command-line Google Workspace route:

[Google Workspace Extension for Gemini CLI](https://github.com/gemini-cli-extensions/workspace)

The extension covers Gmail, Calendar, Drive, Docs, Sheets and other Google Workspace services. It is more involved because it requires command-line installation, authentication and explicit account routing.

Use these safeguards:

- keep each Google account in a separately identifiable authentication context;
- verify which account is active before every consequential action;
- record each account and its route separately in [[System/connections|connections.md]];
- prove read-only retrieval for each account before enabling writes;
- review all send, delete, share and permission-changing actions;
- never place credentials in this vault.

The linked project describes itself as a Google Workspace extension for Gemini CLI. Confirm the intended runtime and multi-account behaviour during setup rather than assuming installation alone provides safe inbox switching.

## 5. Granola for meeting notes through MCP

Use Granola for meeting capture, then connect Granola to Claude or another supported agent through MCP. This lets the agent retrieve meeting notes without manual copying and pasting.

Setup:

- **Claude:** open **Settings → Connectors**, search for Granola, connect and authenticate, then enable it in the relevant conversation.
- **Claude Code, Cursor or another MCP client:** connect the official remote endpoint `https://mcp.granola.ai/mcp`.

Recommended workflow:

1. Granola captures and organises the meeting notes.
2. The agent retrieves the relevant note through Granola.
3. The agent creates or updates a Meeting record in `Meetings/` using `Templates/Meeting.md`.
4. Confirmed changes are reconciled into the relevant Project, People record or Organisation.
5. Tasks are written once in `Tasks.md`.

A transcript or AI-generated summary is evidence, not automatically current truth. Preserve uncertainty and do not silently overwrite canonical records.

Granola's published setup notes say Claude and ChatGPT connections require a paid plan. Enterprise availability may depend on an administrator enabling MCP for the workspace.

## Record each live connection

Use [[System/connections|connections.md]] to record:

- exact account or workspace;
- status;
- approved connector or command-line route;
- allowed read operations;
- actions requiring confirmation;
- last successful live test;
- known limitations.

Never store credentials, tokens, cookies, OAuth codes or secret-bearing URLs in the vault.

## Default permission boundary

| Capability | Default |
|---|---|
| Search and retrieve | Allowed after connection approval and a live test |
| Create a local draft | Allowed |
| Update canonical vault state | Only when evidence and ownership are clear |
| Send externally | Confirm first |
| Delete externally | Confirm first |
| Change permissions or configuration | Confirm first |

A connection answers **what the workspace can reach**. A skill answers **what repeatable outcome the agent should perform**.

## Sources and setup guides

- [Use connectors to extend Claude's capabilities](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities)
- [Use Google Workspace connectors in Claude](https://support.claude.com/en/articles/10166901-use-google-workspace-connectors)
- [Google Workspace Extension for Gemini CLI](https://github.com/gemini-cli-extensions/workspace)
- [Introducing Granola MCP](https://www.granola.ai/blog/granola-mcp)
