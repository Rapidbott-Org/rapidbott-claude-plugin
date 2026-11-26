# Rapidbott Flow for Claude

Build and update chatbots in [Rapidbott Flow](https://rapidbott.com) from Claude. The plugin connects Claude to the Rapidbott-hosted MCP server and adds skills for connecting your account, building chatbot flows, and managing Rapidbott ecommerce stores.

## What it can do

- **Build chatbots:** list, read, create and update chatbot flows as unpublished drafts, using your chatbot's templates, forms, webhooks, custom fields and supported node types.
- **Publish (optional):** publish a flow only when you grant the separate publish permission and explicitly ask Claude to publish.
- **Ecommerce (optional):** view stores and products, add or edit products, read orders, and update order fulfillment when you grant those permissions.

## Privacy and safety

- Sign-in uses Rapidbott's own OAuth consent page. Claude never sees your Rapidbott password or API keys.
- Access is limited to the chatbots you select on the consent page and the permissions you grant.
- Draft changes stay unpublished until you ask Claude to publish.
- Order tools omit customer contact and address details and never return private digital delivery content.
- Cancellation, refunds, payment settings and store deletion are not available through this plugin.
- Revoke access at any time in **Rapidbott Flow → Settings → API Keys → Connected AI clients**.

## Getting started

1. Install the Rapidbott Flow plugin in Claude.
2. Connect the `rapidbott-flow` server and sign in to Rapidbott when prompted. Choose the chatbot(s) and permissions to allow.
3. Ask Claude: *"List the flows in my Rapidbott chatbot."*

### Claude Code

```bash
claude plugin marketplace add Rapidbott-Org/rapidbott-claude-plugin
claude plugin install rapidbott-flow@rapidbott
```

Then run `/mcp`, select `rapidbott-flow`, and sign in.

## Requirements

A Rapidbott Flow account at [app.rapidbott.com](https://app.rapidbott.com). Some features depend on your Rapidbott plan.

## Support

This plugin is maintained by Rapidbott. For help, visit [rapidbott.com](https://rapidbott.com).

## License

[MIT](LICENSE)
