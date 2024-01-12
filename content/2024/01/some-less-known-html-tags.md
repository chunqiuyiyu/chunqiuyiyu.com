---
title: 一些不常见但好用的 HTML 标签
date: 2024-01-06 10:00
tags: [HTML, UI]
---

在构建网页时的三大基础技术（HTML/JS/CSS）中，HTML 可以说是最不起眼的一个了。但是随着 HTML5 的发展，HTML 的功能越来越强大，也越来越有趣。本文就来介绍一些不常见但好用的 HTML 标签。

## `<details>` 和 `<summary>`

`<details>` 标签用于包裹一个可折叠的内容，而 `<summary>` 标签则用于指定折叠内容的标题。这两个标签的使用方法如下：

```html
<details>
  <summary>折叠内容的标题</summary>
  折叠内容
</details>
```

<details>
  <summary>折叠内容的标题</summary>
  折叠内容
</details>

可以使用 `open` 属性来指定默认是否展开。

## `<progress>`

`<progress>` 标签用于显示进度条。它有两个属性：`value` 和 `max`，分别用于指定当前进度和最大进度。

```html
<progress value="50" max="100"></progress>
```

<progress value="50" max="100"></progress>

可以使用 ARIA（Accessible Rich Internet Applications，无障碍富互联网应用）的相关属性来指定进度条的描述。

```html
<div aria-busy="true">
    <progress id="progress"></progress>
</div>
```

## `<meter>`

`<meter>` 标签用于显示一个度量值。它有三个属性：`value`、`min` 和 `max`，分别用于指定当前值、最小值和最大值。

```html
<meter value="50" min="0" max="100"></meter>
```

<meter value="50" min="0" max="100"></meter>

## `<time>`

`<time>` 标签用来表示一个特定的时间段。该元素可包含 datetime 属性，用于将日期转换为机器可读格式，从而获得更好的搜索引擎结果或自定义功能（如提醒）。

```html
<time datetime="2024-01-06 10:00">2024-01-06 10:00</time>
```

<time datetime="2024-01-06 10:00">2024-01-06 10:00</time>

## `<dialog>`

`<dialog>` 标签用于显示对话框。使用 `open` 属性来指定默认是否展开。与 `form` 标签配合的 method 属性可以指定关闭对话框的按钮。

```html
<dialog open>
    <p>Greetings, one and all!</p>
    <form method="dialog">
        <button>OK</button>
    </form>
</dialog>
```

<dialog open>
  <p>Greetings, one and all!</p>
  <form method="dialog">
    <button>OK</button>
  </form>
</dialog>

## `<mark>`

`<mark>` 标签用于高亮显示文本。使用方法如下：

```html
<p>这是一段 <mark>高亮</mark> 的文本。</p>
```

<p>这是一段 <mark>高亮</mark> 的文本。</p>

## `<ruby>` 和 `<rt>`

`<ruby>` 标签用于显示注音文字，`<rt>` 标签用于指定注音文字的解释。

```html
<ruby> 汉 <rt>Hàn</rt> 字 <rt>Zì</rt> </ruby>
```

<ruby> 汉 <rt>Hàn</rt> 字 <rt>Zì</rt> </ruby>

##  `datalist` 和 `option`

`datalist` 标签用于指定一个选项列表，`option` 标签用于指定选项。

```html
<label>
    <input list="browsers">
    <datalist id="browsers">
        <option value="Chrome">
        <option value="Firefox">
        <option value="Internet Explorer">
        <option value="Opera">
        <option value="Safari">
    </datalist>
</label>
```

<label>
    <input list="browsers">
    <datalist id="browsers">
        <option value="Chrome">
        <option value="Firefox">
        <option value="Internet Explorer">
        <option value="Opera">
        <option value="Safari">
    </datalist>
</label>


## `sub` 和 `sup`

`sub` 标签用于指定下标，`sup` 标签用于指定上标。多用于数学公式。

```html
<p>这是一个<sub>下标</sub>，这是一个<sup>上标</sup>。</p>
```

<p>这是一个<sub>下标</sub>，这是一个<sup>上标</sup>。</p>

## `abbr`

`abbr` 标签用于指定缩写。

```html
<p><abbr title="World Wide Web">WWW</abbr> 是一种信息系统。</p>
```

<p><abbr title="World Wide Web">WWW</abbr> 是一种信息系统。</p>

## `map` 和 `area`

`map` 标签用于指定一个图片热区，`area` 标签用于指定热区的形状和位置。

```html
<img
        src="workplace.jpg"
        alt="Workplace"
        usemap="#workmap"
/>

<map name="workmap">
    <area
        shape="rect"
        coords="34,44,270,350"
        alt="Computer"
        href="computer.html"
    />
    <area
        shape="rect"
        coords="290,172,333,250"
        alt="Phone"
        href="phone.html"
    />
</map>

```

<img
src="workplace.jpg"
alt="Workplace"
usemap="#workmap"
/>

<map name="workmap">
    <area
        shape="rect"
        coords="34,44,270,350"
        alt="Computer"
        href="computer.html"
    />
    <area
        shape="rect"
        coords="290,172,333,250"
        alt="Phone"
        href="phone.html"
    />
</map>

## 总结

本文介绍了一些不常见但好用的 HTML 标签，它们可以让我们的网页更加丰富多彩。更多 HTML 标签的介绍可以参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)。




