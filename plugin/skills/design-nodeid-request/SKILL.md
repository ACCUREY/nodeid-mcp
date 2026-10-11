---
name: design-nodeid-request
description: Design and price a NODE ID request before integrating it - which jurisdictions NODE ID connects, which blocks of company data a jurisdiction serves, in which mode, under which legal rules, and what a request costs. Use when the user asks what NODE ID covers in a country, which data it can read about a company there, or what a call will cost.
---

# Design a NODE ID request

The designer tools of the `nodeid` MCP server read the catalogue and the quote through the public
API, on the sandbox. They return no company data and bill nothing. The jurisdictions, the manifests
and the quotes need the sandbox key a person set as `NODEID_API_KEY`; never ask for it in the
conversation.

1. **The jurisdictions.** `nodeid_list_jurisdictions`, filtered by `region` or `status` when the
   user names one. The status says how NODE ID serves it:
   - `live`: through its own sources;
   - `stopgap`: through the rest-of-world manifest;
   - `planned` or `research`: not yet;
   - `not_connected`: under a sanctions regime, never served.
2. **One jurisdiction.** `nodeid_get_jurisdiction` with its code gives the manifest:
   - the identifiers a company is found by;
   - the blocks (`company`, `legalRepresentatives`, `shareholders`, `ultimateBeneficialOwners`,
     `formerBeneficialOwners`, `documents`, `filings`), with each block's freshness and gaps;
   - the selling prices for the calling application;
   - the health of the sources.
3. **The legal rules.** `nodeid_get_rules` with the jurisdiction gives the accesses each block
   needs (`public`, `legitimate_interest`, `obliged_entity`, `consent`, `agreement`), the resale
   policy, the licence and attribution of the register, and any due-diligence flag. A block the
   application may not read is refused, never served.
4. **The mode.** `onboarding` reads from the store within the block's freshness, and uses free or
   lite sources only. `verification` checks live at the source, and is the only mode that uses
   paid sources. Ask for `verification` only where the screen needs a live check.
5. **The price.** `nodeid_quote` with the jurisdiction, the blocks and the mode gives what the
   request would cost, each block with its reason when it would be refused, and whether it fits
   the application's budget. A company is priced once, at the highest tier asked: ask only for
   the blocks the screen needs.
6. **Hand over.** Summarise the jurisdictions, blocks, mode and price chosen. Then write the call
   with the `integrate-nodeid` skill: `nodeid_example_snippet` for `POST /resolve` and
   `GET /entities/{node_id}`, with those blocks and that mode.

In the sandbox, try the flow on the synthetic jurisdiction `ZZ`, whose companies are made up.
