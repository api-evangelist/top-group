---
name: Emulate, send, and track a TON message
description: Safely submit a message to the TON blockchain with pre-flight emulation and confirmation tracking via TON API.
api: openapi/top-group-tonapi-openapi.yml
operations: [getAccountSeqno, emulateMessageToWallet, sendBlockchainMessage, getBlockchainTransactionByMessageHash, getTrace]
generated: '2026-07-21'
method: generated
---

# Emulate, send, and track a TON message

Writes to TON go through message submission; there is no API-level idempotency
key, so always emulate first and track by message hash. Use testnet
(`https://testnet.tonapi.io`) for dry runs — the same TON Console token works.

1. `getAccountSeqno` — read the wallet's current seqno to build a valid
   external message.
2. `emulateMessageToWallet` — pre-flight the signed message BOC; inspect the
   emulated actions and fees before spending anything. (`emulateMessageToEvent`
   / `emulateMessageToTrace` give event- and trace-shaped views.)
3. `sendBlockchainMessage` — submit the message BOC to the blockchain.
4. `getBlockchainTransactionByMessageHash` — poll with the message hash until
   the transaction is finalized.
5. `getTrace` — fetch the full trace (the cascade of transactions caused by
   your message) to confirm downstream effects.

For production monitoring prefer the Webhooks API over polling — see the
`top-group-webhook-monitoring` skill.
