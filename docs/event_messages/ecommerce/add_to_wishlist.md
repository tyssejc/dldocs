---
tags:
  - Recommended
  - Ecommerce
---

# add_to_wishlist

Triggered when a user adds a product to a wishlist.

## When to pass
This event should be triggered when a user adds a product to their wishlist or favorites list.

## Why it's necessary
It helps track user interest in specific products, allowing the business to analyze wishlist activity and identify popular items. This data can inform marketing strategies and personalized recommendations.

# Implementations

| Where | Source | Status |
|-------|--------|--------|
| Cart page | [Link to code](/page) | :material-check-circle: Live |
| Catalog pages | [Link to code](/page) | :material-check-circle: Live |
| PDPs | [Link to code](/page) | :material-check-circle: Live |
| Search results/PLPs | [Link to code](/page) | :material-check-circle: Live |

## Code Example

=== "Web Quote Details"

    ```js
    // Clear any existing ecommerce data
    dataLayer.push({ ecommerce: null });

    dataLayer.push({
      event: "add_to_wishlist",
      ecommerce: {
        currency: "USD",
        value: 9.99,
        items: [
          {
            item_id: "SMTGF703",
            item_name: "2 in. x 150 ft. Aluminum Foil Tape",
            price: 8.48,
            item_brand: "Acme",
            item_category: "Widgets",
            item_category2: "Gadgets",
            currency: "CAD",
            affiliation: "Brick & Mortar Store",
            location_id: "ChIJyakzuxm9KogRfb-d9ZSq1r8",
            quantity: 1,
            index: 1,
            item_list_id: "web_quote_details",
            item_list_name: "Web Quote Details"
          },
          {
            item_id: "SMTGF702",
            item_name: "3 in. x 150 ft. Aluminum Foil Tape",
            price: 12.45,
            item_brand: "Acme",
            item_category: "Widgets",
            item_category2: "Gadgets",
            currency: "CAD",
            affiliation: "Brick & Mortar Store",
            location_id: "ChIJyakzuxm9KogRfb-d9ZSq1r8",
            quantity: 1,
            index: 2,
            item_list_id: "web_quote_details",
            item_list_name: "Web Quote Details"
          }
        ]
      }
    });
    ```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "add_to_wishlist" |
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
| [item_list_id](../../reference/item_list_values.md) | string | No | Unique identifier of the product listing in which the product was presented to the user. |
| [item_list_name](../../reference/item_list_values.md) | string | No | Name of the product listing in which the product was presented to the user. |
| item_variant | string | No | Product variant | "Black", "Large", "10mm" |
| location_id | string | No | Physical location associated with the item. Google recommends using [Google Place ID](https://developers.google.com/maps/documentation/places/web-service/place-id) | "ChIJrTLr-GyuEmsRBfy61i59si0" |
| price | number | No | Product unit price | 9.99, 19.90, 29.00 |
| quantity | number | No | Product quantity | 1, 2, 3 |
