---
title: Coverless Pure-Text Layout Sample
date: 2026-06-28 10:00
excerpt: When an article omits a cover image, list cards automatically expand into a full-width pure-text layout, and the post view skips the hero banner to enter the reading flow immediately.
tags: [Sample, Typography]
categories: Essays
appendRawMarkdown: true
tocType: flat
translations: ['zh-CN']
---

Not every article needs a hero image. For technical notes, reading reflections, or short updates, omitting `cover` and `thumbnail` brings readers straight into the text.

## List & Article View Behavior

In Linen, posts without a cover image adapt cleanly across both views:

- **Home & Archive Lists**: The right-hand thumbnail area is omitted so the title, tags, excerpt, and metadata span the full width of the card without empty placeholders or generic fallback images.
- **Article Page**: The `.post-cover-img-wrap` header banner is skipped, starting the page directly with the title, publish date, category, and estimated reading time.

> Good typography does not rely on decoration—measured whitespace, steady line height, and clear hierarchy carry the visual focus on their own.[^1]

## Paragraphs & Code Sample

For long-form reading, a warm linen canvas paired with a comfortable measure helps reduce eye fatigue. Body copy uses a serif stack while metadata stays crisp in system sans-serif and code blocks render in monospace, giving each layer of information a natural contrast.

```yaml _posts/pure-text-sample.md
---
title: Coverless Pure-Text Layout Sample
date: 2026-06-28 10:00
tags: [Sample, Typography]
categories: Essays
---
```

### When to Skip a Cover Image

1. **Essays & Short Notes**: Capture an idea right away without breaking flow to hunt for a photo.
2. **Changelogs & Documentation**: Keep headings, lists, and code snippets immediately visible above the fold.
3. **Text-First Excerpts**: Pair blockquotes and footnotes for a clean editorial column feel.

[^1]: This sample intentionally omits `cover` and `thumbnail` to demonstrate how coverless posts render in the home list, archive pages, and article view.
