---
tags:
  - Recommended
  - Ecommerce
---

# view_item

Triggered when a user views a specific product's details page.

## When to pass
This event should be triggered when a user views a specific product's details page.

## Why it's necessary
It helps track which products are generating the most interest, allowing the business to analyze product performance and user engagement with specific items. This data can inform inventory decisions and marketing strategies.

## Implementations

| Where | Source | Status |
| ----- | ------ | ------ |
| PDPs | [Link to code](/page) | :material-check-circle: Live |

## Code Example

```js
// Clear any existing ecommerce data
dataLayer.push({ ecommerce: null });

dataLayer.push({
  event: "view_item",
  ecommerce: {
    currency: "USD",
    value: 9.99,
    items: [
      {
        item_id: "I_1234567890",
        item_name: "shoes",
        affiliation: "Brick & Mortar Store",
        discount: 2, // (1)!
        index: 1, // (2)!
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

1. Only if discount offered on the item
2. Should be the index of where it appeared in the referring product listing, if applicable. For example, if it was the 13th item in a list of search results, the value would be `13`.

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "view_item" |
| ecommerce | object | Yes | Object containing all e-commerce parameters | See [ecommerce Parameters](#ecommerce-parameters) |

### ecommerce Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| currency | string | Yes | 3-letter ISO-4217 currency code | "USD", "EUR", "JPY" |
| value | number | Yes | Monetary value of the event | 1.23, 99.9, 300 |
| items | Array<Item> | Yes | Array of item objects<br><br>For `view_item` there should only be one `item` object | See [items Parameters](#items-parameters) |

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
