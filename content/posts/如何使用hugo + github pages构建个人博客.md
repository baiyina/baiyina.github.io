---
author: "BAIYINA"
title: "如何使用hugo + Github Pages构建个人博客"
date: '2025-11-20T23:19:03+08:00'
description: " "
tags: ["java", "go", "code"]
ShowToc: true
TocOpen: true
weight: 2
---

# 如何使用hugo + Github Pages构建个人博客

本文将整理一下通过 Hugo + GitHub Pages 进行个人博客搭建。
将分为以下三步：

1. 本地配置 Hugo 环境
2. Github Pages 配置
3. 基础使用描述

## 1. 本地配置 Hugo 环境

**官网文档**：<https://gohugo.io/getting-started/quick-start/>

1. **安装 hugo**
 通过官网链接选择对应版本进行下载： <https://gohugo.io/installation/>
  全选默认选项即可
2. **初始化、安装主题**

``` cmd
# 确认已安装hugo
hugo version
# 在 quickstart 目录中创建项目的网站框架 。
hugo new site quickstart
# 将当前目录更改为项目根目录。
cd quickstart
# 初始化 Git 仓库。
git init
# 添加 PaperMod 主题作为 Git 子模块。
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
# 将主题添加到 Hugo 配置文件中。
echo "theme = 'PaperMod'" >> hugo.toml
# 启动 Hugo 服务器。
hugo server

```

3. **基础功能**

   ![image-20251121013300009](https://raw.githubusercontent.com/baiyina/baiyina.github.image/main/img/202511210133741.png)

创建出来的目录结构大致如图所示，其中只有圈出来的三部分值得关注，

1. **笔记模板** archetypes\default.md

   这个是可以通过 `hugo new content/posts/first.md` 命令生成 md 文档时会依照这个模板进行生成

2. **页面** content目录

   content 目录下存放了你的博客和其他页面声明，PaperMod主题中笔记的存放目录是 content/posts

3. **全局配置** hugo.yaml

   这里是主题和一些配置，实现一些功能的时候在该文件中进行相关属性更改，关于这个可以参考PaperMod主题提供的演示库：<https://github.com/adityatelange/hugo-PaperMod/tree/exampleSite> 的配置项，及主题官方文档内提供的功能说明进行理解：<https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-features/>

## 2. GitHub Pages 配置

默认有一定GitHub基础，至少知道基础的相关知识

步骤：

1. 创建一个仓库，仓库命名为： {你的Github用户名}.github.io

2. 将你的本地项目 quickstart 更名为上面的仓库名，并且提交到这个仓库内

3. 找到这个界面并在Build and deployment Source位置配置为GitHub Actions，里面有Hugo的构建模板，点击后所有按照默认配置来就好

   ![image-20251121105449682](https://raw.githubusercontent.com/baiyina/baiyina.github.image/main/img/202511211054784.png)

4. 然后提交更改后，就可以发现你的仓库中多出了一个目录，修改这个配置文件中的 jobs.build.env.HUGO_VERSION 的 value 值到最新稳定版本

   ![image-20251121105824974](https://raw.githubusercontent.com/baiyina/baiyina.github.image/main/img/202511211059334.png)

   ![image-20251121105903780](https://raw.githubusercontent.com/baiyina/baiyina.github.image/main/img/202511211059660.png)

5. 现在正常通过创建笔记更新后，正常提交就好了，github 会自动通过配置的 actions 进行发布，仓库名就是你的个人博客网址，当然也可以配置自定义网址，教程很多。
