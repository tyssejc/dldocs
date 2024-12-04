---
tags:
  - Recommended
  - Ecommerce
---

# select_promotion

Triggered when a user selects a promotion or special offer, such as a discount code or free shipping offer.

## When to pass
This event should be triggered when a user selects a promotion or special offer, such as a discount code or free shipping offer, typically by clicking on a promotional banner or link.

## Why it's necessary
It helps track user engagement with promotions and identify which offers are generating the most interest, allowing the business to analyze promotion performance and optimize marketing campaigns. This data can inform promotional strategies and discounting decisions.

## Implementations

| Where | Source | Status |
| ----- | ------ | ------ |
| Home page | [Link to code](/page) | :material-check-circle: Live |
| Search Results/PLPs | [Link to code](/page) | :material-check-circle: Live |

## Code Example

=== "No specific product(s) in promotion"

    ```js
    dataLayer.push({
      event: "select_promotion",
      ecommerce: {
        creative_name: "summer_sale",
        creative_slot: "homepage",
        promotion_id: "P_1234567890",
        promotion_name: "10%_off"
      }
    });
    ```

=== "Promotion includes specific product(s)"

    ```js
    // Only include the product that was clicked
    dataLayer.push({
      event: "select_promotion",
      ecommerce: {
        creative_name: "summer_sale",
        creative_slot: "homepage",
        promotion_id: "P_1234567890",
        promotion_name: "10%_off",
        items: [
          {
            item_id: "SMTGF703",
            item_name: "2 in. x 150 ft. Aluminum Foil Tape",
            price: 9, // (1)!
            discount: 1, // (2)!
            item_brand: "Acme",
            item_category: "Widgets",
            item_category2: "Gadgets",
            currency: "CAD",
            affiliation: "Brick & Mortar Store",
            location_id: "ChIJyakzuxm9KogRfb-d9ZSq1r8",
            quantity: 1,
            index: 1
          }
        ]
      }
    });
    ```

    1. If a discount applies, set `price` to the discounted unit price. In this example, the unit price is $10, but a 10% discount is being offered. So `price` becomes `9`, and we set `discount` to `1`.
    2. Set this to the unit price discount.

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "select_promotion" |
| ecommerce | object | Yes | Object containing all e-commerce parameters | See [ecommerce Parameters](#ecommerce-parameters) |

### ecommerce Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| creative_name | string | No | Name of the promotional creative | "summer_sale", "winter_sale", "spring_sale" |
| creative_slot | string | No | Slot where the promotional creative was displayed | "homepage", "product_page", "checkout" |
| promotion_id | string | No | Unique identifier for the promotion | "P_1234567890" |
| promotion_name | string | No | Name of the promotion | "10%_off", "free_shipping", "buy_one_get_one" |
| items | Array<Item> | No | Array of item objects | See [items Parameters](#items-parameters) |

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
