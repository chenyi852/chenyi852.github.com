---
layout: post
title: "搭建github pages环境"
subtitle: '利用gitee来同步到github'
author: "Johnny"
header-style: text
tags:

  - github pages
  - gitee
---

由于良久失修，当前gitee与github之间博客仓库的同步已经失效了。之前也没做记录，此次
同步将过程记录下来，避免以后又要同步。


要同步的话，首先打开gitee镜像仓库的`管理`选项卡，然后在左侧栏中选中`仓库镜像管理`，
镜像方向选择push， 镜像仓库选择github中的目标仓库即可。私人令牌得去github中获取。

经典令牌（Classic Token）获取方法：
- 登录 GitHub 并点击右上角头像 → Settings（设置）
- 在左侧边栏底部找到 Developer settings（开发者设置）
- 选择 Personal access tokens → Tokens (classic)
- 点击 Generate new token (classic) 按钮
- 设置令牌信息：
    - Note（备注）：给令牌起个名字，例如 "My API Access"
    - Expiration（有效期）：选择过期时间（推荐 90 天，最长可设为永不过期）
    - Scopes（权限范围）：勾选需要的权限，例如：
    - repo — 访问私有仓库
    - workflow — 管理 GitHub Actions
    - read:org — 读取组织信息
    - gist — 访问 Gist
- 点击 Generate token 生成
- ⚠️ 重要：立即复制并保存令牌！页面关闭后无法再次查看

回到gitee刚才得页面，点击即可，这样镜像就创建完成。
