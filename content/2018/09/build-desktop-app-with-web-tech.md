---
title: 使用 Web 技术开发桌面程序
date: 2018-09-25 11:43
tags: [UI, Web]
---

两年前，我第一次尝试使用 [Electron](https://electronjs.org/)，虽然确很方便，但是打包生成的程序体积很大。我当时在 V 站提了一个[问题](https://www.v2ex.com/t/271585)，最后也没有得到解决。Electron 本质上就是一个浏览器，对于每一个使用 Electron 的用户来说，他首先打开了一个浏览器，然后通过“浏览器”的渲染才看到实际代码展现出来的界面与功能。也许在开发者看来，一两百兆的体积算不了什么，但对小空间的用户（比如我）来说，一个小小的软件占用这么大的空间，实在不合算。而且 Electron 生成的软件中，包含了 Node.js（作为后端）和 Chromium（作为前端）相关的内容，对大多数应用来说，这些内容都是相同的，也没必要每个软件包中都保存一份。


## 另辟蹊径
那么有没有一种方法，能够在使用 Web 技术的前提下，尽量减小软件包的体积呢？当然有。对于用 C/C++/C# 开发的桌面程序（Windows 平台）而言，底层的代码已经打包在操作系统中了，分发程序只有上层应用的代码，自然体积就小了。如果想用 Web 技术开发桌面应用，绕不开的一层就是浏览器（或者 Node.js）这样的运行框架，减小这层运行框架的体积，上层应用的体积自然会减少。

事实上，对操作系统而言，本身携带了解析 HTML 的框架，称为 webview。在 Windows 平台上是 MSHTML，没错，就是让前端咬牙切齿的 IE 浏览器的排版引擎。在 Win10 上，自带的 IE 浏览器版本已经是 11，对 W3C 标准的支持也比较全面，如果不是追求最新的特性，够用了。没办法，人在屋檐下，不得不低头。在低版本的 Windows 平台上，webview 是对应的 IE 浏览器的排版引擎。如果不能忍受它们（IE6/7/8），以下的方法就不适用了。而且 webview 没有对本地系统的交互能力，如果桌面程序需要重度依赖操作系统（比如频繁的读取写入文件）等，本文讨论的方法也不适用，老老实实用原生语言开发吧。以下介绍的方法本质上还是在浏览器中渲染网页，只不过为了减小应用体积把浏览器换成了系统自带的而已。

## 实践
调用系统本身的 webview 已经有相应的[开源框架](https://github.com/zserge/webview)，在此基础上，做些小小的改动就可以使用。

```c
#include <unistd.h>
#include "webview.h"

int main()
{
   char buf[80];
   char url[] = "file:///";
   int  i;

   getcwd(buf, sizeof(buf));

   for (i = 0; buf[i] != '\0'; i++)
   {
      if (buf[i] == '\\')
      {
         buf[i] = '/';
      }
   }

   strcat(url, buf);
   strcat(url, "/index.html");

   webview("Minimal webview example", url, 320, 480, 0);
   return 0;
}
```
在示例代码中，将远程 HTTP 访问的网页替换为本地 File 协议访问的网页，网页路径以自己的实际项目为准。编译此 C 代码，我们就拥有了一个“启动器”，用来渲染本地的 HTML 文件。应用的功能在 HTML 中实现，因为这是在浏览器中渲染，所以开发应用的过程可以尽情使用第三方的 JS/CSS 库，提高开发效率。

```bash
gcc main.c -DWEBVIEW_WINAPI=1 -lole32 -lcomctl32 -loleaut32 -luuid -mwindows -o webview-example.exe
```

## 结语
对一些简单的小工具，这样的开发方式能够快速地实现想要的功能。因为是用 C 语言调用本地的 webview，应用程序体积非常小，分发给别人也很方便。技术的革新就应该是这样，扬长避短，但不要钻牛角尖，觉得自己拿个锤子，看什么都是钉子，合适的才是最好的。
