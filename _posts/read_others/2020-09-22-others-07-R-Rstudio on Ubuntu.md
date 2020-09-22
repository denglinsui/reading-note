---
title: "「Others」7 Rstudio on Ubuntu"
subtitle: "Installation and Activate"
layout: post
author: "Linsui"
header-style: text
tags:
  - R language
  - Others
---

# Procedure

## Install r-base

```bash
$ sudo apt update
$ sudo apt -y install r-base
```

## Install Rstudio

```bash
$ sudo apt-get install gdebi-core
$ wget https://download2.rstudio.org/rstudio-server-1.1.463-amd64.deb
$ sudo gdebi rstudio-server-1.1.463-amd64.deb
```

## Run Rstudio

```bash
$ sudo rstudio-server start
```

## Log-in Page

http://localhost:8787/

# Reference

-  [How to use RStudio Server for Ubuntu on Windows 10](https://medium.com/lead-and-paper/how-to-use-rstudio-server-for-ubuntu-on-windows-10-a7aeee661a5d)