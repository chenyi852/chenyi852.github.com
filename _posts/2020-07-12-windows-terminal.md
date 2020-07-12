---
layout: post
title: "windows terminal"
subtitle: 'windows terminal评测'
author: "Johnny"
header-style: text
tags:

  - windows terminal
  - 评测
---

本人使用的windows 专业版，版本号为：1909。之前下载windows terminal总是失败，今天下载却成功了。有可能是升级1909的原因吧？配合windows的暗色主题，界面还是挺不错的，字体也很好看，看上去像是雅黑字体？至少比windows的默认terminal好看多了。在ubuntu上装了fzf,在此终端上按ctrl+t是能弹出该目录下所有文件的。

有个问题是启动默认是power shell，能否默认从ubuntu的bash启动呢？答案是可以的。研究了下，点击窗口顶加号旁边的的向下箭头，弹出的菜单中有设置选项，可以看到菜单中注明了快捷键是***"ctrl + ,"***。点击设置，弹出的是一个文本文件，我的系统默认是用notepad打开。该文件是windows terminal的配置文件，其中有一项是：

```json
"defaultProfile": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
```

从下面的***profiles***字段中可以找各种profile的list， 通过name字段， 我们可以看到有"windows powershell", "命令提示符"，"ubuntu-18.04", "Azure cloud shell"，每种profile对应的guid，我们可以看到上面defaultProfile对应的就是 "powershell" 的guid。那么我们把defaultProfile的guid改成"ubuntu"的guid是否就可以实现默认启动ubuntu的bash呢？
```json
"defaultProfile": "{c6eaf9f4-32a7-5fdc-b5cf-066e8a4b1e40}",
```

重启windows terminal,  果然默认新建了ubuntu bash。



