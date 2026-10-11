# Changelog

`@accurey/nodeid-mcp` follows the NODE ID API `v1` and its OpenAPI description, from which it ships
its documentation.

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
