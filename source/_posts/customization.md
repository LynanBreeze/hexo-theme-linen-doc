---
title: Customization Settings
date: 2026-03-28 23:58
excerpt: Configure the customized settings for your site.
categories: Getting-Started
cover: /img/vinicius-amnx-amano-17NCG_wOkMY-unsplash.jpg
coverInfo:
author: Markus Winkler
url: https://unsplash.com/photos/a-close-up-of-a-street-sign-on-the-ground-newg0EE_rxw
series: User-Guide
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

## Header Logo

Edit the `_config.linen.yml` file located in your site's root directory (create it if it doesn't exist), and then add the following content format to the file:

```yaml _config.linen.yml
logo:
src: '/img/linen-logo.svg'
width: 225
height: 42
```

Please replace `src`, `width`, and `height` with the corresponding file path and dimensions of your logo image.

## Header Navigation Menu

Add the following content format to `_config.linen.yml`:

```yaml _config.linen.yml
navItems:
- name: Archives
path: /archives/
```

## Site Information

Add the following content format to `_config.linen.yml`:

```yaml _config.linen.yml
info:
site_desc: Live Young n Act Now.
avatar: https://xxx.xxx/xx.jpg
siteCardBg: https://xxx.xxx/xx.jpg
```