---
tags:
  - Recommended
  - Ecommerce
---

# add_to_cart

Triggered when a user adds a product to their shopping cart.

## When to pass
This event should be triggered when a user adds a product to their shopping cart.

## Why it's necessary
It allows the business to track which products are being added to carts most frequently, helping the business understand user intent and identify popular items. This data is crucial for analyzing conversion rates and optimizing the path to purchase.

## Implementations

| Where | Source | Status |
|-------|--------|--------|
| Cart page | [Link to code](/page) | :material-check-circle: Live |
| PDP - Cross sell products | [Link to code](/page) | :material-check-circle: Live |
| Search results/category pages | [Link to code](/page) | :material-check-circle: Live |

## Code Example

```js
// Clear any existing ecommerce data
dataLayer.push({ecommerce: null});

dataLayer.push({
  event: "add_to_cart",
  ecommerce: {
    currency: "USD",
    value: 9.99,
    items: [
      {
        item_id: "I_1234567890",
        item_name: "shoes",
        affiliation: "Brick & Mortar Store",
        coupon: "ITEM10OFF",
        discount: 2,
        index: 1,
        item_brand: "Acme",
        item_category: "Widgets",
        item_category2: "Gadgets",
        item_category3: "Gizmos",
        item_category4: "Doodads",
        item_category5: "Trinkets",
        item_list_id: "L_1234567890",
        item_list_name: "Recommended",
        item_variant: "Black",
        location_id: "ChIJrTLr-GyuEmsRBfy61i59si0",
        price: 9.99,
        quantity: 1
      }
    ]
  }
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "add_to_cart" |
| ecommerce | object | Yes | Object containing all e-commerce parameters | See [ecommerce Parameters](#ecommerce-parameters) |

### ecommerce Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| currency | string | Yes | 3-letter ISO-4217 currency code | "USD", "EUR", "JPY" |
| value | number | Yes | Monetary value of the event | 1.23, 99.9, 300 |
| items | Array<Item> | Yes | Array of item objects | See [items Parameters](#items-parameters) |

### items Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| item_id | string | Yes | Unique identifier for the item | "I_1234567890" |
| item_name | string | Yes | Name of the item | "shoes", "t-shirt", "hat" |
| affiliation | string | Yes | Product affiliation to designate a supplying company or brick-and-mortar store location<br>Only available at item level | "Brick & Mortar Store" |
| coupon | string | No | Item-level coupon code. Independent from **event-level** `coupon` parameter | "ITEM10OFF" |
| discount | number | No | Unit discount amount associated with the item | 2.22 |
| index | number | No | Index/position of the item in the list | 1, 10, 465 |
| item_brand | string | No | Product brand | "ProFlow", "Delta" |
| item_category | string | No | Product category | "Plumbing", "HVAC" |
| item_category2 | string | No | Level 2 category hierarchy/taxonomy | "Faucets", "Toilets" |
| item_category3 | string | No | Level 3 category hierarchy/taxonomy | "Kitchen", "Bathroom" |
| item_category4 | string | No | Level 4 category hierarchy/taxonomy | "Sink", "Shower" |
| item_category5 | string | No | Level 5 category hierarchy/taxonomy | "Single Handle", "Double Handle" |
| [item_list_id](../../reference/item_list_values.md) | string | No | Unique identifier of the list in which the product was presented to the user. | "search_results", "recommended_products", "also_viewed" |
| [item_list_name](../../reference/item_list_values.md) | string | No | Name of the list in which the product was presented to the user. | "Search Results", "Recommended Products", "Also Viewed" |
| item_variant | string | No | Product variant | "Black", "Large", "10mm" |
| location_id | string | No | Physical location associated with the item. Google recommends using [Google Place ID](https://developers.google.com/maps/documentation/places/web-service/place-id) | "ChIJrTLr-GyuEmsRBfy61i59si0" |
| price | number | No | Product unit price | 9.99, 19.90, 29.00 |
| quantity | number | No | Product quantity | 1, 2, 3 |
