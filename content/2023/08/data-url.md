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
  