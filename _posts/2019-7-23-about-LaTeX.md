---
layout: post
title: 坑关于LaTeX渲染
date: 2019-07-23
Author: shy
categories:
tags: [manufacturing process]
comments: true
---

### 关于$LaTeX$渲染

第一： 我们想到了luogu里可以直接使用`\$ \$`和`\$\$ \$\$`符号包裹$LaTeX$公式，然而因为[各种原因](https://github.com/github/markup/issues/274)，GFM不支持渲染$LaTeX$公式，因此失败。

恰巧，2019.7.23晚上有rxz的博客课，得知只要在加入$LaTeX$相关库即可`MathJax`。

百度了一番，找到了[这个](<https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages/46765337#46765337>)回答。

经过更改，在`_includes/head.html`中加入了以下代码

```html
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
      tex2jax: {
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
        inlineMath: [['$','$']],
        displayMath: [['$$','$$']]
      }
    });
  </script>
  <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> 
```

注意配置代码的格式是

` a: b,`第一要有*空格*，第二要有*逗号*(被坑过)

测试一遍，可以用luogu里的方式直接使用`\$ \$`和`\$\$ \$\$`符号包裹$LaTeX$公式。

### 大功告成
