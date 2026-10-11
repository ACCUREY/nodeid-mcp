# Changelog

`@accurey/nodeid-mcp` follows the NODE ID API `v1` and its OpenAPI description, from which it ships
its documentation.

## 0.2.0 (2026-10-11)

The designer tools, and the Claude Code plugin `nodeid`.

- **Designer tools.** They return no company data.
  - `nodeid_list_jurisdictions` lists the jurisdictions NODE ID connects, with their status, from
    `GET /catalog/jurisdictions`.
  - `nodeid_get_jurisdiction` reads one jurisdiction's manifest from `GET /catalog/{jurisdiction}`:
    its identifiers, blocks, modes, prices and source health.
  - `nodeid_get_rules` gives the rules an integration follows, from the integration guide. With a
    jurisdiction, it adds that jurisdiction's legal rules.
  - `nodeid_example_snippet` writes a request to one operation in curl, TypeScript or Python,
    offline. The snippet reads the key from `NODEID_API_KEY` and sends an `Idempotency-Key` on every
    `POST`.
  - `nodeid_quote` prices a request, as before.
  - The jurisdictions, the manifest and a jurisdiction's rules are read on the sandbox with the
    sandbox key. The rules and the snippets need no key.
- **Claude Code plugin `nodeid`.** It installs from this repository's marketplace:
  `/plugin marketplace add ACCUREY/nodeid-mcp`, then `/plugin install nodeid@accurey`. It holds:
  - this MCP server, run from this release's tarball;
  - the skills `integrate-nodeid`, `design-nodeid-request` and `nodeid-webhooks`, which follow the
    integration guide;
  - the commands `/nodeid:jurisdictions` and `/nodeid:quote`.

## 0.1.2 (2026-10-11)

- **README**: the NODE ID logo at the top. No change to the server.

## 0.1.1 (2026-10-11)

- **README** rewritten for clients: quick start, environment variables, tools, security model and
  documentation links. No change to the server.

## 0.1.0 (2026-10-11)

The integration MCP of NODE ID.

- **Documentation, offline, without a key.** `nodeid_docs_search` searches the operations of the
  API and the integration guide for agents. `nodeid_docs_operation` describes one operation. Both
  are generated from the OpenAPI description. `nodeid_docs_guide` reads `agents.md`, whole or by
  section.
- **The sandbox only.** `nodeid_services`, `nodeid_resolve`, `nodeid_entity`, `nodeid_quote`,
  `nodeid_identity_verification_start` and `nodeid_identity_verification_get` call
  `https://sandbox.nodeid.co`, with the `nodeid_test_` key in `NODEID_API_KEY`.
- **Refused before anything is sent:** a live key, another host, a redirect, or a key in a tool's
  arguments. No answer repeats the key.
- **No person's fields.** A verification is read without the verified person's fields.
- **The resource `nodeid://agents.md`.**
- **Released on GitHub**, from the public repository `ACCUREY/nodeid-mcp`, as a tarball attached
  to the release `v0.1.0`: `npx -y https://github.com/ACCUREY/nodeid-mcp/releases/download/v0.1.0/accurey-nodeid-mcp-0.1.0.tgz`.
  No npm registry. The package has no dependency: the licences of the bundled packages are in
  `dist/THIRD_PARTY_LICENSES.md`.
- **MIT licence** (`LICENSE`), and a security policy (`SECURITY.md`).
