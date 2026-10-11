---
description: List the jurisdictions NODE ID connects, optionally for one region or status
argument-hint: "[region: europe|gulf|apac|americas|africa|global] [status: live|stopgap|planned|research|not_connected]"
---

List the jurisdictions of the NODE ID catalogue with the `nodeid_list_jurisdictions` tool of the
`nodeid` MCP server, filtered by the region and the status in "$ARGUMENTS" when given.

Answer with a short table: code, name, region and status. Then say in one line what the statuses
mean (`live` through its own sources, `stopgap` through the rest-of-world manifest, `planned` or
`research` not yet, `not_connected` never served), and offer `nodeid_get_jurisdiction` for one of
them.

If the tool says `NODEID_API_KEY` is not set, explain that a person issues a sandbox key
(`nodeid_test_…`) in the client portal, `https://app.nodeid.co`, and sets it in the shell before
starting Claude Code. Never ask for the key in the conversation.
