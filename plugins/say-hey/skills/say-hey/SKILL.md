---
name: say-hey
description: Use when the user asks about their own text messages or the people in them — a person by name, what they promised or owe, who they should reply to or reconnect with, when they last talked to someone, plans, birthdays, deadlines, or "who do I know at…". Say hey answers from the user's local iMessage history with the real message as evidence.
---

# Say hey

Say hey is a macOS app that indexes the user's iMessage history on their Mac and
exposes it as tools. Every answer it gives is backed by a real message. Use it
whenever the question is about the user's people or their conversations; do not
guess at what someone said when you can look it up.

## Which tool

**Who is this person**
- `find_contact` — resolve a name to the person behind it, with a quick dossier (birthday, job, family). Start here when a name is mentioned.
- `people_by_topic` — find the people associated with a topic across the message history.
- `contacts_by_fact` — find the contacts matching a given fact (company, spouse, kid, hometown).
- `closest_contacts` — the people the user is closest to right now.
- `longest_known` — the people the user has known the longest.

**What the user owes, or is owed**
- `open_follow_ups` — what the user owes or is owed; optionally scoped to one person. The answer to "what did I promise", "who do I owe a reply", "what did I drop".
- `drifting_contacts` — people who've gone quiet relative to their own rhythm — "it's been a while".
- `quiet_contacts` — people the user has lost touch with, past an absolute day cut.

**Find a message**
- `search_messages` — full-text search across all messages, ranked by who matters.
- `search_in_thread` — search inside one person's conversation.
- `messages_in_period` — messages within a date range.
- `recent_messages` — the most recent messages, overall or with one person.
- `query_messages` — a read-only SQLite SELECT over curated message views, for anything the other tools can't express.

**Context on a relationship**
- `relationship_brief` — a short brief on the state of a relationship.
- `contact_facts` — facts learned about a contact (job, family, hometown, hobby).
- `group_chat` — find and read a group chat by its title or by member names.
- `shared_links` / `shared_media` — links, photos and media shared in a conversation.

**What's coming up**
- `upcoming_plans` — plans, deadlines and travel on the near horizon (about 45 days).
- `upcoming_birthdays` — whose birthday is coming up.

## Rules

1. **Cite the message.** Quote the actual text and its date for every claim. The value of Say hey is the receipt, not the summary.
2. **Never invent a follow-up.** If the tools don't return it, it isn't there. Say so.
3. **If a call fails with "Say hey isn't reachable"**, tell the user to open Say hey and switch Connect on, then stop. Don't retry or guess.
4. **Privacy.** Say hey runs on the user's Mac and answers from it. Don't send message contents anywhere the user hasn't asked you to.
