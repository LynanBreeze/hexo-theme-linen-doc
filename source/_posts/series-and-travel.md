---
title: Series & Travel Map
excerpt: Organize posts into multi-part series, and unlock the Travel series interactive map and route planning cards.
date: 2026-03-28 23:52
cover: /img/duy-le-duc-GUY2f9csQbc-unsplash.jpg
coverInfo:
  author: Duy Le Duc
  url: https://unsplash.com/photos/GUY2f9csQbc
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

## Series Basics

Add a `series` field in any post's Front Matter to group related articles together:

```yaml
---
title: Part One
series: User-Guide
---
```

Once configured, Linen automatically provides:

- **Dedicated series archive page**: Generated at `/series/<Series-Name>/` (paginated according to `per_page` in Hexo's `_config.yml`).
- **In-article series navigation**: Desktop sidebar directory (up to 50 posts with a link to the full series page when exceeded), bottom previous/next series navigation, and a mobile series TOC drawer.
- **Archives overview**: Automatically listed in `/archives/` and counted in the sidebar site statistics.

## Series Metadata (`assets-db/series.json`)

Create `assets-db/series.json` in your site root to configure covers, descriptions, numbering order, year dividers, and bilingual path mappings for each series:

```json assets-db/series.json
{
  "User-Guide": {
    "description": "A complete guide to configuring and using the Linen theme.",
    "cover": "/img/series-cover.jpg",
    "coverPlaceholder": "/img/series-cover-blur.jpg",
    "coverInfo": {
      "author": "Duy Le Duc",
      "url": "https://unsplash.com/photos/GUY2f9csQbc"
    },
    "noOrder": "asc",
    "yearDivider": false,
    "showMobileIndex": true,
    "mappingName": "用户指南"
  }
}
```

Supported fields:

| Field | Type | Description |
| --- | --- | --- |
| `description` | `string` | Series summary shown on the series page header and in `og:description`. |
| `cover` | `string` | Header cover image for the series page (also used as `og:image`; omitted on Travel series pages where the interactive map is shown instead). |
| `coverPlaceholder` | `string` | Placeholder image for the series cover (URL or Base64). |
| `coverInfo` | `object` | Author or location credit in the bottom-right corner of the series cover (same format as article `coverInfo`). |
| `noOrder` | `string` | Set to `"asc"` for ascending numbering (1, 2, 3...) in the mobile series drawer; defaults to descending. |
| `yearDivider` | `boolean` | Set to `true` to group entries by year with year divider headers. |
| `showMobileIndex` | `boolean` | Set to `false` to hide item numbers in the mobile series drawer (shown by default). |
| `mappingName` | `string` | Target series slug for cross-language switching (e.g., `"User-Guide"` → `"用户指南"`). |

## Travel Series Special Features

When a post's `series` is set to **`Travel`** or **`旅行`**, Linen automatically activates a travel-journal experience featuring an **interactive travel map**, **editorial travel typography**, and **automatic route planning cards**.

> Preview the live demo on this site: [**Travel Series Map Demo**](/hexo-theme-linen-doc/series/Travel/).

### 1. Interactive Travel Map

Visiting `/series/Travel/` (or `/series/旅行/`) renders an interactive Leaflet map (OpenStreetMap tiles for English sites; AMap tiles for Chinese sites) plotting all travel posts that have valid coordinates, synchronized with the place card list below (hover highlights both marker and card; multiple posts near the same coordinates automatically cluster with a badge and multi-item popup).

Coordinates can be supplied in two ways (in priority order):

- **Method 1: `mapPlace` in Front Matter**

  ```yaml
  ---
  title: Kansai Autumn Trip
  series: Travel
  mapPlace:
    coordinate: [35.0116, 135.7681] # [latitude, longitude]
    location: Kyoto, Japan
    url: https://maps.apple.com/?ll=35.0116,135.7681
  ---
  ```

- **Method 2: Auto-parsed from map URL query parameters**

  If `mapPlace.coordinate` is omitted, Linen automatically extracts `coordinate=lat,lng` or `ll=lat,lng` from `mapPlace.url` or `coverInfo.url` (such as an Apple Maps link):

  ```yaml
  ---
  title: Macau Travel
  series: Travel
  coverInfo:
    location: Macau · Municipal Affairs Bureau
    url: https://maps.apple.com/place?coordinate=22.193346,113.539592&name=%E5%B8%82%E6%94%BF%E7%BD%B2
  ---
  ```

> Displayed place name priority: `mapPlace.location > coverInfo.location > post title`. Travel posts without coordinates are omitted from the map markers.

### 2. Route Planning Cards

Inside any `Travel` / `旅行` post, a flat unordered or ordered list (at least 2 items, without nested lists, images, tables, or code blocks) placed directly under an `H2` or `H3` heading titled **`Route`**, **`Route Planning`**, **`路线`**, or **`路线规划`** (case-insensitive) is automatically transformed into a structured route card grid:

```markdown
## Route

- Tokyo 2.5 days
- Mt. Fuji 1 day (Lake Kawaguchi, Lake Yamanaka)
- Kamakura 0.5 days
```

Parsing rules & features:

- **Duration parsing**: Recognizes both English and Chinese formats such as `2 days`, `0.5 days`, `half day`, `3d`, `2 nights`, `4 hours`, `3h`, `2 日`, `3天2晚`, `半日`, `一日`, `两天`, `大阪（2日）`, etc.
- **Stop notes**: Trailing parenthetical text that is not a duration is rendered as a subtitle note beneath the stop (e.g., `Lake Kawaguchi, Lake Yamanaka`).
- **Proportional bar & summary**: When 2 or more stops have parsed durations, a color-coded proportional bar is rendered above the grid; when all stops share the same unit kind (days or nights), a total summary header (e.g., `3 STOPS · 4 DAYS`) is shown automatically.
