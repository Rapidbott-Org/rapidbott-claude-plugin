---
name: build-chatbot
description: Build or update a chatbot in Rapidbott Flow using the connected chatbot's current flows, integrations, templates, forms, and node configuration.
---

# Build a chatbot in Rapidbott Flow

Use the `rapidbott-flow` MCP server for Rapidbott Flow work. The connection is authorized by the user and limited to the chatbot(s) selected on Rapidbott's consent page. Never request or store the user's Rapidbott password, access token, or API key in chat.

## Before editing

1. Call `list_flows` and identify the requested flow. If creating a new flow, call `list_flow_node_types` and `get_flow_authoring_guide` first.
2. For an existing flow, call `get_flow` and use its latest `flowRevision` when saving. Do not overwrite concurrent edits; on a revision conflict, reread and reconcile.
3. Inspect `get_flow_project_context` and the relevant `get_flow_node_examples` before configuring integrations or unfamiliar node types. Use the selected chatbot's template, WhatsApp Flow, reusable form, webhook, and custom-field tools when the requested flow needs those resources. Do not expose form submissions, contact values, sample values, webhook URLs, headers, or secrets.
4. Confirm the requested behavior and any meaningful side effects with the user before drafting. Use only node types enabled by `list_flow_node_types`; do not invent unsupported node data fields when an existing example or authoring guide defines the shape.

## Drafting

- Build the smallest complete graph that meets the user's requested behavior. Include one Start node, connected paths, and a graceful Stop node or configured Jump destination.
- Preserve unrelated nodes, settings, and branches when modifying an existing flow. Keep node IDs unique, edge endpoints valid, and branch `sourceHandle` values aligned with the node's actual outputs.
- Keep credentials and secret values out of generated content. Preserve existing masked secrets as provided by the server; do not replace or infer them.
- Before saving, summarize the intended change and call `create_flow` or `save_flow_draft` only when the user has asked you to make the change. Explain any preflight warnings returned by the tool.
- Changes remain unpublished drafts unless the user explicitly asks to publish and granted `flow:publish`. Before publishing, read the latest revision, summarize that the chatbot will change for live users, then call `publish_flow`; it applies Rapidbott Flow validation and returns the result. Never publish merely because the draft is complete.

## Keep capabilities current

Use `list_flow_node_types` and `get_flow_authoring_guide` at the start of each build rather than relying on a remembered static list. The MCP server provides the selected chatbot's resources and supported node catalog. Use only tools actually exposed by the connected server; if the user asks for an action that is not available, explain that it needs an explicit Rapidbott MCP tool and permission scope before it can be performed.
