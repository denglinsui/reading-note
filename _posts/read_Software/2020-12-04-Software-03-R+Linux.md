---
title: "「Software」3 R language/Linux"
subtitle: "R language/Linux - Some Basic Tips"
layout: post
author: "Linsui"
header-style: text
tags:
  - R language  
  - Linux
  - 笔记
---

# R

## Tips

- Save Data
  -  `save.image(file = "Main_Test.RData")`
- Still Running after disconnected: 
  - ` nohup Rscript test.R >./log/print.log 2>./log/error.log &`

# Linux

- Check authority
  - `ls -l`
- Change quthority
  - `u`: user; `g`: group;`o`: others; `a`: `u+g+a``
  - ``r`: read; `w`: write;`x`: execute
  - Example: `chmod a+x abc.txt`
- We can use `/mnt/d` to enter the windows disk in Linux.
- Remote exchanges:
  - Single file
    - `scp username@servername:/path/filename /var/www/local_dir（本地目录）`
    - `scp /path/filename username@servername:/path `
  - Whole folder
    - `scp -r username@servername:/var/www/remote_dir/（远程目录） /var/www/local_dir（本地目录）`
    - `scp -r username@servername:/var/www/remote_dir/（远程目录） /var/www/local_dir（本地目录）`