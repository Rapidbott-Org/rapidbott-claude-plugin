---
name: manage-ecommerce
description: Manage the user's Rapidbott stores, product catalog, variants, and order fulfillment through explicitly authorized ecommerce MCP tools.
---

# Manage Rapidbott Ecommerce

## Check access and target

Use `list_ecommerce_stores` to confirm the account and store. Ask which store only if the user's request does not identify one unambiguously. Use the store's reported currency for prices. If a tool is missing, explain which separate permission is needed; do not attempt direct APIs or other credentials.

## Catalog reads and changes

Use `list_ecommerce_products` before editing an existing product. Treat SKU as optional. `category` is a label such as Books or Courses; `productKind` controls physical/digital inventory and checkout behavior. For digital products, provide `digitalDeliveryText` only when the user supplies or explicitly selects the delivery instructions. Read responses deliberately omit this private content.

Create new items as drafts unless the user explicitly asks to make the item live. A product edit in an already published store may become visible immediately. Send only fields the user asked to change. If replacing variants, first inspect the full variant list and tell the user that the variants field replaces the set. Price inputs use major currency units, such as `12.50`.

## Orders

Use `list_ecommerce_orders` and `get_ecommerce_order` for payment, item, status, total, and tracking questions. These tools intentionally omit customer names, emails, phone numbers, addresses, and digital fulfillment content. Never infer missing customer data.

Use `update_ecommerce_order_fulfillment` only when the user explicitly requests a specific fulfillment change. Online orders must show paid before fulfillment advances. A tracking number is required to mark an order shipped. This tool cannot cancel orders, refund payments, or change payment settings.

After a successful mutation, report the affected store/product/order and the returned status. Do not claim a payment, email delivery, or external customer notification occurred unless a tool confirms it.
