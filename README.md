# trailsignup-salesforce-qa (Claude plugin)

Lets anyone who installs this plugin ask Claude read-only questions about the `trailsignup` demo Salesforce org — zero setup, no Salesforce login, no direct org access. All calls are proxied through a small relay you host (see the sibling `sdo-ajayksh-mcp-relay` project) that holds the org credentials and only ever issues `GET` requests.

## For the org owner: before you distribute this

1. Deploy `sdo-ajayksh-mcp-relay` (see its README) and complete its one-time `/login` step yourself.
2. Edit `.mcp.json` in this plugin and replace the two placeholders with your real deployed values:
   - `url`: `https://<your-render-app>.onrender.com/mcp`
   - `Authorization` header: `Bearer <your RELAY_SHARED_TOKEN>`
3. Now this plugin is ready to share. Anyone who installs it gets read-only access to this org's data through your relay — remember the shared token is effectively public once distributed (see the relay's security note).

## For installers

Install the plugin, then either ask Claude naturally ("what accounts are in the trailsignup org?") or use `/trailsignup-salesforce-qa:ask-org <question>`. No setup, no login, nothing to configure.

**Naming collision warning:** the bundled MCP server is deliberately named `salesforce-headless360-mcp-xdo` — the same name `/salesforce-for-sales` skills look for — so those skills can use it without modification. If you already have your own connector of that same name pointed at a different org, this plugin's server will collide with it. Don't install this plugin if you rely on your own `salesforce-headless360-mcp-xdo` connector.
