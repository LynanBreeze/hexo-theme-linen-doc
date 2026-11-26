---
title: Comment Plugins
date: 2026-03-28 23:54
cover: /img/volodymyr-hryshchenko-V5vqWC9gyEU-unsplash.jpg
coverInfo:
  author: Volodymyr Hryshchenko
  url: https://unsplash.com/photos/three-crumpled-yellow-papers-on-green-surface-surrounded-by-yellow-lined-papers-V5vqWC9gyEU
series: User-Guide
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

Linen bundles [Gitalk](https://github.com/gitalk/gitalk) with lazy initialization (assets only load once the reader scrolls past the middle of the article or reaches the comment section).

To enable Gitalk, add the following configuration to `_config.linen.yml`:

```yaml _config.linen.yml
comment:
  client_id: ****
  client_secret: ***
  repo: ***
  owner: ***
  admin:
    - ***
  pager_direction: last            # Optional, defaults to last (newest first)
  proxy: https://your-proxy.example.com/?url=https://github.com/login/oauth/access_token # Optional, replace with your own CORS proxy
```

> Notes:
> - The comment UI language automatically follows the post's `language` or the site's `_config.yml` `language`.
> - To disable comments on a specific post, add `comment: false` to its Front Matter.

## Configuration Guide

> The following steps are adapted from the [Icarus User Guide - Comment Plugins](https://ppoffice.github.io/hexo-theme-icarus/Plugins/Comment/icarus%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97-%E7%94%A8%E6%88%B7%E8%AF%84%E8%AE%BA%E6%8F%92%E4%BB%B6/#Gitalk).

1. Log in to GitHub and [click here to register](https://github.com/settings/applications/new) a new OAuth application.
   Fill in the "Application name", "Homepage URL", and "Application description" fields.
   Then enter your blog's root URL in "Authorization callback URL", and click "Register application".

    <img style="max-width: 500px;" alt="Register OAuth Application - GitHub" src="/hexo-theme-linen-doc/img/gitalk-register-application.jpg">

2. Copy the "Client ID" and "Client Secret" values into your theme configuration:

    <img style="max-width: 500px;" alt="OAuth Application Settings - GitHub" src="/hexo-theme-linen-doc/img/gitalk-application-settings.jpg">

   For example, given the "Client ID" and "Client Secret" below:

    ```text GitHub OAuth Application
    Client ID
    xxxxxxxxxxxxxxxxxxxx
    Client Secret
    xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    ```

   The corresponding Gitalk configuration would be:

    ```yaml _config.linen.yml
    comment:
      client_id: xxxxxxxxxxxxxxxxxxxx
      client_secret: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
      repo: Some-of-Your-GitHub-Repo
      owner: your_github_name
      admin:
        - your_github_name
      pager_direction: last           # Optional, defaults to last
      proxy:                          # Optional, CORS proxy URL
    ```

3. For further details on Gitalk options, please refer to the [Gitalk documentation](https://github.com/gitalk/gitalk).
