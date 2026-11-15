<p align="center">
  <a href="https://mojobase.ai/mcp?utm_source=github&utm_campaign=mcp-listing"><img src="https://mojobase.ai/logo.svg" alt="Mojobase" width="240"></a>
</p>

# Mojobase MCP server

**One MCP server for your whole business.** Connect ChatGPT, Claude, Cursor or your own agent once, and it works across your email, team chat, calendar, tasks, files, Handbook, customers and numbers, as you.

Ask "which customers owe us money, and what did we last tell them?" and your agent checks Numbers, Email and Customers in one go, then drafts the follow-up. With a server per app, that's three connections that never see each other.

> [!IMPORTANT]
> **You need a Mojobase account.** Mojobase is invite-only for now: [request a founding spot](https://mojobase.ai/signup?utm_source=github&utm_campaign=mcp-listing).

- **Address for claude.ai and ChatGPT:** `https://app.mojobase.ai/mcp/<your company>`, shown in Mojobase under Settings → Connect an agent
- **Address for a key:** `https://app.mojobase.ai/mcp`
- **Transport:** Streamable HTTP
- **Sign-in:** your Mojobase account, or a key sent as a Bearer token
- **Price:** included in every Mojobase plan, and agents never take a seat

## Who it's for

Owners and teams who run their business in Mojobase and want their own AI to do real work there: answer a customer, find a time, chase an invoice, keep the Handbook current. Your agent gets the same access you have, never more.

## Connect

Start in Mojobase: **Settings → Connect an agent**. It shows your company's address and makes keys. A key is shown once, and you can switch it off at any time.

### claude.ai and Claude Desktop

1. Copy your company's address from Settings → Connect an agent.
2. In Claude, open Customize → Connectors, click **+ Add**, then **Add custom connector**.
3. Name it Mojobase, paste the address and click **Continue**.
4. Sign in with your Mojobase account and allow access.

On Team and Enterprise plans, an owner adds the connector in Organization settings → Connectors first.

### ChatGPT

1. Copy your company's address from Settings → Connect an agent.
2. Go to [chatgpt.com/plugins](https://chatgpt.com/plugins), select **+**, then **Add custom MCP server**.
3. Name it Mojobase and paste the address under Connection.
4. Create it, then sign in with your Mojobase account when asked. In a chat, type @ and pick Mojobase.

In a Business or Enterprise workspace, your admin may need to allow custom MCP servers first.

### Claude Code

```sh
claude mcp add --transport http --scope user mojobase https://app.mojobase.ai/mcp --header "Authorization: Bearer YOUR_KEY"
```

### Codex

```sh
export MOJOBASE_KEY=YOUR_KEY   # in your shell profile
codex mcp add mojobase --url https://app.mojobase.ai/mcp --bearer-token-env-var MOJOBASE_KEY
```

### Cursor

Add Mojobase to `~/.cursor/mcp.json`, or to `.cursor/mcp.json` in a project:

```json
{
  "mcpServers": {
    "mojobase": {
      "url": "https://app.mojobase.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

### Any other MCP client

Use `https://app.mojobase.ai/mcp` over Streamable HTTP with the header `Authorization: Bearer YOUR_KEY`. A client that signs in with OAuth can use your company's address instead. Each request gets one JSON answer.

## What your agent can do

More than 115 tools, by app. An app you can't open, or one that's off for your company, doesn't show up.

**Email.** Search and read every mailbox you can see, attachments included. Write, revise and schedule drafts, put files on them and discard them. Sort conversations and set follow-ups. Archive, move, delete or mark mail as spam, and block or unblock senders, once you switch each on in Email Settings. Connect a Gmail or Outlook mailbox with a link for its owner.
`mail_accounts` `mail_sync` `mail_list` `mail_read` `mail_attachments` `thread_watch` `mail_label` `mail_tidy` `draft_new` `draft_revise` `draft_edit` `draft_attach` `draft_discard` `draft_schedule` `draft_list` `draft_send_test` `mail_connect_link`

**Team chat.** Read and search the conversations you're in, see what's waiting on you, post with files, reply, react and message a teammate. Edit or delete what your agent posted, make channels, and join open ones or add teammates to them. It never posts where a guest is.
`chat_conversations` `chat_read` `chat_search` `chat_needs_you` `chat_people` `chat_post` `chat_dm` `chat_react` `chat_edit` `chat_delete` `chat_channel_save` `chat_join` `chat_channel_add_people`

**Calendar.** List events, find good free times, add and change your own events, hold times you've offered, and read bookings. Make calendars and booking links, and write your meeting notes. A new booking link stays off until you switch it on. Teammates show as busy times only. A change with guests waits for your Approve.
`calendar_settings` `calendar_list` `calendar_find_times` `calendar_team` `calendar_save` `calendar_hold` `calendar_proposals` `calendar_bookings` `calendar_booking_links` `calendar_booking_link_save` `calendar_calendar_save` `calendar_notes` `calendar_note_save` `calendar_activity`

**Tasks.** List, add, update, complete, reopen and comment on tasks across your projects, and set your own reminders. Make and change projects and sections. Deleting a task, and sharing or deleting a project, always wait for your OK.
`tasks_list` `projects_list` `people_list` `task_add` `task_update` `task_complete` `task_comment` `task_remind` `task_delete` `task_history` `suggestions_list` `project_save` `section_save` `project_share` `project_delete`

**Files.** Search inside files and documents and read them. Suggest new documents, files and folders, edits, moves, renames, trash and putting things back from the trash, which you accept unless that kind of change is on Auto.
`docs_search` `docs_list` `docs_spaces` `docs_read` `doc_create` `doc_propose_edit` `items_propose_move` `items_propose_trash` `proposal_status` `docs_ai_settings`

**Handbook.** Read the business profile first, then search, read, write and move pages, start them from templates, archive and restore them, add collections, and set who looks after a page. Approving pages and publishing a site work only where you've let agents do them; deleting and settings go to you as a request.
`knowledge_business_profile` `knowledge_business_profile_update` `knowledge_outline` `knowledge_search` `knowledge_read` `knowledge_history` `knowledge_save_page` `knowledge_move_page` `knowledge_archive_page` `knowledge_create_collection` `knowledge_page_details` `knowledge_approve_page` `knowledge_publish_site` `knowledge_request_approval`

**Customers.** Find, add and update people and companies, and see who your mail and meetings found. Read website chats and support email, draft replies to website chats for you to send, and close, reopen or take them. An agent never deletes a person or company.
`customers_find_people` `customers_find_companies` `customers_save_person` `customers_save_company` `customers_found` `customers_chats` `customers_chat_draft` `customers_chat_status` `support_list` `support_status`

**Forms.** Write and change forms and read the responses. Only a person switches a form on.
`forms_list` `forms_write` `forms_update` `forms_switch` `forms_answers`

**Numbers.** Read sales, ad spend, campaigns, open invoices and bills, and Stripe invoices with their existing payment links, and, as an owner, refresh a source's figures. Note what was done to chase a late invoice. An agent can't create or send invoices, move money, or change a store or ad account.
`numbers_summary` `numbers_campaigns` `numbers_source` `numbers_items` `numbers_invoices` `numbers_invoice_note` `numbers_sync`

**Every app at once.** One search across mail, chat, events, files, tasks, customers and Handbook pages, ranked together. See what needs you and what changed in Activity, and undo a change your agent made.
`mojobase_search` `mojobase_needs_you` `mojobase_activity` `mojobase_undo`

**Your agents.** See your agents in Mojobase, draft a new one for you to set up and switch on, and pause one of yours.
`agents_list` `agent_draft` `agent_pause`

**Your team.** See who's in the company and, as an owner, invite and remove people, change roles and the apps a member opens, and make invite links. Nobody is emailed an invite until you press Send in Settings.
`team_list` `team_invite` `team_role` `team_remove` `team_link`

## What keeps your business safe

- **Your agent is you, never more.** It gets your role and only the apps you may open, checked on every request. Change your role and its tools change. Leave the company and its key stops working.
- **You choose Suggest or Auto.** Each kind of change either waits for your OK or happens at once, and each app's own rules still hold.
- **Every change is in Activity, with Undo.** Each call shows under your name with the agent and model that made it, and you can take a change back for as long as it can be undone.
- **AI off means off.** An agent can't read a mailbox, calendar or Files space with AI switched off, or a chat conversation you didn't give it. When it looks for a free time, those calendars still mark you busy, with no names or details.
- **Outside text is never an order.** What your agent reads in an email or a document is information, never an instruction.
- **A key opens the MCP server and nothing else.** It's shown once, and switching it off stops it at once.

## Learn more

- [One MCP server for your whole business](https://mojobase.ai/mcp?utm_source=github&utm_campaign=mcp-listing)
- [Bring your own AI agents](https://mojobase.ai/agents?utm_source=github&utm_campaign=mcp-listing)
- [Use Claude with your whole business](https://mojobase.ai/agents/claude?utm_source=github&utm_campaign=mcp-listing) and [ChatGPT](https://mojobase.ai/agents/chatgpt?utm_source=github&utm_campaign=mcp-listing)
- [Docs: connect your own agent](https://mojobase.ai/docs/connect-your-own-agent?utm_source=github&utm_campaign=mcp-listing)
- [Request a founding spot](https://mojobase.ai/signup?utm_source=github&utm_campaign=mcp-listing)

Questions: [hello@mojobase.ai](mailto:hello@mojobase.ai).

This repository holds this page and the server's entry in the official MCP Registry (`server.json`, listed as `ai.mojobase/mojobase`). The server itself runs at Mojobase and isn't open source. For agents and registries, its [server card](https://mojobase.ai/.well-known/mcp/server-card.json) says where and how to connect.
