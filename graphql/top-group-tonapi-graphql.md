---
generated: '2026-07-21'
method: searched
source: https://docs.tonconsole.com/tonapi/graphql
---

# TON API GraphQL

TON API exposes a GraphQL endpoint alongside its REST API.

- Endpoint: `https://tonapi.io/v2/graphql`
- Playground: `https://tonapi.io/v2/graphql/playground`
- Docs: https://docs.tonconsole.com/tonapi/graphql

The official documentation warns that the GraphQL API "may work unstably and is
expected to be redesigned" and recommends the REST API for reliable operation.
Example published query:

```graphql
query {
  allAccounts(first: 1) {
    nodes {
      id
      name
    }
  }
}
```
