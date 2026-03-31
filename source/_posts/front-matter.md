---
title: Article Configuration
excerpt: Some custom Front Matter configurations.
date: 2026-03-28 23:53
cover: /img/freestocks-VFs2fZEVkXo-unsplash.jpg
coverInfo:
author: freestocks
url: https://unsplash.com/photos/top-view-of-opened-magazine-near-up-of-coffee-VFs2fZEVkXo
series: User-Guide
appendRawMarkdown: true
tocType: flat
customComments:
  - text: For example, right here
    index: 0
    comment: Do you see the hover text?
translations: ['zh-CN']
---

## Cover Information

In the bottom-right corner of the cover image, you can add either author credits or location information (choose one).

The format is as follows:

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

Sometimes you may wish to include explanatory notes, but you don't want to constantly append parenthetical text (like this) after your content. By adding the configuration shown below, you can attach hoverable explanatory text to specific parts of your writing. 

For example, right here:

```yaml
customComments:
  - text: For example, right here
    index: 0
    comment: Do you see the hover text?
```

## Hiding Posts

Adding the configuration below allows you to remove a post from the homepage or archive page (this does not prevent the post from being generated; the post page can still be accessed directly via its URL).

```yaml
hide:
recent: true
archive: true
```

Setting `recent: true` ensures the post does not appear on the homepage.
Setting `archive: true` ensures the post does not appear in the archives.

## PhotoSwipe Plugin

This plugin is sourced from [https://photoswipe.com/](https://photoswipe.com/). If you do not need it, you can disable it in the following ways:

Global Disable: Add `photoswipe: false` to `_config.linen.yml`.
Page-level Disable: Add `photoswipe: false` to the Front Matter of the specific post.

Note that if a post contains no images, the PhotoSwipe plugin will not be loaded—even if `photoswipe: false` has not been explicitly specified.

## Table of Contents (TOC)

There are three configuration options for the Table of Contents within the Front Matter:

- Hidden: `toc: false`
- Expanded: `toc: flat`
- Automatic: <small>(Leave blank/Add nothing)</small>

## Image Lazy Loading

This feature is enabled by default. If you do not need it, you can disable it in the following way:

Global Disable: Add the following to `_config.linen.yml`:

```_config.linen.yml
lazyload:
enable: false
```

After doing so, you must run `npm run clean` to clear the previously built posts; otherwise, the change will not take effect on posts that have already been generated.

If you wish to disable lazy loading for specific images only, you can reference those images using one of the following formats:

- `![no-lazy](https://abc.com/def.jpg)`

- `![This is a image $no-lazy](https://abc.com/def.jpg)`

- `<img no-lazy src="https://abc.com/def.jpg" alt="def">`