---
title: 现代浏览器已经支持 CSS 嵌套
date: 2023-06-11 14:30
tags: [CSS]
---

CSS 嵌套是一种 CSS 预处理器的特性，它可以让你在 CSS 中使用类似于 HTML 的嵌套语法，从而让你的 CSS 更加简洁易读。以前，我们需要使用 Sass、Less 等 CSS 预处理器才能使用 CSS 嵌套，但是现在，CSS 嵌套已经被纳入了 CSS 规范，现代浏览器已经支持 CSS 嵌套语法。详细的兼容性可查看 [caniuse](https://caniuse.com/css-nesting)。

## 嵌套规则

原版 CSS 中，如果你想对子元素设置样式，那么你需要在父元素的选择器后面添加一个空格，然后再写子元素的选择器。

```css
.parent-selector {
  color: red;
}

.parent-selector .child-selector {
  color: blue;
}
```

转换为 CSS 嵌套语法，代码如下：

```css
.parent-selector {
  color: red;

  .child-selector {
    color: blue;
  }
}
```


