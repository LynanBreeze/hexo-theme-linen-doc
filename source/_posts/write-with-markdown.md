---
title: Markdown Syntax
date: 2026-03-28 22:00
excerpt: Some examples of Markdown syntax.
appendRawMarkdown: true
cover: /img/markus-spiske-mygLDe2KvSg-unsplash.jpg
coverInfo:
  author: Markus Spiske
  url: https://unsplash.com/photos/a-white-wall-with-a-clock-on-it-mygLDe2KvSg
toc: true
translations: ['zh-CN']
---

Thanks to [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all Markdown syntax elements. Since it is impossible to cover every edge case, if you need more information about any of these elements, please consult the reference guides for [Basic Syntax](https://www.markdownguide.org/basic-syntax/) and [Extended Syntax](https://www.markdownguide.org/extended-syntax/).

## Basic Syntax

The following are the elements outlined by John Gruber in his original design document. All Markdown applications support these elements.

### Headings

# H1

## H2

### H3

## Bold

**Bold text**

## Italic

_Italic text_

## Blockquotes

> Blockquote

## Ordered Lists

1. First item
2. Second item
3. Third item

## Unordered Lists

- First item
- Second item
- Third item

## Horizontal Rules

---

## Strikethrough

~~The world is flat.~~

## Links

[Markdown Guide](https://www.markdownguide.org)

## Footnotes

Footnotes let you add notes and references without cluttering the body of your article. When you create a footnote, a superscript number with a link appears where you added the footnote reference, jumping readers down to the footnote content at the bottom of the page.

Here is a simple footnote[^1].

## Images

![The magnificent north coast of Madeira](https://images.unsplash.com/photo-1619898331052-ac35cf01ec84?q=80&w=4686&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

## Tables

| Syntax | Description |
| ---- | ---- |
| Header | Title |
| Paragraph | Text |

## Code

`const a = 1;`

## Code Blocks

Code blocks come with a built-in one-click copy button.

```json example.json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Folded Code Blocks

For longer snippets, add the `folded` keyword to the code block's title (info string) to collapse it by default with an expand/collapse toggle:

````markdown
```javascript long-example.js folded
// Code content...
```
````

Live example:

```javascript long-example.js folded
function greet(name) {
  const greeting = `Hello, ${name}!`;
  return greeting;
}

const users = ['Alice', 'Bob', 'Charlie'];
users.forEach((user) => {
  console.log(greet(user));
});
```

## Collapsible Details

Linen styles native HTML `<details>` / `<summary>` blocks for collapsible supplementary notes:

<details>
<summary>Click to expand additional notes</summary>

You can place any Markdown paragraphs or supplementary explanations here without distracting from the main flow.

</details>

## Math Formulas

Linen includes built-in server-side KaTeX rendering. See [LaTeX Math Formulas](/hexo-theme-linen-doc/latex/).

## Task Lists

- [x] Write press release

- [ ] Update website

- [ ] Contact media

[^1]: This is the first footnote.
