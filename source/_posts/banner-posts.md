---
title: Banner Posts
date: 2026-03-28 23:57
cover: /img/vackground-com-hDQ-dUjQN8E-unsplash.jpg
coverInfo:
author: vackground.com
url: https://unsplash.com/photos/a-blue-and-white-abstract-background-with-hexagonal-shapes-hDQ-dUjQN8E
series: User-Guide
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

You can configure a total of four posts—consisting of one large featured post and three smaller ones—to appear in the Banner section at the top of the site's homepage.

The result looks like this:

![](/img/banner-posts.jpg)

Simply add content in the following format to your `_config.linen.yml` file:

```yaml _config.linen.yml
topArticles:
- _posts/quick-start.md
- _posts/lorem.md
```

Restart Hexo to preview the changes.

It is worth noting that while you can list more than four entries under `topArticles`, the theme will only render the first four **valid posts**.

A "valid post" refers to an actual, existing article file; if you configure an entry pointing to a non-existent file, that specific record will be filtered out.

```yaml _config.linen.yml
topArticles:
- _posts/fake-1.md
- _posts/fake-2.md
- _posts/quick-start.md
- _posts/lorem.md
```

In this example, since `fake-1.md` and `fake-2.md` do not actually exist, their presence in the list does not prevent `quick-start.md` from being recognized as the first valid post.