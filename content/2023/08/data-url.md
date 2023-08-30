---
title: Data URL 在浏览器中的妙用
date: 2023-08-20 20:30
tags: [浏览器, ES6]
---

Data URL 是一种使用 `data:` 协议特殊的 URL，它可以将文件内容嵌入到 URL 中。Data URL 的格式如下：

```
data:[<mediatype>][;base64],<data>
```

有四个部分组成：

- `data:` 协议头
- `<mediatype>` 媒体类型，可选
- `;base64` 表示数据使用 base64 编码，可选
- `<data>` 数据内容

一个简单的例子：

```html
data:text/plain;base64,SGVsbG8sIFdvcmxkIQ%3D%3D 
```

将上述 Data URL 复制到浏览器地址栏中，浏览器会自动解析并显示出来，如下：

```
Hello, World!
```


## Data URL 的妙用

Data URL 格式中的 `mediatype` 支持 `text/html`，这意味着我们可以将 HTML 文件嵌入到 URL 中，从而实现在浏览器中直接运行 HTML 文件。
借助于现代浏览器支持的 HTML5/CSS3/ES6 特性，我们可以在浏览器中运行一些简单的程序，来实现各种各样的功能。将下面的 Data URL 复制到浏览器地址栏中，即可查看效果。


  