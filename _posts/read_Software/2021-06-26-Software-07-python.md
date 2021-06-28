---
title: "「Software」6 python"
subtitle: "Python - Chinese support in matplotlib"
layout: post
author: "Linsui"
header-style: text
tags:
  - python 
  - 笔记

---

# Python

## 

## Chinese support in matplotlib

- If Chinese Caption cannot normally display, download `Simhei` in the following `dictionary + font/ttf`.

```python
import matplotlib 
print(matplotlib.matplotlib_fname()) 
```

- Before plotting, use

  ```python
  plt.rcParams['font.sans-serif'] = ['SimHei']  # Used to display Chinese labels normally
  plt.rcParams['axes.unicode_minus'] = False  # Used to display the negative sign normally
  ```

  

- In addition, the cache file should be removed by `rm -r the dictionary` below.

  ```python
  print(matplotlib.get_cachedir())
  ```


  