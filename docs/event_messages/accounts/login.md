---
tags:
  - Custom
---

# login

Triggered when a user logs into their account on the website.

## When to pass
This event should be triggered when a user logs into their account on the website.

## Why it's necessary
It allows the business to track user logins and identify returning customers, enabling personalized experiences and targeted marketing campaigns. This data can help improve user retention and loyalty.

## Implementations

| Where | Source | Status |
| ----- | ------ | ------ |
| Login page |  | :material-check-circle: Live |

## Code Example

```js
dataLayer.push({
  "event": "login",
  "method": "oauth2"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "login" |
| method | string | Yes | Name of the method used to log in | "email", "oauth" |
