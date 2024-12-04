---
title: "Home"
---

# GA4 Data Layer Docs

A marketing data layer serves as a central hub for collecting, organizing, and distributing data related to marketing activities on a website or digital platform. For software engineers, it's essentially a structured framework that standardizes the way marketing data is captured and managed across various tools and platforms.

The purpose of a data layer specification is to define a standardized framework for capturing, structuring, and transmitting data related to user interactions and behaviors on digital platforms. It serves as a blueprint that guides the implementation of a data layer, ensuring consistency in data collection methods and formats across different tools and systems. By establishing clear guidelines, a data layer specification facilitates seamless integration, data interoperability, and effective analytics for informed decision-making in marketing and web development.

## What is a (marketing) data layer?
A marketing data layer is a centralized queue for receiving event messages communicating how users interact with a web page in order to facilitate analytics, third-party marketing tags and tools.

In a Google Analytics implementation, it's one of the cornerstones of data quality (along with the GA4 property configuration and the Google Tag Manager container).

### The data layer queue
The data layer queue is implemented as a simple JavaScript array in the global scope of a page.

```js
window.dataLayer = window.dataLayer || [];
```

### Event messages
As a user interacts with a site, **event messages** are added to the queue as objects via the `Array.prototype.push()` method.

All event messages have at least one property (`event`, a unique event name that distinguishes it from other event message types).

```js
dataLayer.push({
    event: 'generate_lead'
});
```

However most event messages contain other properties, sometimes nested by context.

```js
dataLayer.push({
    event: 'page_view',
    page_type: 'Homepage',
    country: 'us',
    language: 'en'
});
```

Alternatively, data can be pushed to the data layer using a *data message*. This type of message does not have an `event` property and therefore can't be used to trigger an event in GTM. It can be used to pre-populate the data layer with data for later collection, or update existing data between events.


```js
// CANNOT be used as a trigger in GTM, only to add or modify existing data in the data layer
dataLayer.push({
    some_data: 'new_value';
});

// Any tags which are subsequently triggered and which have a field set to 
// a GTM Variable mapped to the dataLayer value `page.name` will collect the
// data from the data message
dataLayer.push({
    event: 'collect_some_data';
});
```

## Resources
- [What is a data layer queue?](https://github.com/google/data-layer-helper?tab=readme-ov-file#what-is-a-data-layer-queue)
- [Google Tag Manager docs — The data layer](https://developers.google.com/tag-platform/tag-manager/datalayer)
- [Analytics Mania — GTM Guide: dataLayer.push with examples](https://www.analyticsmania.com/post/datalayer-push/)
- [GA4 event types](https://support.google.com/analytics/answer/9322688)
    - [GA4 Enhanced Measurement Events](https://support.google.com/analytics/answer/9216061)
    - [Recommended events](https://support.google.com/analytics/answer/9267735)
