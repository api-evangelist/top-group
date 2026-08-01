---
name: Monitor TON accounts with webhooks
description: Create a webhook and subscribe to account transactions on the TON blockchain via the TON API Webhooks API.
api: openapi/top-group-tonapi-webhooks-openapi.yml
operations: [createWebhook, webhookAccountTxSubscribe, webhookAccountTxSubscriptions, getFailureLogs, webhookBackOnline, deleteWebhook]
generated: '2026-07-21'
method: generated
---

# Monitor TON accounts with webhooks

The Webhooks API (base `https://rt.tonapi.io`, testnet
`https://rt-testnet.tonapi.io`) requires a private TON Console API key in the
`Authorization: Bearer` header (or `token` query param). It replaces the
deprecated SSE Streaming API.

1. `createWebhook` — register your HTTPS endpoint; keep the returned
   `webhook_id`.
2. `webhookAccountTxSubscribe` — subscribe the webhook to a list of account
   IDs. Deliveries are POSTs containing `account_id`, `lt`, and `tx_hash`;
   fetch full detail with the REST API (`getBlockchainTransaction`).
3. `webhookAccountTxSubscriptions` — page subscriptions (`offset`/`limit`) to
   audit what is being watched and spot `failed_attempts` counts.
4. `getFailureLogs` — inspect delivery failures for the webhook.
5. `webhookBackOnline` — resume delivery after your endpoint recovers from
   downtime.
6. `deleteWebhook` — remove the webhook and all its subscriptions when done.

Opcode-wide subscriptions (`webhookMsgOpcodeSubscribe`) fire for every matching
message on the chain, not just your accounts — use them sparingly.
