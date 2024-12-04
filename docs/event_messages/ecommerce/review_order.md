---
tags:
  - Custom
---

# review_order

Triggered when a user reviews their order details before completing a purchase.

## When to pass
This event should be triggered when a user reviews their order details before completing a purchase, typically on the Order Review page.

## Why it's necessary
It helps track user interactions with order details and identify common review behaviors, allowing the business to analyze purchase intent and optimize checkout flow. This data can inform order confirmation pages and post-purchase communications.

## Implementations

| Where | Source | Status |
| ----- | ------ | ------ |
| Review Order page | [Link to code](/page) | :material-check-circle: Live |

## Code Example

```js
dataLayer.push({
  "event": "review_order",
  "gtm_tag_name": "GA4 - Event",
  "checkout_step_number": 3,
  "checkout_step_name": "review order"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "review_order" |
| gtm_tag_name | string | Yes | Name of the GTM tag this event should trigger | "GA4 - Event" |
| checkout_step_number | number | Yes | Step number of the checkout process | 3 |
| checkout_step_name | string | Yes | Name of the checkout step | "review order" |
