---
layout: post
title:  "博客技巧汇总"
date:   2023-12-20 14:08:05 +0800
categories: Blog, Jekyll, Github Pages
---

## 隐藏博文
如果你不想让某篇post展示在博客中，可以在该post的`Front Matter`中指定`Published: False`。[查看ChatGPT的解释](https://chat.openai.com/share/277f331d-c8d1-4bb4-b0dd-e6caa3184eec)。

## 为博客插入图片
相比于网上比较流行的使用 PicGo 等工具搭配 Github 作为图床的方法，我更偏向于只使用Github实现相同的效果。

在将图片上传到 Github 仓库中后，在博客的 .md 文件中通过如下方式插入图片：

`![图片描述](图片链接)`

**注意**，这里的图片链接并不是在仓库中直接复制的链接，而是**在新标签页中打开的图片链接**，如下图：

![在博客中引用图片](https://raw.githubusercontent.com/KeithBH/KeithPictures/main/CiteImage.png)

[参考链接](https://www.bilibili.com/video/BV1Va41177xV/?spm_id_from=333.337.search-card.all.click&vd_source=e76e9bb0a051986a16535ab4f8d9842a)