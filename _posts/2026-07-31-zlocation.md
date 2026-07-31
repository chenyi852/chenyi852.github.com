---

layout: post
title: "widows智能跳转工具ZLocation"
author: "Johnny"
header-style: text
tags:

  - ZLocation 
  - windows
  - powershell
---

`ZLocation`是一个专为powershell设计的智能目录跳转工具。你可以把它看作是autojump或
z.sh在powershell的实现。它的核心作用是记录里经常访问的文件夹，并让你能通过输入
一个简单的关键词或路径片段就行跳转到想去的目录，从而告别在cli中输入一长段繁琐的
路径。

## 主要功能

- 智能学习：它会追踪在powershell中访问过的文件夹。
- 权重排名：每个被记录的文件夹都有权重，访问越频繁，权重越高。ZLocation优先跳转
到权重高的路径。
- 跨平台：支持主流操作系统。

## 安装与配置

1.安装：

```powershell
Install-Module ZLocation -Scope CurrentUser
```

2.配置：为了让ZLocation在每次powershell启动时自动加载，需要将它添加到powershell
的配置文件中。

```powershell
Add-Content -Value "`r`n`r`nImport-Module ZLocation`r`n" -Encoding utf8 -Path $PROFILE
```

完成后，重新打开powershell,ZLocation就准备好了。

## 核心命令与使用

安装并加载模块后，你就能是使用一下命令：

- z：这是核心常用命令。只需输入z加上路径关键词，就能瞬间跳转。

- z(无参数)：不带任何参数直接运行,会列出所有已学习的文件夹及其权重，方便你查看。

- z -l <关键词>：查找并列出所有匹配某个关键词的文件夹及其权重。

```powershell
z -l unity
```

- tab键自动补全：如何`z <关键词>`跳转到的不是你想去的目录，可以在输入`z <关键词>`
后按`tab`键，在所有的候选项中循环选择。

- `z -`：返回使用`z`命令跳转前的上一个目录，相当于`cd -`。

```powershell
C:\> z foo   # 跳转到 C:\foo
C:\foo> z bar # 跳转到 C:\bar
C:\bar> z -  # 回到 C:\foo
```


- `z <子路径1> <子路径2>`：当多个路径有相同关键词时，可以用多个关键词来精确指定。

```powershell
# 假设有两个项目文件夹: D:\Project1\unity 和 D:\Project2\unity
z 2 unity 
# 会跳转到 D:\Project2\unity
```

## 其他实用命令

- `pop-ZLocation`：功能和`z -`相同，也是返回上一个目录。

- `Remove-Zlocation`：从历史记录中移除一个条目。

- `Update-ZLocation`：手动更新历史记录。





