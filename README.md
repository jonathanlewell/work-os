# Welcome

Welcome to The Work OS.

It can sometimes be hard to get started with obsidian and creating an agent-friendly vault so I wanted to give you a vault that's easily set up and adopts the best practises of an agent-friendly vault ([[Principles of an Agent-Friendly Obsidian Vault]]).

The idea is that you store all of your notes within this vault as markdown .md files. They are all linked together and they give an agent like Claude or ChatGPT rich context to be able to answer your questions and serve you.

Think of this as a starting template that you can refine and improve over time.

## The Folders

| Place            | Use it for                                                                              |
| ---------------- | --------------------------------------------------------------------------------------- |
| `Organisations/` | Companies, clients, suppliers, partners, departments or institutions                    |
| `People/`        | People you work with and the context needed to work with them well                      |
| `Projects/`      | Outcomes with a finish line                                                             |
| `Notes/`         | Meetings, research, decisions, ideas, processes and other useful information            |
| `System/`        | Small operational files that describe how the vault works or connects to other services |
| `Templates/`     | One simple starting format for each record type                                         |
|                  |                                                                                         |

In an ideal world everything lives in one of these folders.

* When you have a meeting, you put the meeting record in the Notes/ folder.
* If you have a general note about history or documentation at work, you put that in the Notes/ folder.
* If you meet somebody, you put that information in the People/ folder
*  if you want to write about a client or hospital or nursery, you put that note within the Organisations/ folder

 At some point you may outgrow it and you may need to create new folders. That's totally okay. Just make sure that you update everything else

## The Templates

Within the Templates folder you'll see templates for the different .md files. Each record type has consistent front matter, and People records use the [[Templates/People]] template.

The main thing with working with agents is that you want to keep it as consistent as possible because agents prefer structured data rather than unstructured free-flowing text. This is why it's good to template records so they are consistent.

## How to Use the Vault with Claude/GPT

How to use it depends on if you're going with an agent or if you're going by hand but generally the principle is the same.

When you wanna create a new record, you create a new note, apply the template, and just fill it out. You ensure that it's linked to other relevant records in the front matter and also the body so that the agent can then see what records are linked to what.

To work with an AI, simply sit your Claude Code or Codex on top of the root vault folder. To take it further, you may also want to ask Claude/GPT to install [Obsidian skills](https://github.com/kepano/obsidian-skills) so that it can better read the relations between files and work with Obsidian in a native CLI way.

A simple way of doing this with Claude/Codex is to just narrate and say, "Create a new meeting note for my meeting with my manager, John." It should then create the relevant note following the template and link it to the correct organisation / projects etc.

## Example data

I've included some example records for you to see generally how it works. Explore [[Acme]], [[Alex Morgan]], [[Acme Website Launch]] and their linked example task in [[Tasks]].

## First use

1. Enable Obsidian's core **Templates** plugin. This enables you to save certain Markdown files as templates (the ones we have in the templates/ folder)
2. Add your tasks to [[Tasks]], using the `Now`, `Next`, `Waiting` and `Later` sections.
3. Create an Organisation using [[Templates/Organisation]].
4. Create a record for someone using [[Templates/People]] and link the relevant Organisation.
5. Create a Project using [[Templates/Project]] and link the relevant Organisations and People.
6. Use [[Templates/Note]] for everything else, including meeting notes.
7. If external services are connected, update [[System/connections|connections.md]] after a successful live test.

## How records connect

Use a double bracket like below to link to another record. You want to link records together to build the graph and let your agent know what is related to what. Records linked in the front matter are easily read by agents.

```yaml
organisations:
  - "[[Acme]]"
people:
  - "[[Alex Morgan]]"
projects:
  - "[[Acme Website Launch]]"
```

## Further guidance

- [[Principles of an Agent-Friendly Obsidian Vault]] explains how to keep files understandable and safe for both people and agents.
- [[Recommended Connections]] explains how to connect Slack, Google Calendar, Gmail, the Google Workspace CLI and Granola.
- [[System/connections|Connection Registry]] records which services this vault can actually reach now.
