---
name: nodeid-webhooks
description: Write the endpoint that receives NODE ID's signed webhook events - verify the NodeID-Signature on the raw body, refuse old deliveries, deduplicate on the event id and answer within 10 seconds. Use when the user integrates NODE ID events such as identity.verification_completed, request.completed, aml.screening_updated or a monitor's changes.
---

# Receive NODE ID webhooks

NODE ID posts each event to the application's endpoints that subscribed to its type, at least
once. Read the current list of event types and the delivery rules with `nodeid_docs_guide` and the
section `Webhooks`.

## The receiver

1. **Raw body first.** Read the request body as raw bytes, before any JSON parsing or framework
   middleware that re-serialises it.
2. **Verify the signature.** The header is
   `NodeID-Signature: t=<unix time>, v1=<hex HMAC-SHA256>`. Compute HMAC-SHA256 of
   `"<t>.<raw body>"` with the endpoint's secret, read from `NODEID_WEBHOOK_SECRET` (never written
   in code), and compare it to `v1` in constant time. Refuse a delivery whose `t` is more than 300
   seconds away from now. On any mismatch, answer 400 and process nothing.
3. **Deduplicate.** Delivery is at least once: keep the event's `id` (also in `NodeID-Event-Id`)
   and ignore an id already processed.
4. **Answer fast.** Answer 2xx within 10 seconds, and do the work afterwards (a queue or a
   background job). Anything else is retried for 24 hours.
5. **Read, then act.** An event says what changed; read the resource it names with its route
   (`GET /identity/verifications/{id}`, `GET /requests/{request_id}`, `GET /aml/screenings/{id}`,
   `GET /entities/{node_id}`) before acting on it. Never poll in place of an event.
6. **Log ids only.** Log the event id, its type and the ids it names, never a person's field.

## Testing

- Unit-test the verification with a payload signed in the test itself, with a test secret: a valid
  signature, a tampered body, an old timestamp and a wrong secret.
- An owner of the account can send a `webhook.test` event to the endpoint from the client portal,
  in Test mode as in live mode.
