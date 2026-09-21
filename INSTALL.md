# Installing the trailsignup-salesforce-qa plugin

This lets you ask Claude questions about the trailsignup demo Salesforce org — no Salesforce login, no setup, nothing to configure.

## Install (one time)

In Claude Code, run:

```
/plugin marketplace add haveblue26/trailsignup-salesforce-qa
/plugin install trailsignup-salesforce-qa@trailsignup-salesforce-qa-marketplace
```

That's it. No credentials, no env vars, no Salesforce account needed.

## Using it

Just ask naturally, e.g.:

> What accounts are in the trailsignup org?
> Show me open opportunities for Upstyle Inc.

Or use the bundled command:

```
/trailsignup-salesforce-qa:ask-org what cases are open right now?
```

## What this is (and isn't)

- **Read-only.** This can look up data but can never create, edit, or delete anything in the org.
- **Shared demo org.** The org is Salesforce's standard trial/demo data (accounts like "Acme Partners," "Omega, Inc.," "Upstyle Inc." are seeded samples, not real customers).
- Your questions go through a small relay service Ajay hosts — you never see or need org credentials.

## Troubleshooting

- **First request slow (~10-30s)?** The relay is on a free hosting tier that spins down when idle — the first call after a quiet period just wakes it back up.
- **Getting errors?** Ping Ajay — the relay's login can occasionally need refreshing on his end.
