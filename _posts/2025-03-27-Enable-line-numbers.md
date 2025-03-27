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

  ```scss
 .rouge-table {
    width: 100%;
    table-layout: fixed; // 固定表格布局
    border-collapse: collapse;


    .rouge-gutter {
      width: 3.5em; // 增加行号列宽度
      min-width: 3.5em; // 防止内容压缩
      user-select: none; // 禁用行号选择

      pre {
        color: #666; // 行号颜色
        text-align: right; // 右对齐
      }

      td {
        padding: 0;
        vertical-align: top; // 顶部对齐
      }
    }

    .rouge-code {
      width: 100%; // 代码列填满剩余空间

      pre {
        overflow-x: auto; // 恢复水平滚动
        white-space: pre; // 保持原有空白处理
        margin: 0;
        padding: $base-spacing;

        code {
          white-space: pre; // 重置代码换行方式

          * {
            white-space: pre; // 移除强制不换行设置
          }
        }
      }
    }

    .rouge-gutter pre.lineno {
      white-space: pre-wrap;
      /* 允许换行 */
      display: block;
      /* 确保块级显示 */
      line-height: 23px;
      /* 设置行高匹配代码行 */
    }

    .highlight table td {
      padding: 5px;
    }

    .highlight table pre {
      margin: 0;
    }

  ```

</details>
