---
tags:
  - Enhanced Measurement
  - Recommended
---

# video_complete

!!! warning
    Embedded YouTube videos with the JS API enabled are tracked automatically through [Enhanced Measurement](https://support.google.com/analytics/answer/9216061?hl=en). All YouTube videos embedded *without* JS API support and any non-YouTube videos must be instrumented manually.

Triggered when a user completes watching a video on the website.

## When to pass

This event should be triggered when a user completes watching a video on the website, typically by reaching the end of the video or clicking on a completion button.

## Why it's necessary
It helps track user engagement with video content and identify video completion rates, allowing the business to analyze video performance and optimize video engagement. This data can inform video marketing strategies and content production.

## Implementations
Not implemented.

## Code Example

```js
dataLayer.push({
  "event": "video_complete",
  "video_current_time": 0,
  "video_duration": 30,
  "video_percent": 0,
  "video_provider": "YouTube",
  "video_title": "How to Build a Rocket",
  "visible": true
});
```

## Parameters

| Name | Type | Required | Description | Examples |
|------|------|----------|-------------|----------|
| event | string | Yes | Name of the event | "video_complete" |
| video_current_time | number | Yes | Current time of the video in milliseconds | 0, 10, 120 |
| video_duration | number | Yes | Duration of the video in milliseconds | 30, 120, 1800 |
| video_percent | number | Yes | Percentage of the video watched by the user | 0, 25, 50, 75, 100 |
| video_provider | string | Yes | Provider of the video | "YouTube", "Vimeo", "Wistia" |
| video_title | string | Yes | Title of the video | "How to Build a Rocket" |
| visible | boolean | Yes | Visibility status of the element | True, False |
