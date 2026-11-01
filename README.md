# Tier 1 Protocol — Connector for Bolt

Tier 1 Protocol is a library your AI searches instead of guessing from. Documents are cut into records, each one sealed with SHA-256 at its exact byte address, and served through a single MCP door: your agent asks, the door returns the exact passages — and the proof recomputes on every fetch.

## Add it to Bolt (about a minute)

1. From the Bolt homepage, click the **+** by the chat box → **Connectors** → **Manage connectors** → **Custom MCP server**.
2. Fill in exactly:
   - **Name:** `Tier 1 Protocol`
   - **URL:** `https://kjvxatpuprlhohufdmwb.supabase.co/functions/v1/mcp`
   - **Transport:** `HTTP`
   - **Authentication:** `None`
3. Back in your project, toggle **Tier 1 Protocol** on.
4. Ask your agent: *"Using Tier 1, search the starter library: what happened in this account between 23:41 and 00:19?"*

The agent should answer from the sealed records and cite record addresses. One record in the starter library — ticket-0007 — fails its verification check on purpose. That's the receipt doing its job: a record that doesn't check out gets flagged, not smoothed over.

## The tools

Bolt discovers these from the server at connect time:

| Tool | What it does |
| --- | --- |
| `authorize_sources` | Lists the sources your agent may search |
| `search` | Finds the records that answer a question |
| `fetch` | Retrieves a record by address and re-verifies its seal |
| `render_context_results` | Renders search results as context your agent can use |

## The starter library

Every Tier 1 account begins with the same starter library: the Northpine sample — 282 records across 9 documents, sealed at revision `6bf3c9cb1af2`. It's small on purpose. Ask it the 23:41 question and watch the whole loop — search, fetch, verify — run on material you can check by hand.

## Your own library

Build your library in your browser at **[tier-1-protocol-kfn8.bolt.host](https://tier-1-protocol-kfn8.bolt.host)** — your files are cut and sealed on your machine, and the door is what you pay for:

- **$19/month** for door access, or
- a **3-day free trial**, no card, if you want to watch it work first.

The paywall is the door, not the app.

## Notes

- Connectors serve Bolt **build sessions** — that's where the agent calls the door. A published app that needs Tier 1 at runtime calls the same endpoint from its own code, like any external service.
- The starter library is public, which is why Authentication is `None`. Your own library is fenced to your account.
- This repository is the setup sheet only. There is no product code in it.

---

© 2026 Tyler Brassel · Tier 1 Protocol · [tier1protocol.network](https://tier1protocol.network)
