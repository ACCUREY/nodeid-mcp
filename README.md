<p align="center">
  <img src="https://nodedb.nodehq.co/storage/v1/object/public/images/node-id-logo.png" alt="NODE ID logo" width="320"/>
</p>

<h1 align="center">NODE ID — Integration MCP</h1>

<p align="center">
  <strong>Let an AI agent integrate the NODE ID API from its documentation and its sandbox</strong>
</p>

<p align="center">
  <em>Company & Beneficial-Ownership Data • Identity Verification • AML Screening — by Accurey</em>
</p>

---

<p align="center">
  <!-- Release & status -->
  <img src="https://img.shields.io/github/v/release/ACCUREY/nodeid-mcp?style=for-the-badge&label=release&color=blue" alt="Latest release"/>
  <img src="https://img.shields.io/badge/status-Public%20Beta-success?style=for-the-badge" alt="Status"/>
  <img src="https://img.shields.io/badge/license-MIT-green?style=for-the-badge" alt="MIT licence"/>
  <img src="https://img.shields.io/badge/MCP-server-191919?style=for-the-badge" alt="Model Context Protocol server"/>
</p>

<p align="center">
  <!-- Ownership -->
  <img src="https://img.shields.io/badge/Publisher-Accurey%2C%20Inc.-navy?style=flat-square" alt="Publisher"/>
  <img src="https://img.shields.io/badge/Product-NODE%20ID-darkblue?style=flat-square" alt="Product"/>
  <img src="https://img.shields.io/badge/API-v1-blue?style=flat-square" alt="API v1"/>
</p>

<p align="center">
  <!-- Tech stack -->
  <img src="https://img.shields.io/badge/Node.js-%E2%89%A5%2020-339933?style=flat-square&logo=nodedotjs&logoColor=white" alt="Node.js 20 or later"/>
  <img src="https://img.shields.io/badge/TypeScript-bundled-3178c6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/zod-validated-3068b7?style=flat-square&logo=zod&logoColor=white" alt="zod"/>
  <img src="https://img.shields.io/badge/OpenAPI-3.1-6ba539?style=flat-square&logo=openapiinitiative&logoColor=white" alt="OpenAPI 3.1"/>
  <img src="https://img.shields.io/badge/dependencies-none-brightgreen?style=flat-square" alt="No dependency"/>
</p>

<p align="center">
  <!-- Works with -->
  <img src="https://img.shields.io/badge/Claude%20Code-compatible-191919?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code"/>
  <img src="https://img.shields.io/badge/Cursor-compatible-000000?style=flat-square" alt="Cursor"/>
  <img src="https://img.shields.io/badge/any%20MCP%20client-stdio-555555?style=flat-square" alt="Any MCP client"/>
</p>

---

### 🛡️ Security & Compliance

<p align="center">
  <!-- Frameworks (Accurey Information Security Policy ACC-SEC-POL-001) -->
  <img src="https://img.shields.io/badge/🇪🇺_GDPR-Privacy%20by%20Design-blue?style=flat-square" alt="GDPR"/>
  <img src="https://img.shields.io/badge/🇬🇧_UK_GDPR-Privacy%20by%20Design-darkblue?style=flat-square" alt="UK GDPR"/>
  <img src="https://img.shields.io/badge/🇸🇬_PDPA-Aligned-red?style=flat-square" alt="PDPA"/>
  <img src="https://img.shields.io/badge/ISO%2FIEC%2027001%3A2022-Controls%20Mapped-darkgreen?style=flat-square" alt="ISO 27001"/>
  <img src="https://img.shields.io/badge/NIST%20CSF-2.0%20Mapped-darkgreen?style=flat-square" alt="NIST CSF 2.0"/>
  <img src="https://img.shields.io/badge/SOC%202%20Type%202-Planned-lightgrey?style=flat-square" alt="SOC 2"/>
</p>

<p align="center">
  <!-- Standards -->
  <img src="https://img.shields.io/badge/Errors-RFC%209457-informational?style=flat-square" alt="RFC 9457"/>
  <img src="https://img.shields.io/badge/Webhooks-HMAC--SHA256-informational?style=flat-square" alt="HMAC-SHA256"/>
  <img src="https://img.shields.io/badge/Transport-HTTPS%20only-4caf50?style=flat-square&logo=letsencrypt&logoColor=white" alt="HTTPS only"/>
</p>

<p align="center">
  <!-- Guards -->
  <img src="https://img.shields.io/badge/scope-Sandbox%20Only-orange?style=flat-square" alt="Sandbox only"/>
  <img src="https://img.shields.io/badge/live%20keys-Refused-red?style=flat-square" alt="Live keys refused"/>
  <img src="https://img.shields.io/badge/keys%20in%20prompts-Refused-red?style=flat-square" alt="Keys in prompts refused"/>
  <img src="https://img.shields.io/badge/personal%20data-Withheld-brightgreen?style=flat-square" alt="Personal data withheld"/>
  <img src="https://img.shields.io/badge/vulnerabilities-Private%20Reporting-success?style=flat-square&logo=github&logoColor=white" alt="Private vulnerability reporting"/>
</p>

---

> **🌐 Endpoints:**\
> 🧪 Sandbox · [sandbox.nodeid.co](https://sandbox.nodeid.co/agents.md) — the only API this MCP calls\
> 🏭 Production · [api.nodeid.co](https://api.nodeid.co/agents.md) — documented here, never called\
> 🔑 Client portal · [app.nodeid.co](https://app.nodeid.co) — API keys, services, credit (people only)
>
> **📦 Version:** 0.2.0 · **Released:** 2026-10-11 · **Distribution:** GitHub Releases only (no npm registry)

---

## 📋 Table of Contents

<details>
<summary>Click to expand</summary>

- [Overview](#-overview)
- [Quick Start](#-quick-start)
- [Claude Code Plugin](#-claude-code-plugin)
- [Tools](#-tools)
- [Security Model](#-security-model)
- [Documentation](#-documentation)
- [This Repository](#-this-repository)
- [Support](#-support)
- [License](#-license)

</details>

---

## 📊 Overview

[NODE ID](https://api.nodeid.co/agents.md) is Accurey's API for company and beneficial-ownership
data and for the verification of persons: company data, monitoring, declared-verified beneficial
owners, identity verification, biometric authentication and AML screening, each service subscribed
per application.

`@accurey/nodeid-mcp` is a [Model Context Protocol](https://modelcontextprotocol.io) server that
gives an AI coding agent what it needs to integrate the NODE ID API into an application.

### Key Capabilities

| Capability                | Description                                                                                        | Needs a key |
| ------------------------- | -------------------------------------------------------------------------------------------------- | :---------: |
| **Offline documentation** | Every operation of the API, its parameters and request body, and the integration guide `agents.md` |     No      |
| **Request design**        | The jurisdictions, a jurisdiction's manifest and legal rules, a quote, and a code snippet per call | Sandbox key |
| **Sandbox calls**         | Real answers from `https://sandbox.nodeid.co`, with synthetic companies and nothing billed         | Sandbox key |
| **Safe by construction**  | Never reads production data, never accepts a live key, never returns a verified person's fields    |      —      |

---

## 🚀 Quick Start

**Requirements:** Node.js 20 or later. The package has no dependency.

### 1. Run it

Each release is a tarball attached to a [GitHub release](https://github.com/ACCUREY/nodeid-mcp/releases)
of this repository. Run it by its exact version:

```bash
npx -y https://github.com/ACCUREY/nodeid-mcp/releases/download/v0.2.0/accurey-nodeid-mcp-0.2.0.tgz
```

### 2. Add it to your agent

For Claude Code, in `.mcp.json` at the root of your project:

```json
{
  "mcpServers": {
    "nodeid": {
      "command": "npx",
      "args": [
        "-y",
        "https://github.com/ACCUREY/nodeid-mcp/releases/download/v0.2.0/accurey-nodeid-mcp-0.2.0.tgz"
      ],
      "env": { "NODEID_API_KEY": "${NODEID_API_KEY}" }
    }
  }
}
```

Other MCP clients take the same `command`, `args` and `env`.

### 3. Set the sandbox key (optional)

The documentation tools work without a key. For the sandbox tools, the person who holds the
account issues a **Test mode** key (`nodeid_test_…`) in the client portal
([app.nodeid.co](https://app.nodeid.co), API keys) and sets it in the shell:

```bash
export NODEID_API_KEY=nodeid_test_...
```

> [!IMPORTANT]
> Never paste a key into a chat or a prompt. The configuration names the variable; the key stays in
> the environment. The server refuses any tool argument that looks like a key.

### Environment Variables

| Variable          | Required          | Default                     | Purpose                                                 |
| ----------------- | ----------------- | --------------------------- | ------------------------------------------------------- |
| `NODEID_API_KEY`  | For sandbox tools | none                        | A Test mode key, `nodeid_test_…`. A live key is refused |
| `NODEID_BASE_URL` | No                | `https://sandbox.nodeid.co` | The sandbox, or a local NODE ID (`http://localhost:…`)  |

---

## 🧩 Claude Code Plugin

In [Claude Code](https://code.claude.com), install the plugin `nodeid` from this repository's
marketplace. It holds this MCP server, run from its release tarball, and skills that follow the
integration guide:

```text
/plugin marketplace add ACCUREY/nodeid-mcp
/plugin install nodeid@accurey
```

| Part                                     | What it does                                                                      |
| ---------------------------------------- | --------------------------------------------------------------------------------- |
| MCP server `nodeid`                      | The tools below, with `NODEID_API_KEY` and `NODEID_BASE_URL` read from your shell |
| Skill `integrate-nodeid`                 | Integrates the API server side, as `agents.md` says                               |
| Skill `design-nodeid-request`            | Chooses the jurisdictions, blocks and mode of a request, and prices it            |
| Skill `nodeid-webhooks`                  | Writes the receiver of the signed events                                          |
| Command `/nodeid:jurisdictions [region]` | Lists the jurisdictions NODE ID connects                                          |
| Command `/nodeid:quote <code> <blocks>`  | Prices a request on the sandbox                                                   |

Set the sandbox key in the shell before starting Claude Code (step 3 above). The plugin's version is
the MCP's: update the marketplace (`/plugin marketplace update accurey`) to move to a new release.

---

## 🧰 Tools

| Tool                                 | What it does                                                               | Key |
| ------------------------------------ | -------------------------------------------------------------------------- | :-: |
| `nodeid_docs_search`                 | Searches the operations and the integration guide                          |  —  |
| `nodeid_docs_operation`              | Describes one operation: parameters, request body, answers                 |  —  |
| `nodeid_docs_guide`                  | Reads `agents.md`, whole or one section                                    |  —  |
| `nodeid_get_rules`                   | The rules an integration follows; with a jurisdiction, its legal rules     | (✓) |
| `nodeid_example_snippet`             | A request to one operation in curl, TypeScript or Python                   |  —  |
| `nodeid_list_jurisdictions`          | `GET /catalog/jurisdictions`: the jurisdictions and their status           |  ✓  |
| `nodeid_get_jurisdiction`            | `GET /catalog/{jurisdiction}`: identifiers, blocks, modes, prices, health  |  ✓  |
| `nodeid_services`                    | `GET /catalog/services`: the services and the application's subscriptions  |  ✓  |
| `nodeid_resolve`                     | `POST /resolve`: ranked candidates (sandbox: jurisdiction `ZZ`)            |  ✓  |
| `nodeid_entity`                      | `GET /entities/{node_id}`: the canonical view of a company                 |  ✓  |
| `nodeid_quote`                       | `POST /quote`: the price of a request, without running it                  |  ✓  |
| `nodeid_identity_verification_start` | `POST /identity/verifications`: a session and its hosted page              |  ✓  |
| `nodeid_identity_verification_get`   | `GET /identity/verifications/{id}`: the outcome, without the person's data |  ✓  |

**Resource:** `nodeid://agents.md`, the integration guide for agents.

(✓): `nodeid_get_rules` needs the key only for a jurisdiction's legal rules. The designer tools
(the jurisdictions, a manifest, the rules, a quote, a snippet) return no company data.

In the sandbox, use the synthetic jurisdiction `ZZ` and its test company numbers `ZZ000001` and
`ZZ000002`.

---

## 🔒 Security Model

| Guard                  | How it is enforced                                                                                                                                                           |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sandbox only**       | `NODEID_BASE_URL` may only be the sandbox or a local NODE ID. A live key, another host, a URL with credentials or a path, and a redirect are refused before anything is sent |
| **No key in the chat** | No tool takes a key. An argument that looks like one is refused with the advice to revoke it, and no answer repeats the key                                                  |
| **No personal data**   | Starting a verification takes no contact details or expected identity; reading one withholds the verified person's fields, which only the application's server reads         |
| **No dependency**      | A single bundled file; the licences of the bundled packages ship in `dist/THIRD_PARTY_LICENSES.md`                                                                           |
| **Verified releases**  | Accurey builds and checks each release before publishing it here, and checks that the downloadable tarball is the one it checked                                             |

NODE ID follows the Accurey Information Security Policy (ACC-SEC-POL-001), with its controls mapped
to ISO/IEC 27001:2022, SOC 2, GDPR, PDPA Singapore and NIST CSF 2.0. NODE ID is not yet certified
against these frameworks; the badges above state where each one stands.

---

## 📚 Documentation

| Resource                                           | Content                                                                        |
| -------------------------------------------------- | ------------------------------------------------------------------------------ |
| [agents.md](https://api.nodeid.co/agents.md)       | The integration guide for AI agents: flow, rules, webhooks, errors, operations |
| [llms.txt](https://api.nodeid.co/llms.txt)         | An index of the documentation for language models                              |
| [OpenAPI](https://app.nodeid.co/openapi.yaml)      | Every operation, schema and event of the API                                   |
| [Problem types](https://api.nodeid.co/v1/problems) | One page per error code                                                        |
| [CHANGELOG](CHANGELOG.md)                          | What changed in each release                                                   |

---

## 📦 This Repository

It holds the released files of the package only: the bundle `dist/nodeid-mcp.js`, the licences of
the packages bundled in it, this README, the changelog, the licence, the security policy, and the
Claude Code plugin (`plugin/`) with its marketplace (`.claude-plugin/marketplace.json`). The
package is not published to any npm registry: install it only from this repository's releases.
Pull requests are not merged here.

---

## 🛟 Support

| Need                  | Where                                                                                              |
| --------------------- | -------------------------------------------------------------------------------------------------- |
| **Vulnerability**     | Privately, as [SECURITY.md](SECURITY.md) explains. Never in a public issue                         |
| **Access to NODE ID** | Accurey onboards each client; owners manage keys, services and credit in the portal                |
| **API reference**     | [agents.md](https://api.nodeid.co/agents.md) and the [OpenAPI](https://app.nodeid.co/openapi.yaml) |

---

## 📜 License

> **This package is open source under the MIT License.** NODE ID itself, its API and its data are
> proprietary services of Accurey, Inc., used under their own terms.

### Ownership

| Entity            | Role                                           |
| ----------------- | ---------------------------------------------- |
| **Accurey, Inc.** | Publisher of this package, operator of NODE ID |

**Copyright © 2026 Accurey, Inc.**

### Terms (MIT)

| Permission     | Status                                    |
| -------------- | ----------------------------------------- |
| Commercial use | ✅ Permitted                              |
| Modification   | ✅ Permitted                              |
| Distribution   | ✅ Permitted                              |
| Private use    | ✅ Permitted                              |
| Condition      | 📄 Keep the copyright and licence notice  |
| Liability      | ❌ None                                   |
| Warranty       | ❌ None, the software is provided "as is" |

See [LICENSE](LICENSE). The licences of the bundled packages are in `dist/THIRD_PARTY_LICENSES.md`.
"NODE ID" and "Accurey" are names of Accurey, Inc.; the MIT License grants no right to use them.

---

## 🙏 Acknowledgments

<p align="center">
  <img src="https://img.shields.io/badge/Model%20Context%20Protocol-191919?style=for-the-badge" alt="Model Context Protocol"/>
  <img src="https://img.shields.io/badge/TypeScript-3178c6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/zod-3068b7?style=for-the-badge&logo=zod&logoColor=white" alt="zod"/>
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js"/>
</p>

---

<p align="center">
  <strong>Developed by the Accurey team</strong>
</p>

<p align="center">
  <em>Company and identity data your agents can integrate, safely.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Operated%20by-Accurey%2C%20Inc.-navy?style=flat-square" alt="Operated by Accurey, Inc."/>
  <img src="https://img.shields.io/badge/Serves-EU_·_KSA_·_UAE_·_SG_·_UK-purple?style=flat-square" alt="Serves 5 jurisdictions"/>
</p>

---

<p align="center">
  <sub>Version 0.2.0 | Released 2026-10-11 | © 2026 Accurey, Inc. | MIT License</sub>
</p>
