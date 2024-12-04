---
tags:
  - Recommended
---

# share

Triggered when a user shares content from the website on social media or other platforms.

## When to pass
This event should be triggered when a user shares content from the website on social media or other platforms, typically by clicking on a share button or link.

## Why it's necessary
It helps track user engagement with shared content and identify popular sharing channels, allowing the business to analyze social media reach and user-generated content. This data can inform social media strategies and content marketing efforts.

## Implementations
Not implemented.

## Code Example

```js
dataLayer.push({
  "event": "share",
  "content_type": "product",
  "content_id": "P_1234567890"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "share" |
| content_type | string | No | Type of content viewed by the user | "product", "blog", "video" |
| content_id | string | No | Unique identifier for the content | "P_1234567890", "B_1234567890", "V_1234567890" |
