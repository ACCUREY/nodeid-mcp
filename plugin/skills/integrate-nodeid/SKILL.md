---
name: integrate-nodeid
description: Integrate the NODE ID API into an application, server side, as its integration guide for agents says - company and beneficial-ownership data, monitoring, identity verification and AML screening, with idempotency keys, signed webhooks and the prepaid credit. Use when the user wants to call NODE ID, add KYB, KYC or AML checks through NODE ID, or test an integration against the NODE ID sandbox.
---

# Integrate the NODE ID API

NODE ID is one REST API under `/v1`: `https://api.nodeid.co/v1` in production,
`https://sandbox.nodeid.co/v1` in the sandbox. Build and test against the sandbox. The `nodeid`
MCP server of this plugin carries the API's documentation offline and calls the sandbox only.

## Before writing code

1. Read the rules with `nodeid_get_rules`, and follow every one of them. The essentials:
   - **The key stays out of the conversation.** Never ask for an API key, never print one, never
     write one in code, a commit, a test, a log or a prompt. A person issues it in the client
     portal (`https://app.nodeid.co`) and sets it as `NODEID_API_KEY`; the base URL is
     `NODEID_BASE_URL`. If a key appears in the conversation, tell the user to revoke it in the
     portal.
   - **Server side only.** NODE ID is called from the application's server, never from a browser.
   - **Every `POST` sends an `Idempotency-Key`**, one per order, stored with the order so that a
     retry sends the same key.
   - **Webhooks, not polling**, wherever an event exists (see the `nodeid-webhooks` skill).
   - **No personal field in a log**: log ids only (`node_id`, verification id, request id).
2. Check the application's services with `nodeid_services`. A call to a service it has not
   subscribed to answers `403 service_not_subscribed`; the account's owners subscribe in the
   portal, for free.
3. Design and price the request with the `design-nodeid-request` skill when it reads company data.

## Writing the integration

1. Find each operation with `nodeid_docs_search`, then read it with `nodeid_docs_operation`: its
   parameters, its body and its answers.
2. Start from `nodeid_example_snippet` in the application's language (curl, TypeScript or
   Python), and adapt it to the application's HTTP client and configuration. Keep its shape: the
   key from the environment, an `Idempotency-Key` on every `POST`, the problem's `code` on an
   error.
3. Handle errors as RFC 9457 problem details with a typed `code`. Retry `source_unavailable` and
   `rate_limited` later (honour `Retry-After`); fix the request for the others. `402
   insufficient_credit` means the account's owners top up the credit in the portal.
4. Read `X-NodeID-Request-Id` on every answer and keep it with the application's record, to quote
   it when reporting a problem.
5. The flows the guide describes:
   - **Company data.** `POST /resolve` finds the company and its `node_id`; `GET
     /entities/{node_id}` reads the blocks the screen needs, in `onboarding` mode from the store,
     `verification` mode only to check live at the source (202, then `request.completed`). Keep the
     `node_id` the API answers: a merged entity is answered as its survivor, with `merged_from`.
   - **Identity.** `POST /identity/verifications` with the service (`kyc`, `kyc_aml` or
     `biometric_auth`) and the application's stable `reference` of the person answers a hosted
     page; send the person there. The decision arrives as `identity.verification_completed`; read
     it then with `GET /identity/verifications/{id}`. NODE ID records the provider's decision and
     decides nothing itself.
   - **AML screening.** `POST /aml/screenings` screens a person or a company at once; with
     monitoring, each change arrives as `aml.screening_updated`.
   - **Monitoring.** `POST /monitors` watches the blocks of an entity; each change is an event.

## Testing

- Try each call on the sandbox with the MCP's tools (`nodeid_resolve`, `nodeid_entity`,
  `nodeid_quote`, `nodeid_identity_verification_start`, ...). In the sandbox, use the synthetic
  jurisdiction `ZZ` and its test numbers `ZZ000001` and `ZZ000002`.
- The application's tests never call NODE ID: record sandbox answers once and replay them, with no
  key and no personal data in the recordings.
- Never use the MCP's tools to read a verified person's fields: the application's server reads
  them, and only for the verifications it ordered.
