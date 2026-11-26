---
title: LaTeX Math Formulas
excerpt: Write crisp math formulas with Linen's built-in server-side KaTeX rendering.
date: 2026-03-28 23:51
cover: /img/klara-kulikova-PgrSvkU1_4Y-unsplash.jpg
coverInfo:
  author: Klara Kulikova
  url: https://unsplash.com/photos/PgrSvkU1_4Y
series: User-Guide
tags: [Quick-Start, Configuration]
appendRawMarkdown: true
tocType: flat
latex: true
translations: ['zh-CN']
---

## Overview

Linen includes built-in server-side [KaTeX](https://katex.org/) rendering with no extra Hexo math plugins required:

- **Build-time pre-rendering**: Formulas are rendered to HTML during `hexo generate`, with zero client-side JavaScript math parsing overhead.
- **On-demand assets**: Bundled `katex.min.css` and `.woff2` fonts are generated only when at least one post or page uses KaTeX, and the stylesheet is loaded only on pages containing rendered math.

## Global Configuration

Configure `latex` in `_config.linen.yml`:

- **Quick enable**

  ```yaml _config.linen.yml
  latex: true
  ```

- **Full options (custom CSS or KaTeX options)**

  ```yaml _config.linen.yml
  latex:
    enable: true
    css: "" # Optional local path or CDN URL for KaTeX CSS; leave empty to use bundled assets
    options:
      throwOnError: false # Default: false
      strict: ignore      # Default: "ignore"
      macros:
        "\\RR": "\\mathbb{R}"
        "\\E": "\\mathbb{E}"
  ```

## Page-level Configuration

Enable, disable, or customize KaTeX per post in Front Matter using `latex` (or its alias `math`):

```yaml
---
title: Post with Math
latex: true # Or math: true; set false to disable on a single post when enabled globally
---
```

You can also pass page-level KaTeX options and macros (merged with global `options`):

```yaml
---
title: Custom Macros Example
latex:
  enable: true
  macros:
    "\\vect": "\\mathbf{#1}"
---
```

## Syntax & Live Examples

This page has `latex: true` enabled. Below are source snippets alongside their live rendered output.

### Inline Math

Wrap single-line expressions in single dollar signs `$ ... $`:

```markdown
Mass-energy equivalence $E = mc^2$, Euler's identity $e^{i\pi} + 1 = 0$, and conditional probability $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$.
```

Rendered output: Mass-energy equivalence $E = mc^2$, Euler's identity $e^{i\pi} + 1 = 0$, and conditional probability $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$.

To prevent currency values from being misparsed as math, inline math follows strict rules:

- Cannot span multiple lines;
- Opening `$` cannot be followed by whitespace or preceded by a digit;
- Closing `$` cannot be preceded by whitespace or followed by a digit.

Values like `$100` or `from $10 to $20` remain untouched. To output a literal `$` in edge cases, escape it with `\$`.

### Display Math

Use double dollar signs `$$ ... $$` for standalone single-line or multi-line equations:

```markdown
$$
\int_{-\infty}^{+\infty} e^{-x^2}\,dx = \sqrt{\pi}
$$
```

Rendered output:

$$
\int_{-\infty}^{+\infty} e^{-x^2}\,dx = \sqrt{\pi}
$$

Multi-line `aligned` environments and matrices are supported:

```markdown
$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \mathbf{B} &= 0 \\
\nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
\nabla \times \mathbf{B} &= \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}
\end{aligned}
$$
```

Rendered output:

$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \mathbf{B} &= 0 \\
\nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
\nabla \times \mathbf{B} &= \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}
\end{aligned}
$$

Display math inside Markdown blockquotes (`>`) is also supported:

> The probability density function of the normal distribution is:
>
> $$
> f(x) = \frac{1}{\sigma \sqrt{2\pi}} \exp\left(-\frac{(x - \mu)^2}{2\sigma^2}\right)
> $$

### Automatically Skipped Regions

`$` and `$$` inside the following regions are ignored automatically:

- Markdown fenced code blocks (```` ``` ```` / `~~~`) and inline code spans (`` `$x$` ``)
- Raw HTML `<pre>`, `<code>`, `<script>`, and `<style>` blocks
- Hexo `{% codeblock %}` and `{% raw %}` tags
