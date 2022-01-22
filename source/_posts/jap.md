---
title: JavaScript 高级程序设计
tag: 读书笔记
categories: books
top_img: https://www.zhaozf.site/assets/blogImg/JavaScript%E9%AB%98%E7%BA%A7%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1%EF%BC%88%E7%AC%AC4%E7%89%88%EF%BC%89_%E5%B0%81%E4%B8%80.jpg
cover: https://www.zhaozf.site/assets/blogImg/JavaScript%E9%AB%98%E7%BA%A7%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1%EF%BC%88%E7%AC%AC4%E7%89%88%EF%BC%89_%E5%B0%81%E4%B8%80.jpg
---

## 什么是JavaScript

JS由核心ES、文档对象模型DOM、浏览器对象模型BOM构成。

### ECMAScript

描述了语法、类型、值、对象、属性、函数、语句、关键字、保留字、操作符、全局对象。

### DOM

提供与网页内容交互的方法和接口，它通过创建表示文档的树，让开发者可以随心所欲地控制网页的内容和结构，并且可以使用DOM API轻松地对节点进行增删改查。DOM主要是与浏览器页面显示相关，比如页面内容、事件。

### BOM

提供与浏览器交互的方法和接口，用于支持访问和操作浏览器的窗口，使用BOM开发者可以操控浏览器显示页面之外的部分，比如弹出新窗口的能力、移动缩放和关闭浏览器窗口的能力、navigator对象、location对象、screen对象、performance对象、对cookie的支持以及其他自定义对象。

将JS引入网页，使得网页具有更多的可操作性。

## HTML 中的 JavaScript

### \<script>元素

将 JS 插入 HTML 的主要方法，它具有下列八个属性：

- **async**: 推迟执行脚本，表示应该立即开始下载脚本，但不能阻止其他页面动作，比如下载资源或等待其他脚本加载。只对外部脚本文件有效。
- **defer**: 异步执行脚本，表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。在 IE7 及更早的版本中，对行内脚本也可以指定这个属性。

js代码加载执行顺序：
![js代码加载执行顺序](https://segmentfault.com/img/bVWhRl/view?w=801&h=814)

- crossorigin: 配置相关请求的 CORS(跨源资源共享)设置。默认不使用 CORS。crossorigin= "anonymous" 配置文件请求不必设置凭据标志。crossorigin="use-credentials" 设置凭据 标志，意味着出站请求会包含凭据。
- integrity: 允许比对接收到的资源和指定的加密签名以验证子资源完整性。这个属性可以用于确保内容分发网络不会提供恶意内容。
- language: 废弃。
- src: 表示包含要执行的代码的外部文件。
- charset: 使用 src 属性指定的代码字符集。
- type: 代替 language，表示代码块中脚本语言的内容类型(也称 MIME 类型)。

### 行内代码与外部文件

JS 代码可以通过行内代码或放在外部文件中执行。

在 HTML 文件中最佳实践是尽可能的将 JS 代码放在外部文件中，放在外部文件中能带来许多好处：可维护性、缓存、适应未来。在配置浏览器请求外部文件时，要重点考虑的一点是它们会占用多少带宽，这是衡量网页性能的一个重要的指标。

### \<noscript>元素

对于禁用 JS 浏览器的一个页面优雅降级的处理方案，被用于给不支持 JavaScript 的浏览器提供替代内容。

\<noscript>元素可以包含任何可以出现在\<body>中的 HTML 元素，\<script>除外。在下列两种 情况下，浏览器将显示包含在\<noscript>中的内容:
- 浏览器不支持脚本
- 浏览器对脚本的支持被关闭

当任何一个条件被满足，包含在\<noscript>中的内容就会被渲染。
