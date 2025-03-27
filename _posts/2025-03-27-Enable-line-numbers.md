---

layout: post
title: "启用thinkspace主题的代码块行号"
description: "fix some bugs"
comments: true
keywords: "Jekyll"
---


1.首先在`_config.yml`中启用行号
<details>
  <summary markdown="span">_config.yml修改</summary>

  ```yml
  kramdown:
  parse_block_html: true
  syntax_highlighter: rouge
  syntax_highlighter_opts:
    css_class: 'highlight'
    span:
      line_numbers: false
    block:
      line_numbers: true
      start_line: 1
  ```

</details>


2.然后需要禁用`_layouts/default.html`中的`layout: compress`，这个似乎存在bug
<details>
  <summary markdown="span">_layouts/default.html</summary>

  ```html
 ---
<!-- layout: compress -->
published: true
---
  ```

</details>

3.修改`assets/scss/_syntax-highlighting.scss`，来增加行号、表格等的样式
<details>
  <summary markdown="span">assets/scss/_syntax-highlighting.scss</summary>

  ```css
 .rouge-table {
    width: 100%;
    table-layout: fixed; 
    border-collapse: collapse;

    td {
      padding: 0;
      vertical-align: top;
    }
  }

  .rouge-gutter {
    width: 3.5em; 
    min-width: 3.5em; 
    user-select: none;

  .rouge-code {
    width: 100%;

    pre {
      color: #666;
      text-align: right;
      overflow-x: auto;
      white-space: pre; 
      margin: 0;
      padding: $base-spacing;

      code {
        white-space: pre;

        * {
          white-space: pre;
        }
      }
    }
  }

  .rouge-gutter pre.lineno {
    white-space: pre-wrap;
    display: block;
    line-height: 23px;
  }

  .highlight table td {
    padding: 5px;
  }

  .highlight table pre {
    margin: 0;
  }

  ```

</details>
