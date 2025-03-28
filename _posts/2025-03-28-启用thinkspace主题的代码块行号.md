---

layout: post
title: "启用thinkspace主题的代码块行号"
description: "fix some bugs"
comments: true
keywords: "Jekyll"
---


1.首先在`_config.yml`中关闭rouge渲染
<details>
  <summary markdown="span">_config.yml修改</summary>
```yml
highlighter: none  
```

</details>


2.然后禁用`_layouts/default.html`中的`layout: compress`，这个似乎存在bug
<details>
  <summary markdown="span">_layouts/default.html</summary>

  ```html
 ---
<!-- layout: compress -->
published: true
---
  ```

</details>

3.去[prismjs官网](https://prismjs.com/download.html)选择主题、渲染语言和插件下载js和css，可以放到`assets`文件夹目录下，并在`_include/head.html`里添加引用
```html
<script src="/assets/js/prism.js"></script>
<link rel="stylesheet" href="/assets/css/prism.css">
```
行号是依赖于`line-numbers`类，所以需要在`_include/footer.html`添加js来依次给代码块添加该类，js来自参考链接
```html
<script>
var pres = document.getElementsByTagName("pre");
for(var i = 0; i < pres.length; i++){
    var pre = pres[i];
    if(pre.childNodes[0].nodeName == "CODE"){
        pre.setAttribute("class","line-numbers");
    }
}
</script>
```

4.如果此时无法显示行号，需要修改`assets/css/prism.css`，来增加行号的样式
<details>
  <summary markdown="span">assets/css/prism.css</summary>

  ```css
pre[class*=language-].line-numbers.line-numbers {
  padding-left: 3.8em !important; /* 恢复左侧留白 */
}

pre[class*=language-].line-numbers.line-numbers code {
  padding-left: 0 !important; /* 移除代码区域的留白 */
}

pre[class*=language-].line-numbers.line-numbers .line-numbers-rows {
  left: -3.8em !important; /* 行号列向左偏移到留白区域 */
}

  ```

</details>

大功告成！

---

参考链接

[为 jekyll 中的代码块添加行号 - LIUMH的博客](https://hugueliu.github.io/2019/12/28/add_line_number_for_code_block_in_jekyll/)
