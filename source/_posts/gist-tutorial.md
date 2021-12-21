---
title: gists 教程
tag: gists
categories: tools
top_img: https://miro.medium.com/max/1024/1*9igtxjzMnJWCjrwgELXEYg.jpeg
cover: https://miro.medium.com/max/1024/1*9igtxjzMnJWCjrwgELXEYg.jpeg
---

Github 作为代码分享平台在开发者中非常流行。此平台托管了包括游戏、书籍以至于字体在内的一千两百多万个项目（现在更多），这使其成为互联网上最大的代码库。

Github 还提供另一个非常有用的功能，这就是 Gists。

开发人员常常使用Gists记录他们的代码片段，但是Gist不仅仅是为极客和码农开发的，每个人都可以用到它。如果听说过类似Pastebin或者Pastie这样的web应用的话，那就可以看到它们和Gist很像，但是Gists比它们要更优雅。因为这些免费应用一般含有广告，而且带有很多其他杂七杂八的功能。

## 可以用来做什么

### 匿名张贴

不需要拥有Github账号就可以使用Gist。用浏览器打开[gist.github.com](http://gist.github.com)，在窗口中写下你想说的就可以创建一个Gist。您可以发布一个私密的Gist，也就是说这个Gist将不能被他人搜索到而只对直接在浏览器中输入其URL的人可见。

### 能像wiki一样记录历史

如果修改了已经发布了的Gist，之前的所有版本都将被保存。可以通过点击Revisions按钮按时间浏览，而且还可以通过内置的diff引擎查看任意两个版本间的差异。 这也可以用于比较文本文件。

### 发布富文本内容

虽然Gist只能用纯文本来写，但是可以用markdown来发布html格式的Gist。并且可以添加列表、图片（已有图床上的）和表格。当使用markdown的时候不要忘了文件名要以.md为后缀。

### 把Gist当做写作平台

虽然现在有很多写作引擎，比如Blogger、Medium、Tumblr，但您还可以用Gist来快速发布您的作品。您可以用纯文本或者markdown等文档标记语言些一个Gist然后用[roughdraft.io](http://roughdraft.io)来把它作为一个独立的网页发布。

### 托管Gist上的单个页面

可以用纯文本把HTML、CSS、JavaScript代码写下来以index.html为文件名保存为Gist，然后用[bl.ocks.org](http://bl.ocks.org)把渲染好的结果在浏览器中展示出来。

### 制作任务列表

可以用Gist跟踪待处理任务，这是用纯文本的特殊语法写的但是你可以任意勾选。

- [x] Pick the flowers
- [ ] Call John 9303032332
- [x] Cancel cable subscription
- [ ] Book the flight tickets

可以勾选或者勾去任意选项，源文本将会自动变更。如果Gist是公有的的话，任何人都可以看到这个的列表，但是只有拥有者可以改变其勾选状态。

其实任务列表也可以在issue中建立，所有拥有写权限的人都可以uncheck/check。

### 把Gist作为一个网页收藏夹

在Chrome浏览器可以找到一个叫GistBox的插件，通过这个插件可以在浏览网页时选择保存网页内容为Gist。甚至可以添加标注或者话题标签以易于以后更容易找到它们。

### 把Gists嵌入网页中

用一行js代码就可以把任何一条Gist嵌入到网页中。嵌入的Gist格式不发生任何变化，而且访问者可以非常方便的把它们fork到他们的Github中。要嵌入wordpress的话有这个插件和这个短代码可以使用。

### 测量访问量

可以使用Google Analytics查看Gist的访问量。因为Gist纯文本中不允许运行js代码，所以我们可以用[GA Beacon](https://github.com/igrigorik/ga-beacon)来记录实时访问Gist的情况。

### 在桌面端管理Gist

Gisto是一个能在浏览器之外管理Gist的桌面应用。可以对Gist进行搜索、编辑、查看历史和分享。 此应用可运行于Mac、Windows和linux系统。 当然也可以用[cacher(GistBox)](https://www.cacher.io/)这个web应用替代它。

## 快速开始

### 创建一个Gist

打开[gists](https://gist.github.com)点击GitHubGist即可创建一个Gists，支持多种文本格式编写保存。如果需要在本地进行编辑，使用git和repo类似将代码pull到本地修改之后push即可。

### 分享Gist

![点击share](https://cdn.cacher.io/attachments/u/3gla8t6baqs8z/MKxfiiJTt3OVSmlOnv0AOTVBmEuAJOFm/截屏2021-12-19_下午1.56.15.png)

### 推荐工具

桌面管理工具[cacher](https://www.cacher.io/)，用来记录学习笔记或者每天的TodoList十分的方便，同时它也有对应的Chrome/FireFox插件，能够支持在浏览器中添加gist到GitHub中（十分有用）。例如，当浏览页面时或者阅读一个GitHub的代码时，觉得不错的idea或者代码就能轻松的记录下来。
cacher还支持添加分类标签和搜索功能，当需要查找时能快速的找到之前的记录。

## Ref

- [What You Can Do With Gists on Github?](https://www.labnol.org/internet/github-gist-tutorial/28499/)
SAVE TO CACHER