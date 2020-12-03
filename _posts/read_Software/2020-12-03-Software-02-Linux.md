---
title: "「Software」1 Linux"
subtitle: "Linux - Remote Log & Installation of Rmosek"
layout: post
author: "Linsui"
header-style: text
tags:
  - Linux
  - 笔记
---

# Linux

## Tips

- ` ssh usersname@10.224.255.112 -p 5102`
  
  - `10.224.255.112` is the address of the remote server
  
- How to disconnect:

  - `Ctrl+D`
  - input `logout`
  - input `exit`

- How to keep the process after connect?

  - `nohup`

- When it appears some error like `.so` when installing packages in `R` or via `cmake`, check whether I have make some configure files before.

- License file should be located in 
  **username**.

  - `c:\users\_userid_\mosek\mosek.lic`

  - Otherwise, there will be error in `status` or something like:

    ```R
    Optimization interrupted.
    ERROR: MSK_RES_ERR_MISSING_LICENSE_FILE: A license cannot be located.
    ```

# Reference

- [Rmosek Installation](https://gist.github.com/mikelove/67ea44d5be5a053e599257fe357483dc)