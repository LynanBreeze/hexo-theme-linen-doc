---
title: HDR & Advanced Image Settings
excerpt: Learn about HDR/SDR image switching, inline Markdown image directives, video/Live Photo lazy loading, and the assets-db/imgs metadata store.
date: 2026-03-28 23:50
cover: /img/mariola-grobelska-rxFb6meV3ck-unsplash.jpg
coverInfo:
  author: Mariola Grobelska
  url: https://unsplash.com/photos/rxFb6meV3ck
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
hdrSwitch: true
hdrAssetsPrefix: hdr-demo/hdr
translations: ['zh-CN']
---

## HDR / SDR Image Switching

For photography posts containing HDR gain-map images, Linen supports live switching between HDR and SDR assets without reloading the page.

### Live Demo

This page is configured with `hdrSwitch: true` and `hdrAssetsPrefix: hdr-demo/hdr`. On an HDR-capable display and browser, click the **HDR switch** in the top navigation bar to toggle the sample photo below between HDR and SDR:

![HDR / SDR Switch Demo (Photo copyright © lynan)](/img/hdr-demo/sdr/DSC08834.jpg)

### 1. Enabling HDR Switching

Add `hdrSwitch` and `hdrAssetsPrefix` to your post's Front Matter:

```yaml
---
title: Iceland Aurora Photography
hdrSwitch: true
hdrAssetsPrefix: photos/hdr # Or a full prefix like https://cdn.example.com/photos/hdr
---
```

### 2. Path Naming Convention

- `hdrAssetsPrefix` must contain `/hdr` (using a relative segment such as `hdr-demo/hdr` works seamlessly for both root and subpath deployments).
- Linen automatically derives the SDR prefix by replacing `/hdr` with `/sdr` (e.g. `hdr-demo/sdr`).
- Reference `/sdr/` URLs by default in your Markdown. When HDR is enabled, Linen swaps the SDR prefix to the HDR prefix across rendered `<img>` elements, lazyload `data-content` payloads, and PhotoSwipe lightbox links.

### 3. Detection & Interaction

- Linen checks both `matchMedia('(dynamic-range: high)')` and `CSS.supports('dynamic-range-limit: no-limit')` to confirm actual HDR image rendering support.
- On capable devices with viewport width ≥ `500px`, HDR mode activates automatically on load. Readers can toggle HDR/SDR manually at any time via the header switch button.
- When viewing image EXIF inside PhotoSwipe, active HDR photos also display an `HDR` badge.

## Inline Markdown Image Directives

When `lazyload.enable: true` is enabled in `_config.linen.yml`, you can embed control directives directly in an image's `alt` text (directives are stripped automatically from rendered captions):

| Directive | Behavior | Example |
| --- | --- | --- |
| `no-lazy` / `$no-lazy` | Skip lazy-loading wrapper for this image | `![Landscape $no-lazy](/img/a.jpg)` |
| `no-link` / `$no-link` | Disable PhotoSwipe lightbox link on click | `![Diagram $no-link](/img/b.jpg)` |
| `$aspect-ratio=W/H=aspect-ratio` | Specify placeholder aspect ratio to prevent layout shift | `![Wide shot $aspect-ratio=16/9=aspect-ratio](/img/c.jpg)` |
| `$placeholder=value=placeholder` | Set a per-image placeholder (URL or `data:image/...`) | `![Caption $placeholder=https://.../blur.jpg=placeholder](/img/d.jpg)` |

When writing raw HTML `<img>` tags, you can also use HTML attributes directly:

```html
<img
  src="https://cdn.example.com/photo.jpg"
  alt="Photo description"
  style="aspect-ratio: 3/2;"
  data-placeholderimg="data:image/jpeg;base64,..."
  pswp-src="https://cdn.example.com/photo-original.jpg"
/>
```

- `no-lazy` and `no-link` work directly as boolean HTML attributes on `<img>`.
- `pswp-src` specifies a higher-resolution original image to load inside PhotoSwipe.

## Video, `<iframe>`, and Live Photos

With `lazyload.enable: true`, `<video>` and `<iframe>` tags are lazily loaded too (also supporting `no-lazy` and `style="aspect-ratio: ..."`).

In addition, `<iframe>` embeds matching `/static/live-photo/` (with `picUrl` / `photoSrc` and `videoUrl` / `videoSrc` query parameters, plus optional `muted`, `loop`, and `volume`) integrate automatically with PhotoSwipe when `photoswipe: true` is enabled, offering a **LIVE** playback trigger directly inside the lightbox.

## Image Metadata Store (`assets-db/imgs/*.json`)

For photo-heavy blogs, instead of writing dimensions, placeholders, or EXIF strings inline in Markdown, place one or more `.json` files (each containing an array of image objects) under `assets-db/imgs/` in your site root.

During build, Linen matches images by URL (`pathname + search + hash`, ignoring protocol and host) for both body images and post covers, injecting aspect ratios, placeholders, localized captions, and EXIF metadata automatically.

### Example JSON

```json assets-db/imgs/2026.json
[
  {
    "url": "https://cdn.example.com/photos/sdr/tokyo-tower.webp",
    "width": 1600,
    "height": 1067,
    "originalUrl": "https://cdn.example.com/photos/sdr/tokyo-tower-full.jpg",
    "placeholder": "blurhash:LGF5]+Yk^6#M@-5c,1J5@[or[Q6.",
    "alt": "暮色中的东京塔",
    "alten": "Tokyo Tower at Dusk",
    "caption": "拍摄于六本木展望台",
    "caption_en": "Taken from Roppongi Hills",
    "exif": "{Sony A7C II}{ISO 100}{35mm}{f/2.8}{1/500s}{0 EV}{FE 35mm F1.8}{1}",
    "location": "https://maps.apple.com/?ll=35.6586,139.7454",
    "locationText": "东京塔",
    "locationText_en": "Tokyo Tower",
    "noLink": false
  },
  {
    "url": "https://cdn.example.com/photos/sdr/tokyo-tower-full.jpg",
    "width": 4000,
    "height": 2667
  }
]
```

### Field Reference

| Field | Description |
| --- | --- |
| `url` | Image URL matched against post `src` and `cover` values. |
| `width` / `height` | Pixel dimensions used for placeholder aspect ratios and PhotoSwipe sizing. |
| `originalUrl` | High-resolution original URL for PhotoSwipe; if another entry matches `originalUrl`, its `width`/`height` are used for the lightbox. |
| `placeholder` | Placeholder image URL, Base64 `data:image/...`, or BlurHash string prefixed with `blurhash:`. |
| `alt` / `alt<lang>` | Caption displayed beneath the image (prefers locale-suffixed fields like `alten` or `altzh-CN`, falling back to `alt`). |
| `caption` / `caption_<lang>` | Caption displayed inside the PhotoSwipe lightbox (e.g., `caption_en`, `caption_zh-CN`). |
| `exif` | Eight brace-delimited EXIF slots in fixed order: `{camera}{iso}{focusLength}{aperture}{shutterSpeed}{ev}{lens}{isHDR}` (leave empty slots as `{}`). |
| `location` | Map link URL displayed alongside EXIF in the lightbox. |
| `locationText` / `locationText_<lang>` | Display label for the location link (supports locale suffixes like `locationText_en`). |
| `noLink` | Set to `true` to disable PhotoSwipe lightbox linking for this image. |
