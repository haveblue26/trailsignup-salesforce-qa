---
description: Ask a read-only question about the shared trailsignup demo Salesforce org (Accounts, Opportunities, Cases).
argument-hint: [question]
---

Answer the user's question about the trailsignup demo org using the `trailsignup-salesforce` MCP server's `dispatch_readonly` tool. It takes `{ url, queryParams }` and issues a GET against the org's REST/GraphQL API — GET only, so there is no way to write data through it.

Question: `$ARGUMENTS`

## How to query

Prefer the UI API GraphQL endpoint for record data:

```
dispatch_readonly({
  url: "/services/data/v65.0/graphql",
  queryParams: { queryInput: "{\"query\":\"query { uiapi { query { Account(first: 5) { edges { node { Id Name { value } } } } } } } }\"} " }
})
```

- Ground unfamiliar custom field names first with an `objectInfos` query before relying on them — don't guess `__c` field names.
- This org is a Salesforce trial/demo org seeded with standard sample data (e.g. "Acme Partners," "Omega, Inc.," "Upstyle Inc.," and similarly-named accounts) — if asked to assess "customer health" or similar, be transparent that these are demo/seed accounts, not real customers, rather than presenting fabricated relationship signal as real.
- This connector is strictly read-only. If asked to create, update, or delete anything, say plainly that this shared connector can't write and there's no path to make it do so.
