---
title: computer configuration
date: 2024-10-13
authors: [Pengyu-Jin]
slug: computer configuration
categories:
  - Life
---

**computer configuration**

当你有一台新的电脑时，往往需要重新配置电脑环境，以便让自己更熟悉，有些必要的工具、软件等已经离不开我们的个人生活，但再去寻找相关网站等资源很耗费时间。因此只需参考此篇博客就可以事半功倍。

<!-- more -->

## 常用软件
**欧陆词典**：添加朗文词库和韦氏大学词库，参考bilibili的[up主-昂克英文君](https://www.bilibili.com/video/BV1fK4y1E7mC?p=1&vd_source=a69c9948d8c31b427ccd421455913cab){:target="_blank"}

**word插件**：[小恐龙公文排版助手](https://xkonglong.com/){:target="_blank"}、AXmath[^1]

**idm[^2]-Internet Download Manager**：下载管理器

!!! bug "一些问题"

    用一段时间后会显示“此版本的IDM不支持该类下载，请尝试将IDM更新至最新版本”。原因是chrome浏览器在更新时扩展插件会自动更新，导致下载失败。解决办法是移除插件，在从idm安装目录中找到IDMGCExt.crx，拖入浏览器扩展界面中，重新安装插件即可使用。具体参考下面链接。

    [此版本的IDM不支持该类下载，请尝试将IDM更新至最新版本](https://blog.csdn.net/chenxihe123/article/details/121283537){:target="_blank"}

**Adobe Acrobat[^3]**：Adobe PDF阅读器，参考bilibili的[up主-云渲视觉](https://www.bilibili.com/video/BV1nB4y1o7Py/?spm_id_from=333.337.search-card.all.click&vd_source=a69c9948d8c31b427ccd421455913cab){:target="_blank"}

**SimpleTex**：公式识别，生成对应的LaTex代码。[SimpleTex主页](https://simpletex.cn/){:target="_blank"}

**PicGo**：上传图片到图床的软件，获取对应的URL。[PicGo主页](https://picgo.github.io/PicGo-Doc/){:target="_blank"}

**mathematica**: 数学软件，可以用来做一些数学计算。[Mathematica 激活指南](https://tiebamma.github.io/InstallTutorial/){:target="_blank"}

[^1]:百度网盘/我的资源/Axmath

[^2]:百度网盘/我的资源/idm

[^3]:百度网盘/我的资源/Adobe Acrobat

## 配置问题

装的acrobat在显示缩略图上出现问题，即桌面上的pdf文件有的显示缩略图，有的没有显示。解决办法是安装SumatraPDF，安装的时候在选项里面勾选在windows资源管理器显示pdf预览，然后acrobat就可以显示预览了。

