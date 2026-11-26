---
title: Website RSS
date: 2026-03-28 23:56
cover: /img/markus-winkler-GdpDAj8unB4-unsplash.jpg
coverInfo:
  author: Markus Winkler
  url: https://unsplash.com/photos/a-wooden-block-spelling-subscribe-on-a-table-GdpDAj8unB4
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

No additional plugins are required; an RSS feed is generated automatically.

Supported configuration options:

```yaml _config.linen.yml
feed:
  path: /feed.xml                  # Defaults to /feed.xml
  limit: 10                        # Defaults to 10 (number of recent posts)
  icon: /linen-theme/favicon.svg   # Recommended: set an explicit site path or full URL
```

You may customize the three options above. Since `icon` does not have a built-in fallback, it is recommended to specify a site path or full `https://` URL explicitly.

To disable the built-in RSS generator (for example, if you use another RSS plugin), add the following to `_config.linen.yml`:

```yaml _config.linen.yml
feed: false
```
