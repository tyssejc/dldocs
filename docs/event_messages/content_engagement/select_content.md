---
tags:
  - Recommended
---

# select_content

Triggered when a user interacts with content on the website, such as clicking on a product image or video.

## When to pass
This event should be triggered when a user interacts with content on the website, such as clicking on a product image or video.

## Why it's necessary
It helps track user engagement with specific content elements, allowing the business to analyze user interactions and optimize content placement. This data can inform content strategy and user experience design.

## Implementations
Not implemented.

## Code Example

```js
dataLayer.push({
  "event": "select_content",
  "content_type": "article",
  "content_id": "A_1234567890"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "select_content" |
| content_type | string | No | Type of content viewed by the user | "article", "blog", "video" |
| content_id | string | No | Unique identifier for the content | "A_1234567890" |
