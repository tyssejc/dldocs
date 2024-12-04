# Product list attribution

**Product list attribution** is a feature that helps track how customers interact with product listings on an ecommerce website, and attributes conversions to these interactions.

GA4 uses a **last-click attribution model** for product listing interactions. This means the last product listing a customer interacted with before making a purchase gets credit for conversion.

## Why is it important?

When product list attribution is implemented correctly, it enables powerful reporting in Google Analytics which helps the business understand which product listings are most effective in driving conversions, allowing for optimization of product placement and listing design.

## Key interactions
These events drive product list attribution.

### [view_item_list](../event_messages/ecommerce/view_item_list.md)

Signifies when a user sees a product listing of multiple products.

Examples:

- Search results
- Product listing pages (PLPs), such as category pages
- A "Recommended Products" or "Customers Also Viewed" widget

It's critical for this event to include `item_list_id` and `item_list_name` so that the business can see e.g. which product listings are driving product interactions.

### [select_item](../event_messages/ecommerce/select_item.md)

Signifies when a user selects (clicks, taps, etc.) a product from a product listing.

In this context, it's important to "pass on" the values for `item_list_id` and `item_list_name` used in the `view_item_list` event for the product listing.

Example:
```js
// Customer is shown a product listing...
dataLayer.push({
	event: "view_item_list",
	ecommerce: {
		item_list_id: "category_01", // <== tells the business where a customer saw a product
		item_list_name: "Category Listing", // <== tells the business where a customer saw a product
		items: [
			{
				item_id: "I_123456710",
				item_name: "Kyber Crystal",
				price: 8.48,
				item_brand: "Acme",
				item_category: "Widgets",
				item_category2: "Gadgets",
				currency: "USD",
				affiliation: "Brick & Mortar Store",
				quantity: 1,
				index: 1
			},
			{
				item_id: "I_123456711",
				item_name: "Focusing Lens",
				price: 12.45,
				item_brand: "Acme",
				item_category: "Widgets",
				item_category2: "Gadgets",
				currency: "USD",
				affiliation: "Brick & Mortar Store",
				quantity: 1,
				index: 2
			},
			{
				item_id: "I_123456712",
				item_name: "Cycling Field Energizer",
				price: 5.66,
				item_brand: "Acme",
				item_category: "Widgets",
				item_category2: "Gadgets",
				currency: "USD",
				affiliation: "Brick & Mortar Store",
				quantity: 1,
				index: 3
			}
		]
	}
}
});

// ... then clicks on a product to see more details about it.
dataLayer.push({
	event: "select_item",
	item_list_id: "category_01", // <== MUST MATCH VALUE IN view_item_list
	item_list_name: "Category Listing", // <== MUST MATCH VALUE IN view_item_list
	ecommerce: {
		items: [
			{
				item_id: "I_123456710",
				item_name: "Kyber Crystal",
				price: 8.48,
				item_brand: "Acme",
				item_category: "Widgets",
				item_category2: "Gadgets",
				currency: "USD",
				affiliation: "Brick & Mortar Store",
				quantity: 1,
				index: 1
			}
		]
	}
});

```

## Supporting events

### [view_item](../event_messages/ecommerce/view_item.md)

Signifies when a user has viewed a product detail page (PDP).

`item_list_name` and `item_list_id` are important here because the business can then break down PDP views by listings that resulted in the view.

It's important to note that in this event (and some others), `item_list_name` and `item_list_id` are set at the *item* level, not at the *event* level (as with `view_item_list` and `select_item`.) See below note about [scope](#a-note-about-scope).

### [view_cart](../event_messages/ecommerce/view_cart.md)

Signifies when a user has viewed their shopping cart.

Users can add products to their carts from many different sources — PLPs, PDPs, promotions, etc. Each product in the `items` array for this event should reflect which `item_list_id` and `item_list_name` the add came from.

### [begin_checkout](../event_messages/ecommerce/begin_checkout.md) and other checkout events

Once the user starts the checkout flow, the contributing `item_list_id` and `item_list_name` should be set at the item level for each event in the funnel.

## A note about scope

`item_list_id` and `item_list_name` can be set either at the *event* level (e.g. `ecommerce.item_list_name`) or at the *item* level (e.g. `ecommerce.items[0].item_list_name`). When set at the event level, the value will *override* any value set at the item level.

Here's an example:

```js
dataLayer.push({
	event: "view_item_list",
	ecommerce: {
		item_list_name: "Product Recommendations", // <== overrides item-level item_list_name
		item_list_id: "product_recs_01", // <== overrides item-level item_list_id
		items: [
			{
				item_id: "I_123456710",
				item_name: "Kyber Crystal",
				item_list_name: "Product Recommendations" // <== overridden by ecommerce.item_list_name
				item_list_id: "product_recs_01", // <== overridden by ecommerce.item_list_id
				item_brand: "Acme",
				item_category: "Widgets",
				item_category2: "Gadgets",
				currency: "USD",
				affiliation: "Brick & Mortar Store",
				price: 8.48,
				index: 1
			}
		]
	}
})
```

