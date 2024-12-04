---
tags:
  - Recommended
  - Ecommerce
---

# begin_checkout

Triggered when a user initiates the checkout process.

## When to pass
This event should be triggered when a user initiates the checkout process, typically by clicking a "Checkout" button or entering the first step of a multi-step checkout.

## Why it's necessary
It allows the business to track how many users are starting the checkout process, which is a critical step in the conversion funnel. This data helps analyze cart abandonment rates and identify potential issues in the transition from cart to checkout.

## Implementations

| Where | Source | Status |
|-------|--------|--------|
| Checkout button | [Link to code](/page) | :material-check-circle: Live |

## Code Example

```js
// Clear any existing ecommerce data
dataLayer.push({ecommerce: null});

dataLayer.push({
  event: "begin_checkout",
  ecommerce: {
    currency: "USD",
    value: 9.99,
    coupon: "SUMMER2021",
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
| event | string | Yes | Name of the event | "begin_checkout" |
| ecommerce | object | Yes | Object containing all e-commerce parameters | See [ecommerce Parameters](#ecommerce-parameters) |

### ecommerce Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| currency | string | Yes | 3-letter ISO-4217 currency code | "USD", "EUR", "JPY" |
| value | number | Yes | Monetary value of the event | 1.23, 99.9, 300 |
| coupon | string | No | Coupon code used in the event<br>Event-level and item-level `coupon` parameters are independent. | "SUMMER2021", "WINTER2021", "SPRING2021" |
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