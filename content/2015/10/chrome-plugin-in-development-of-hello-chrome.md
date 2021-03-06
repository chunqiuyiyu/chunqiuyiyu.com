---
title: Chrome 插件开发之 Hello-Chrome
date: 2015-10-30 19:30
tags: [插件, HTML5, JavaScript, Chrome]
---
## 前言

从事前端开发的工作者，想必十分熟悉 Chrome。尤其对于移动 Web 开发来说，Webkit 内核的浏览器可以说是一统天下，作为其杰出代表的 Chrome,在上面开发以及调试 Web 网站和应用十分之方便快捷，“开发者工具”是我最常用的一个功能。同时，众多的插件也让 Chrome 如虎添翼，涵盖方方面面，但是，别人做的东西总归有一些不尽如人意的地方。所以就想着学习相关的插件开发技术，自己动手，丰衣足食，解决生活或者工作上的问题。主要用到的技术也就是 HTML、CSS 和 JavaScript 了，上手很快，重点和难点是 Chrome 插件 API 的使用。


<!--more-->


## 入门

每一门程序语言的入门总要写一个 Hello World 程序，这已经成为了一种惯例，这个系列也不会例外。现在来学着写一个 Hello Chrome 的插件，就算作入门。抛开繁琐的细节，直接上手，在实践中学习，这是我的学习方法。先来了解一些基本知识，什么是插件？我们接触到的是已经上线的 CRX 文件，但它实际上是一个压缩包文件，将后缀名改为 `.rar`，用解压软件打开就可以看到里面的文件(比如这个我经常使用的 Web 前端助手)。

![ctx_struction-1024x307.png][1]

其中包含用来展示界面的 HTML5 文件，控制样式的 CSS 文件，以及逻辑处理的 JS 文件，还有一个配置文件 `manifest.json`文件。`manifest.json` 文件十分重要，它是插件的入口文件，我们的例子就从这里开始。

## Manifest 文件

这个文件里面主要是插件的配置信息。新建一个目录，起名为 "Hello-Chrome",在里面新建一个 `manifest.json` 文件，详情如下：
```
{
"manifest_version": 2,
"name": "Hello_Chrome",
"version": "1.0",
"description": "Chrome扩展入门",
"browser_action": {
"default_icon": {
"19": "images/icon19.png"
},
"default_title": "Hello_Chrome",
"default_popup": "popup.html"
}
}
```
最开始是 `manifest` 文件的版本号，现在统一为2（旧版的插件是1），接下来就是插件的名称，版本以及描述。

![example.png][2]

`browser_action` 定义了与浏览器有关的信息，首先是在地址栏右边显示的默认图标（视情况而定，有些插件只有后台，就不需要显示），事先在插件根目录下建立一个 `images` 文件夹，里面放入图标文件（本例使用谷歌的图标），然后是默认标题，也是是鼠标移到图标上显示的文字，最后是点击图标弹出的页面，实际上就是一个 HTML 文件。同样以 Web 前端助手为例，信息如图所示。

![browser_action_example.png][3]

**注意：这并不是 `manifest` 文件的固定形式，需要根据实际情况添加或者删除相关的配置信息比如说是否需要在后台运行脚本、创建右键菜单的权限等等。**现在只是一个很简单的入门，以后会慢慢涉及到复杂的部分。

## 弹出页面

`popup.html` 文件如下：
```
<html>
<head>
<style type="text/css">
p{
width: 200px;
font-size: 14px;
}
</style>
</head>
<body>
<p>click the button to show dialog...</p>
<input id="button" type="button" value="click me"></input>
<script type="text/javascript" src="js/app.js"></script>
</body>
</html>
```
基本跟普通的 HTML 文件没什么区别，主要是去除了文档声明，这是因为这个文件本身就在 Chrome 环境中运行，也就不需要多此一举（如果加上也没什么问题）。**一个重点在于，出于安全考虑，在这个页面中不能直接使用 `script` 标签来内嵌 JS 脚本，需要用 src 从外部引入。**这个页面显示了一句话和一个按钮，点击后弹出一个对话框，JS 文件很简单，没什么好说的。
```
document.getElementById("button").addEventListener("click" , hello);
function hello(){
alert("hello chrome!");
}
```
## 效果演示

好了，一个最简单的插件就完成了，是不是觉得很简单呢，现在就来运行看看效果吧。打开 Chrome 的扩展程序页面，勾选开发者模式（如果不勾选，不会出现加载插件文件夹的按钮），点击“加载已解压的扩展程序”按钮，加载我们的插件。开发过程中如果需要多次调试，可点击“重新加载”链接（或者用快捷键：CTRL + R）。
![load_hello_chrome_plugin.png][4]
![hello_chrome_show.png][5]

## 源码

[Github][6]

## 后记

知易行难。好多事情其实没什么捷径而言，踏踏实实敲一遍代码，该懂的也就懂了，如果不懂，就再敲一遍。今天就先到这里，后面随着插件的复杂化，也可以学习更多的知识，只能说 Chrome 真是太强大了，但愿它能越来越好。


  [1]: /img/130204898.png
  [2]: /img/1095636572.png
  [3]: /img/91592680.png
  [4]: /img/4069920326.png
  [5]: /img/1840007412.png
  [6]: https://github.com/chunqiuyiyu/learn-javascript/tree/master/hello_chrome
