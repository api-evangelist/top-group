---
name: Inspect a TON account and its activity
description: Read a TON account's balance, jettons, NFTs, and event history via TON API.
api: openapi/top-group-tonapi-openapi.yml
operations: [getAccount, getAccountJettonsBalances, getAccountNftItems, getAccountEvents, getBlockchainAccountTransactions]
generated: '2026-07-21'
method: generated
---

# Inspect a TON account and its activity

Use TON API (base `https://tonapi.io`, testnet `https://testnet.tonapi.io`) with a
TON Console bearer token in the `Authorization` header. Unauthenticated calls are
limited to 1 request per 4 seconds; see `rate-limits/top-group-rate-limits.yml`.

1. `getAccount` — fetch the human-friendly account view (balance, status,
   interfaces) for a raw (`0:...`) or user-friendly address. Use `addressParse`
   first if you need to normalize an address form.
2. `getAccountJettonsBalances` — list the account's jetton (token) balances;
   follow with `getAccountJettonsHistory` for transfer history.
3. `getAccountNftItems` — list NFTs owned by the account.
4. `getAccountEvents` — page through decoded activity (actions like
   TonTransfer, JettonTransfer, NftItemTransfer) using `limit` and the
   `before_lt` cursor from the previous page.
5. `getBlockchainAccountTransactions` — drop to raw transactions when you need
   lt/hash-level detail.

Errors come back as a JSON object with a single `error` string field
(`errors/top-group-problem-types.yml`); there is no idempotency-key contract —
reads are safe to retry.
