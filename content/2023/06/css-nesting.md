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

使用 & 符号可以引用父元素的选择器，这在原版 CSS 中是做不到的。

```css
.parent-selector {
  color: red;

  &:hover {
    color: blue;
  }
}
```

目前 CSS 嵌套语法支持所有用符号开头的子选择器，如下：

```css
main {
 .bar { ... } 
 #baz { ...}
 :has(p) { ... }
 ::backdrop { ... }
 [lang|="zh"] { ... }
 * { ... }
 + article { ... }
 > p { ... }
 ~ main { ... }
}
```

## 注意事项

因为浏览器解析引擎的限制，CSS 嵌套语法不支持字母开头的子选择器（元素选择器），如下：

```css
main {
  article { ... } /* 不支持 */
}
```

在这种情况下，可以在子元素前面添加 & 符号，如下：

```css
main {
  & article { ... }
}
```

或者使用 `:is()` 伪类，如下：

```css
main {
  :is(article) { ... }
}
```

## 想法
很高兴现代浏览器已经支持 CSS 嵌套语法，至少在一些对兼容性要求不太高的项目中可以方便地使用 CSS 嵌套来提升开发效率。随着 CSS 规范的不断完善，相信类似于嵌套之类新的特性会越来越受欢迎。
