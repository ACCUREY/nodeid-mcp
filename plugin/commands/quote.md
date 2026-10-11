---
description: Price a NODE ID request (jurisdiction, blocks, mode) on the sandbox, without running it
argument-hint: "<jurisdiction> <block> [block ...] [onboarding|verification]"
---

Price a NODE ID request with the `nodeid_quote` tool of the `nodeid` MCP server.

Read the jurisdiction code, the blocks and the mode from "$ARGUMENTS":

- the jurisdiction is a code such as `GB`, `FR`, `AE-AZ-ADGM`, or `ZZ` in the sandbox;
- the blocks are among `company`, `legalRepresentatives`, `shareholders`,
  `ultimateBeneficialOwners`, `formerBeneficialOwners`, `documents` and `filings`;
- the mode is `onboarding` unless `verification` is given.

When the jurisdiction or the blocks are missing, ask for them. When the code is unknown, look it up
with `nodeid_list_jurisdictions`.

Answer with the total in USD, each block with its price or the reason it would be refused, and
whether the request fits the application's budget. Then say in one line which mode was quoted and
that `verification` checks live at the source.

If the tool says `NODEID_API_KEY` is not set, explain that a person issues a sandbox key
(`nodeid_test_…`) in the client portal, `https://app.nodeid.co`, and sets it in the shell before
starting Claude Code. Never ask for the key in the conversation.
