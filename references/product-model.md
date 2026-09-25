# Official Grok Bot primitives

Do not invent fields. Encode only these unless the user documents a newer official capability.

| Primitive | What it is | Where it lives |
|---|---|---|
| Bot | Named durable teammate with its own conversation and compounding context | Sidebar; Edit Profile |
| Name | Short identity | Profile |
| Label / Title | One-line job headline | Profile |
| Description | Durable job + laws + approval boundary + schedule intent | Profile (load-bearing) |
| Instructions / chat law | Operational spec: workflow, rules, failure modes, output contract | Description + first messages / pinned habits |
| Avatar | Visual identity only | Profile |
| Shared cloud computer | Desktop, filesystem, terminal, browser, logins — shared across the user's bots, isolated per user | Always-on |
| Chat | Direct tasking | Conversation |
| Routines / triggers | Schedule (hourly/daily/weekday) or event (Slack, GitHub PR, new mail) | Bot routines |
| Skills | Saved multi-step paths, often from demonstration | Enabled skills |
| Plugins / connectors / MCP | Same family as Cursor; marketplace + custom MCP | Settings → Plugins |
| Group chat / DM between bots | Visible handoff surface | Multi-bot |
| Template | Recipe: identity, description, skills, routines, first-party plugins. Not a clone. No computer, logins, history, or custom scripts | Share → Create template |
| Approval boundary | What the Bot must not do without a human | Description |
| Duplicate | Copies profile, settings, skills, routines, avatar. Does **not** copy history, learned memory, attachments | Bot menu |

Facts that must stay true in every package:

- All of one user's Bots share one cloud computer (files, browser sessions, app logins).
- Hiding a Bot does not pause its routines.
- Work enters a Bot three ways: chat, routine/trigger, another Bot.
- Create a separate Bot when goal/ownership, tools/sources, working style, approval boundary, or recurring schedule is distinct.
- Templates are recipes. Strip API keys, internal URLs, customer data, private memory, custom scripts before share.
- Memory is not an authoritative source. Consequential decisions cite or reopen live data.
- Description holds durable law. Conversation holds this task.

Surface split:

- **Grok Bot** — cloud-computer teammates (this skill's default).
- **Grok Build** — terminal/repo coding agent (`AGENTS.md`, hooks, plugins, `grok -p`). A Grok Bot may *drive* it; do not put Grok Build fields on a Bot profile.
- **Public x.ai/bot assistant** — instruction-only, no computer. Label that surface explicitly.
