---
tags:
  - Recommended
---

# search
    
Triggered when a user performs a search on the website.

## When to pass
This event should be triggered when a user performs a search on the website, typically by entering a search query into a search bar.

## Why it's necessary
It allows the business to track user search behavior and identify popular search terms, helping the business understand user intent and optimize search functionality. This data can inform content strategy and product recommendations.

## Implementations
Not implemented. See [search_interaction](./search_interaction.md).

## Code Example

```js
dataLayer.push({
  "event": "search",
  "search_term": "condensers"
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "search" |
| search_term | string | Yes | Search term associated with the event.<br>Only required for events with associated search interactions | "condensers", "toilets", "fittings" |
