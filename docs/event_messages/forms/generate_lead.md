---
tags:
  - Recommended
---

# generate_lead

Triggered when a user submits a lead form or expresses interest in a product or service.

## When to pass
This event should be triggered when a user submits a lead form or expresses interest in a product or service, typically by providing contact information or requesting more information.

## Why it's necessary
It helps track user engagement with lead generation forms and identify which products or services are generating the most interest. This data can inform marketing strategies and lead nurturing campaigns.

## Implementations
Not implemented.

## Code Example

```js
dataLayer.push({
  "event": "generate_lead",
  "lead_source": "google",
  "currency": "USD",
  "value": 30.03
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "generate_lead" |
| currency | string | Yes | 3-letter ISO-4217 currency code | "USD", "EUR", "JPY" |
| lead_source | string | No | Lead source of the user | "google", "trade show", "form", "tfn" |
| value | number | Yes | Monetary value of the event. This is typically the expected value of the lead, e.g. average customer lifetime value (CLV) * lead-to-customer conversion rate | 30.03, 99.9, 300 |