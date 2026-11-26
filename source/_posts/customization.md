---
title: Customization Settings
date: 2026-03-28 23:58
excerpt: Configure the customized settings for your site.
categories: Getting-Started
cover: /img/vinicius-amnx-amano-17NCG_wOkMY-unsplash.jpg
coverInfo:
  author: Vinicius "amnx" Amano
  url: https://unsplash.com/photos/17NCG_wOkMY
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

## Header Logo

Edit the `_config.linen.yml` file located in your site's root directory (create it if it doesn't exist), and add the following configuration:

```yaml _config.linen.yml
logo:
  src: /img/linen-logo.svg
  width: 225
  height: 42
```

Replace `src`, `width`, and `height` with your logo image path and dimensions.

If you prefer a text-only logo, you can configure `text` instead:

```yaml _config.linen.yml
logo:
  text: My Blog
```

## Favicon & Asset Version

You can customize the site favicon and the cache-busting query version appended to CSS/JS assets (`?v=...`) in `_config.linen.yml`:

```yaml _config.linen.yml
icon: /img/favicon.svg # Defaults to /linen-theme/favicon.svg
version: 1.0.0
```

## Header Navigation Menu

Add the following to `_config.linen.yml`:

```yaml _config.linen.yml
navItems:
  - name: Archives
    path: /archives/
```

## Site Information

Add the following to `_config.linen.yml`:

```yaml _config.linen.yml
info:
  site_desc: A Simple Hexo Theme.
  avatar: https://xxx.xxx/xx.jpg
  github: https://github.com/your-name/your-repo
  about: /about/
  siteCardBg: https://xxx.xxx/xx.jpg
  copyright: All content on this site is licensed under CC BY-NC-SA 4.0.
  registration: ICP-22222222
```

- `avatar`: Author avatar image shown in the sidebar. Free avatar illustrations can be found at https://unsplash.com/s/illustrations/avatar?license=free.
- `github`: GitHub icon link on the right side of the top navigation bar.
- `about`: Destination link for the footer "About This Site" heading (supports internal paths like `/about/` or full external URLs; if omitted, renders as plain non-clickable text).
- `siteCardBg`: Default Open Graph cover image (`og:image`) when sharing the site.
- `copyright`: Custom copyright license text displayed in the footer `©` popover; falls back to the theme's built-in localized text if omitted.
- `registration`: Optional footer ICP/registration notice.

## Lazy Loading

Lazy loading for images, videos, and `<iframe>` embeds must be explicitly enabled (`enable: true`) in `_config.linen.yml`:

```yaml _config.linen.yml
lazyload:
  enable: true
  loadingImage: ""                                       # Empty by default (warm-paper shimmer skeleton), or set a custom loading image path
  errorTipImage: /linen-theme/img/lazyload/error-tip.svg # Custom error placeholder image
  intersectionRatio: 0.25                                # Visible ratio to trigger loading
  placeholderRatio: 1.5                                  # Default placeholder aspect ratio (3/2 = 1.5)
  showTransition: true                                   # Enable fade-in transition
  showAltText: true                                      # Display image alt text as caption below image
  preloadCount: 5                                        # Number of images to preload
  keepPlaceholder: true                                  # Keep placeholder element after load
```

Except for `enable`, the values above are defaults and can be customized as needed. After changing `enable`, run `hexo clean` before rebuilding. For advanced placeholders, lightbox EXIF metadata, and HDR switching, see [HDR & Advanced Image Settings](/hexo-theme-linen-doc/advanced-images/).

## PhotoSwipe Lightbox

Linen bundles [PhotoSwipe](https://photoswipe.com/) and requires explicit opt-in in `_config.linen.yml`:

```yaml _config.linen.yml
photoswipe: true
```

Once enabled globally, you can still disable it per post via `photoswipe: false` in Front Matter. On posts without images or Live Photos, PhotoSwipe assets are not loaded.

## LaTeX Math Formulas

To enable built-in server-side KaTeX rendering globally, add to `_config.linen.yml`:

```yaml _config.linen.yml
latex: true
```

You can also enable it per post or customize KaTeX options/macros. See [LaTeX Math Formulas](/hexo-theme-linen-doc/latex/) for details.

## Injecting Scripts & Styles (`heads` / `appends`)

Use `heads` to inject custom CSS or scripts inside `<head>`, and `appends` to append HTML/scripts right before `</body>` (such as analytics scripts):

```yaml _config.linen.yml
heads:
  - <script src="/path-to/your-js.js"></script>
  - <link rel="stylesheet" href="/path-to/your-css.css">
appends:
  - <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
```

> Tip: The post metadata bar includes `<span id="busuanzi_value_page_pv"></span>`, so injecting the Busuanzi script automatically displays page view counts.

## Bilingual Site Configuration

If you maintain separate Chinese and English domains (or subpaths), configure `siteOriginLocaleMap` in `_config.linen.yml`:

```yaml _config.linen.yml
siteOriginLocaleMap:
  zh-CN: https://test.cn
  en: https://test.com
```

To make the top-right language switcher link properly to matching pages:

1. **Posts**: Declare the target translation locale in each post's Front Matter, e.g. `translations: ['zh-CN']` on the English site and `translations: ['en']` on the Chinese site (both posts should share the same slug/path).
2. **Series / Categories / Tags**: Create corresponding JSON mapping files under `assets-db/` in your site root with `mappingName` pointing to the target locale's path name:
   - `assets-db/series.json`
   - `assets-db/categories.json`
   - `assets-db/tags.json`

Example `assets-db/categories.json`:

```json assets-db/categories.json
{
  "Getting-Started": {
    "mappingName": "快速开始"
  }
}
```
