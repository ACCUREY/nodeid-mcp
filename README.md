# @accurey/nodeid-mcp

The integration MCP of [NODE ID](https://api.nodeid.co/agents.md), Accurey's API for company and
beneficial-ownership data and for the verification of persons. It lets an AI agent integrate the
NODE ID API into an application from the documentation alone. It does two things:

- it searches the documentation it ships, offline and without a key: every operation of the API,
  its parameters and request body, and the integration guide for agents, `agents.md`;
- it calls the **sandbox**, `https://sandbox.nodeid.co`, and nothing else, with a sandbox key
  (`nodeid_test_…`) that a person sets in the server's environment.

It never reads production data and never takes a live key.

## Install

It needs Node.js 20 or later, and nothing else: the package has no dependency. Each release is a
tarball attached to a [GitHub release](https://github.com/ACCUREY/nodeid-mcp/releases) of this
repository; run it by its exact version:

```bash
npx -y https://github.com/ACCUREY/nodeid-mcp/releases/download/v0.1.0/accurey-nodeid-mcp-0.1.0.tgz
```

Add it to the agent's MCP configuration, for example `.mcp.json` for Claude Code:

```json
{
  "mcpServers": {
    "nodeid": {
      "command": "npx",
      "args": [
        "-y",
        "https://github.com/ACCUREY/nodeid-mcp/releases/download/v0.1.0/accurey-nodeid-mcp-0.1.0.tgz"
      ],
      "env": { "NODEID_API_KEY": "${NODEID_API_KEY}" }
    }
  }
}
```

The configuration names the variable; the key itself stays in the shell's environment, set by the
person who issued it in the client portal (`https://app.nodeid.co`, API keys, Test mode). Never
paste a key into a chat or a prompt. The MCP refuses any tool argument that looks like one, and
answers with the advice to revoke it. The documentation tools work without a key.

The package is not published to any npm registry: install it only from this repository's
releases.

## Tools

| Tool                                 | What it does                                                               | Key |
| ------------------------------------ | -------------------------------------------------------------------------- | --- |
| `nodeid_docs_search`                 | Searches the operations and the integration guide                          | no  |
| `nodeid_docs_operation`              | Describes one operation: parameters, request body, answers                 | no  |
| `nodeid_docs_guide`                  | Reads `agents.md`, whole or one section                                    | no  |
| `nodeid_services`                    | `GET /catalog/services`: the services and the application's subscriptions  | yes |
| `nodeid_resolve`                     | `POST /resolve`: ranked candidates (sandbox: jurisdiction `ZZ`)            | yes |
| `nodeid_entity`                      | `GET /entities/{node_id}`: the canonical view of a company                 | yes |
| `nodeid_quote`                       | `POST /quote`: the price of a request, without running it                  | yes |
| `nodeid_identity_verification_start` | `POST /identity/verifications`: a session and its hosted page              | yes |
| `nodeid_identity_verification_get`   | `GET /identity/verifications/{id}`: the outcome, without the person's data | yes |

The resource `nodeid://agents.md` is the integration guide. The API serves the same page at
`https://api.nodeid.co/agents.md`, and an index of its documentation at
`https://api.nodeid.co/llms.txt`.

The API gives an application no endpoint for its credit balance: the owners of the account read it
in the portal, and each answer says what it debited (`X-NodeID-Cost-USD`, `cost_usd` here).

## Guards

- **The sandbox only.** `NODEID_BASE_URL` may only be `https://sandbox.nodeid.co`, the default, or
  a local NODE ID (`http://localhost:…`). A live key (`nodeid_live_…`), another host, a URL with
  credentials or a path, and a redirect are refused before anything is sent.
- **No key in the conversation.** No tool takes a key. A tool argument that looks like a key is
  refused, and no answer repeats the key.
- **No personal data.** `nodeid_identity_verification_start` takes no contact details and no
  expected identity: send the person to the hosted page. `nodeid_identity_verification_get`
  withholds the verified person's fields, which the application's server reads.

## This repository

It holds the released files of the package: the bundle `dist/nodeid-mcp.js`, the licences of the
packages bundled in it (`dist/THIRD_PARTY_LICENSES.md`), this README, the changelog, the licence
and the security policy. Accurey builds and checks each release before it is published here; pull
requests are not merged into it.

## Security

Report a vulnerability privately, as [SECURITY.md](SECURITY.md) says. Never in a public issue.

## Licence

MIT, see [LICENSE](LICENSE). The licences of the bundled packages are in
`dist/THIRD_PARTY_LICENSES.md`.
