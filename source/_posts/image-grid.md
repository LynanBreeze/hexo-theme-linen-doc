---
title: Image Layouts
excerpt: Simple layouts make for easier reading.
date: 2026-03-28 23:55
cover: /img/ivan-shimko-PhciG8fpRKw-unsplash.jpg
coverInfo:
  author: Ivan Shimko
  url: https://unsplash.com/photos/three-beach-illustrations-PhciG8fpRKw
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

By default, Markdown displays images one per line.

![](/img/duy-le-duc-GUY2f9csQbc-unsplash.jpg)

The Linen theme introduces an image container (`:::image-grid`) supporting multiple layouts. Click **Switch to Raw Markdown Content** on this page to view the exact Markdown syntax.

## Landscape Layout

:::image-grid landscape
![](/img/klara-kulikova-PgrSvkU1_4Y-unsplash.jpg)
![](/img/mariola-grobelska-rxFb6meV3ck-unsplash.jpg)
:::

## Portrait Layout

:::image-grid portrait
![](/img/kamran-norollahi-KwP58z9zJeE-unsplash.jpg)
![](/img/julian-scholl-Wf6MhLHePSI-unsplash.jpg)
![](/img/david-boca-Xqmj-oQ_Nek-unsplash.jpg)
:::

## Mixed Layouts

Six mixed aspect-ratio layouts are supported:

- **3:2 & 2:3**: `r73` (landscape left, portrait right), `r37` (portrait left, landscape right)
- **4:3 & 3:4**: `r64` (landscape left, portrait right), `r46` (portrait left, landscape right)
- **16:9 & 9:16**: `rLeftWide` (wide left, portrait right), `rRightWide` (portrait left, wide right)

:::image-grid r73
![](/img/jasper-gribble-EOMFC1NyHgM-unsplash.jpg)
![](/img/squids-z-ShAHqWGOrRU-unsplash.jpg)
:::

## Horizontal Scroll Carousel (`scroll` / `slider`)

Use `scroll` or `slider` (both are equivalent, with `scroll-snap` alignment) to display multiple photos in a horizontally scrollable strip:

:::image-grid scroll
![](/img/klara-kulikova-PgrSvkU1_4Y-unsplash.jpg)
![](/img/mariola-grobelska-rxFb6meV3ck-unsplash.jpg)
![](/img/duy-le-duc-GUY2f9csQbc-unsplash.jpg)
:::

## Tabbed Image Switcher (`switcher`)

Use `switcher` to compare multiple images in place with an animated tab bar:

- Specify tab labels explicitly with `Label | ![](image-url)`;
- Or use the image's `alt` text directly as the tab label (`alt` takes priority if both are present);
- Falls back to `1`, `2`, `3`, ... when omitted;
- Navigating slides inside the PhotoSwipe lightbox automatically keeps the active tab in sync.

:::image-grid switcher
![Option A](/img/klara-kulikova-PgrSvkU1_4Y-unsplash.jpg)
![Option B](/img/mariola-grobelska-rxFb6meV3ck-unsplash.jpg)
![Option C](/img/duy-le-duc-GUY2f9csQbc-unsplash.jpg)
:::

> Tip: A plain `:::image-grid` without a layout class automatically adapts to 2–4 columns and also supports `<iframe>` embeds (such as Live Photos).
