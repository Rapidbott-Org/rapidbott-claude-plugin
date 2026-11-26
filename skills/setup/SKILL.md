---
name: setup
description: Connect Claude to the user's Rapidbott Flow account, confirm which chatbots are authorized, and explain the available permissions.
---

# Connect Rapidbott Flow

## Start the connection

When the user asks to connect Rapidbott Flow, check whether the `rapidbott-flow` MCP tools are available. This plugin connects to `https://app.rapidbott.com/api/mcp/rapidbott-flow`.

If the tools are not available yet, tell the user to connect the server and sign in to Rapidbott:

- **Claude (web, desktop, Cowork):** open the plugin or connector settings for Rapidbott Flow and choose **Connect**, then complete the Rapidbott sign-in and consent page.
- **Claude Code:** run `/mcp`, select `rapidbott-flow`, and start its sign-in.

Never ask for the user's password, API token, or other secret. Sign-in happens only on Rapidbott's own consent page.

## Confirm access

After consent succeeds, call `get_profile` and `list_connected_projects` to confirm the connected account and authorized chatbot(s), then call `list_flows` to confirm access. The consent screen limits access to the chatbot(s) the user selected.

Ecommerce permissions are separate and account-wide; request only the read/write access needed. Draft editing requires `flow:write`. Publishing requires the separate `flow:publish` permission and the user's explicit instruction to publish; publishing affects live users and runs Rapidbott Flow validation.

If the connection reports an OAuth or connection error, report the specific error and do not claim the account is connected. The user can revoke access from **Rapidbott Flow → Settings → API Keys → Connected AI clients**.
