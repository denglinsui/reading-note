---
title: "「Others」4 Latex Pakage Installation"
subtitle: "Latex Pakage Installation - Manual"
layout: post
author: "Linsui"
header-style: text
tags:
  - Latex
  - Others
---
# Latex Pakage Installation

**安装环境**： Windows 10 + MiKTeX+TexStudio

有时候会因为网络的问题，在引入新的宏包的时候，自动安装会出错。

接下来是安装的方法：

## 方法一

- 打开 **MiKTeX Console**
- 选择 **Packages**
- 官方的package就能直接在里面下载啦

## 方法二

- 在[Latex宏包网站](https://www.ctan.org/pkg)中下载所需要的包xxx并进行解压
- 在cmd中进入解压目录
- 运行`latex xxx.ins`就会生成相应的lsy文件 或者  运行`tex xxx.dtx`就会生成相应的lsy文件
- 将对应文件夹移到包的文件夹位置```...\mitex\tex\latex```
- 最后在**MiKTeX Console**中选择```Refresh Database```

