---
title: Article Configuration
excerpt: Custom Front Matter options supported by Linen.
date: 2026-03-28 23:53
cover: /img/freestocks-VFs2fZEVkXo-unsplash.jpg
coverInfo:
  author: freestocks
  url: https://unsplash.com/photos/top-view-of-opened-magazine-near-up-of-coffee-VFs2fZEVkXo
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
customComments:
  - text: For example, right here
    index: 0
    comment: Do you see the hover text?
translations: ['zh-CN']
copyright: true
donates:
  - type: wechat
    qrcode: /img/freestocks-VFs2fZEVkXo-unsplash.jpg
sponsors:
  - name: Me
    amount: A cup of coffee
    date: 2026-04-12
---

## Subtitle

Add a subtitle that renders alongside the post title in the article header, post lists, banner posts, series directory, page `<title>`, and RSS feed:

```yaml
subTitle: Advanced Guide
```

## Cover, Thumbnail & Share Image

Post image-related Front Matter options:

```yaml
cover: /img/cover.jpg
coverPlaceholder: /img/cover-blur.jpg  # Optional placeholder image for the cover (URL or Base64)
thumbnail: /img/thumb.jpg              # Optional thumbnail for post lists/banners/related posts/travel cards (takes priority over cover)
ogImage: /img/og.jpg                   # Optional Open Graph og:image cover
```

Social share image (`og:image`) resolution priority: `seriesInfo.cover > ogImage > cover > info.siteCardBg`.

## Cover Information

In the bottom-right corner of the cover image, you can add either author credits or location information (choose one):

- Author Information
  ```yaml
  coverInfo:
    author: freestocks
    url: https://unsplash.com/photos/top-view-of-opened-magazine-near-up-of-coffee-VFs2fZEVkXo
  ```
- Location Information
  ```yaml
  coverInfo:
    location: Macau · Municipal Affairs Bureau Building
    url: https://maps.apple.com/place?address=Avenida%20de%20Almeida%20Ribeiro%20No.%20163,%20Macao%20SAR,%20China&coordinate=22.193346,113.539592&name=%E5%B8%82%E6%94%BF%E7%BD%B2&place-id=IC211FBD448B1E6C&map=explore
  ```

## Hover Text

Sometimes you want to attach explanatory notes without cluttering prose with parentheses (like this). Add `customComments` to attach hoverable tooltip notes to specific occurrences of text:

For example, right here:

```yaml
customComments:
  - text: For example, right here
    index: 0
    comment: Do you see the hover text?
```

## Hiding Posts & SEO Control

Remove a post from the homepage or archives, or prevent search engine indexing (the post page is still generated and directly accessible by URL):

```yaml
hide:
  recent: true   # Exclude from homepage recent posts
  archive: true  # Exclude from archives and site post counts
  seo: true      # Output <meta name="robots" content="noindex, nofollow">
```

## PhotoSwipe Plugin

Powered by [https://photoswipe.com/](https://photoswipe.com/).

- Global Enable: Add `photoswipe: true` to `_config.linen.yml`.
- Page-level Disable: When globally enabled, add `photoswipe: false` in a post's Front Matter to disable it on that page.

If a post contains no images or Live Photos, PhotoSwipe assets are not loaded.

## Table of Contents (TOC)

Three TOC modes are supported in Front Matter:

- Hidden: `toc: false`
- Expanded by default: `tocType: flat`
- Auto collapse/expand: <small>(Leave blank / omit)</small>

## Image Lazy Loading

Enable lazy loading explicitly in `_config.linen.yml`:

```yaml _config.linen.yml
lazyload:
  enable: true
```

Run `hexo clean` (or `npm run clean`) after changing this setting so already-built posts are regenerated.

You can also override `keepPlaceholder` for a specific post in Front Matter:

```yaml
lazyload:
  keepPlaceholder: false
```

To skip lazy loading for individual images (or `<video>` / `<iframe>` elements), use any of the following:

- `![no-lazy](https://abc.com/def.jpg)`
- `![This is an image $no-lazy](https://abc.com/def.jpg)`
- `<img no-lazy src="https://abc.com/def.jpg" alt="def">`

For `$no-link`, `$aspect-ratio`, `$placeholder`, `assets-db/imgs/*.json`, and HDR switching, see [HDR & Advanced Image Settings](/hexo-theme-linen-doc/advanced-images/).

## Raw Markdown Toggle

Enable a "Switch to Raw Markdown Content" button in the post metadata bar so readers can inspect or copy the original Markdown source:

```yaml
appendRawMarkdown: true
```

## Post Age Notice

For time-sensitive tutorials or notes, enable `ageWarning: true`. When a post is older than **180 days**, a notice banner is automatically shown at the top of the article:

```yaml
ageWarning: true
```

## Reading Time & Word Count

By default, estimated reading time, word count, and photo count are displayed together. To hide the word/photo count and show only the estimated reading time:

```yaml
readTime:
  count: false
```

## Disabling Comments Per Post

When Gitalk is enabled globally, you can disable comments on a single post:

```yaml
comment: false
```

## Page-level `<head>` Injection

Inject extra stylesheets or scripts into `<head>` for a single post:

```yaml
heads:
  - <link rel="stylesheet" href="/css/custom-post.css">
  - <script src="/js/custom-post.js" defer></script>
```

## Language & Translations

Override the language for a single post (affecting date formatting, word counting, Gitalk language, and `og:locale`), and declare translated locales for the header language switcher (used together with `siteOriginLocaleMap` in `_config.linen.yml`):

```yaml
language: en
translations: ['zh-CN']
```

## Related Posts

Posts sharing 2 or more tags are automatically treated as related and shown at the bottom of the article. To hide related posts on a specific page:

```yaml
showRelated: false
```

## Copyright Notice

Display a copyright notice banner at the bottom of the article:

```yaml
copyright: true
```

## Donate QR Codes & Sponsor List

Configure donation QR codes in Front Matter:

```yaml
donates:
  - type: wechat
    qrcode: /img/wx_qr.jpg
```

To display a thank-you list of sponsors below the donate button, add `sponsors` (note: `sponsors` renders only when `donates` is also configured):

```yaml
sponsors:
  - name: Me
    amount: A cup of coffee
    date: 2026-04-12
```

## More Dedicated Guides

Additional Front Matter features have their own dedicated guides:

- **Series & Travel Map** (`series`, `mapPlace`): see [Series & Travel Map](/hexo-theme-linen-doc/series-and-travel/)
- **LaTeX Math Formulas** (`latex` / `math`): see [LaTeX Math Formulas](/hexo-theme-linen-doc/latex/)
- **HDR Image Switching** (`hdrSwitch`, `hdrAssetsPrefix`): see [HDR & Advanced Image Settings](/hexo-theme-linen-doc/advanced-images/)
