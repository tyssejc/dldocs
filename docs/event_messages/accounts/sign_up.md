---
tags:
  - Recommended
---

# sign_up

Triggered when a user creates an account on the website.

## When to pass
This event should be triggered when a user creates an account on the website, typically by completing a registration form or sign-up process.

## Why it's necessary
It allows the business to track user registrations and identify new customers, enabling personalized experiences and targeted marketing campaigns. This data can help improve user retention and loyalty.

## Implementations
Not implemented. See [registration_complete](./registration_complete.md).

## Code Example

```js
dataLayer.push({
  "event": "sign_up",
  "method": "email"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "sign_up" |
| method | string | No | Method used to log in | "email", "oauth2", "google" |
