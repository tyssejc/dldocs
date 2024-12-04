---
tags:
  - Recommended
  - Ecommerce
---

# select_item

Triggered when a user selects a specific product from a list or grid of products.

## When to pass
This event should be triggered when a user selects a specific product from a list or grid of products, typically by clicking on the product image or title.

## Why it's necessary
It helps track user interest in specific products and identify popular items, allowing the business to analyze product performance and user engagement. This data can inform product recommendations and marketing strategies.

## Implementations

| Where | Source | Status |
| ----- | ------ | ------ |
| Home page | [Link to code](/page) | :material-check-circle: Live |
| Catalog | [Link to code](/page) | :material-check-circle: Live |
| Search Results | [Link to code](/page) | :material-check-circle: Live |
| PDP - Product Recommendations | [Link to code](/page) | :material-check-circle: Live |
| Shopping Cart | [Link to code](/page) | :material-check-circle: Live |

## Code Example

=== "Order Details Page"

    ```js
    // Clear any existing ecommerce data
    dataLayer.push({ecommerce: null});

    dataLayer.push({
      event: "select_item",
      item_list_id: "My Orders",
      item_list_name: "Order Details Page",
      ecommerce: {
        items: [
          {
            item_id: "MIL276720",
            item_name: "Milwaukee 2767-20 M18 FUEL 18 Volt Lithium-lon Brushless Cordless 1/2 in. High Torque Impact Wrench",
            affiliation: "Brick & Mortar Store",
            index: 4,
            item_brand: "Acme",
            item_category: "Widgets",
            item_category2: "Gadgets",
            item_category3: "Gizmos",
            price: 123.50,
            quantity: 1
          }
        ]
      }
    });
    ```

=== "Web Quote Details"

    ```js
    // Clear any existing ecommerce data
    dataLayer.push({ ecommerce: null });

    dataLayer.push({
      event: "select_item",
      item_list_id: "web_quote_details",
      item_list_name: "Web Quote Details",
      ecommerce: {
        items: [
          {
            item_id: "MIL276720",
            item_name: "Milwaukee 2767-20 M18 FUEL 18 Volt Lithium-lon Brushless Cordless 1/2 in. High Torque Impact Wrench",
            affiliation: "Brick & Mortar Store",
            index: 4,
            item_brand: "Acme",
            item_category: "Widgets",
            item_category2: "Gadgets",
            item_category3: "Gizmos",
            price: 123.50,
            quantity: 1
          }
        ]
      }
    });
    ```


## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "select_item" |
| ecommerce | object | Yes | Object containing all e-commerce parameters | See [ecommerce Parameters](#ecommerce-parameters) |

### ecommerce Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| items | Array<Item> | Yes | Array of item objects | See [items Parameters](#items-parameters) |
| [item_list_id](../../reference/item_list_values.md) | string | No | Unique identifier for this product listing.<br>Note: This should NOT be unique to instances of the product listing, but rather to the component which presents the product listing itself. (e.g. there shouldn't be a unique ID for individual web quote IDs, only the web quote details product listing *component*) | "search_results", "web_quote_details", "also_viewed" |
| [item_list_name](../../reference/item_list_values.md) | string | No | Name of the product listing. This should be a value recognizable to business users in GA4. | "Search Results", "Web Quote Details", "Also Viewed" |

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
| [item_list_id](../../reference/item_list_values.md) | string | No | Unique identifier of the product listing in which the product was presented to the user.<br>**Overrides the `item_list_id` parameter at the event level**: do not set here if set at the event level! | "search_results", "web_quote_details", "order_details" |
| [item_list_name](../../reference/item_list_values.md) | string | No | Name of the product listing in which the product was presented to the user.<br>**Overrides the `item_list_name` parameter at the event level**: do not set here if set at the event level! | "Search Results", "Web Quote Details", "Also Viewed" |
| item_variant | string | No | Product variant | "Black", "Large", "10mm" |
| location_id | string | No | Physical location associated with the item. Google recommends using [Google Place ID](https://developers.google.com/maps/documentation/places/web-service/place-id) | "ChIJrTLr-GyuEmsRBfy61i59si0" |
| price | number | No | Product unit price | 9.99, 19.90, 29.00 |
| quantity | number | No | Product quantity | 1, 2, 3 |
