---
title: "「Others」3 WOS Citation Analysis"
subtitle: "WoS Citation Analysis - Data Collection"
layout: post
author: "Linsui"
header-style: text
hidden: true
tags:
  - Paper
  - Others
  - Web of Science
  - Network
---
# WoS Citation Analysis

## 数据收集的说明

[Mapping the Backbone of Science](https://www.researchgate.net/publication/220365044_Mapping_the_Backbone_of_Science)里用到的数据是wos里sci和ssci 2000年发表的文章的引用信息，我在网上暂时没有找到公开的已经整理好的数据集。

- [WOS Collection List](https://mjl.clarivate.com/collection-list-downloads) 和 [WOS JCR]( http://fhyxa7c727d884744f15a180f8aa826e027cswpuwu5ok9v6o6oqx.fcfb.libproxy.ruc.edu.cn/JCRJournalHomeAction.action# ) 有截至2020年的期刊汇总。
-  [WOS JCR]( http://fhyxa7c727d884744f15a180f8aa826e027cswpuwu5ok9v6o6oqx.fcfb.libproxy.ruc.edu.cn/JCRJournalHomeAction.action# ) 里点进具体的期刊[WOS Example]([http://fhyxd70aa7ecb75b499faadc5662f40791aaswpuwu5ok9v6o6oqx.fcfb.libproxy.ruc.edu.cn/jif/home/?journal=NAT%20REV%20CHEM&year=2019&editions=SCIE&pssid=H1-upPjEjnj3XgwIsj94a4GzU4x2BxxR3KyfCxx-18x2d6qKNhtEfrbAa4tn0JGiq6Ax3Dx3DOUwW8UZ8UOyy7evR7ZhQgAx3Dx3D-WwpRYkX4Gz8e7T4uNl5SUQx3Dx3D-wBEj1mx2B0mykql8H4kstFLwx3Dx3D](http://fhyxd70aa7ecb75b499faadc5662f40791aaswpuwu5ok9v6o6oqx.fcfb.libproxy.ruc.edu.cn/jif/home/?journal=NAT REV CHEM&year=2019&editions=SCIE&pssid=H1-upPjEjnj3XgwIsj94a4GzU4x2BxxR3KyfCxx-18x2d6qKNhtEfrbAa4tn0JGiq6Ax3Dx3DOUwW8UZ8UOyy7evR7ZhQgAx3Dx3D-WwpRYkX4Gz8e7T4uNl5SUQx3Dx3D-wBEj1mx2B0mykql8H4kstFLwx3Dx3D))，里面会有Journal Relationship来展示和其他期刊的引用和被引用的关系，但是没有方便分析的原始数据。
- [WOS_Crawler](https://github.com/tomleung1996/wos_crawl) 提供了根据期刊名爬取wos文章数据的方法，但是有时候会因为访问权限的问题会报错。确定了需要用到的数据集的范围(年份，范围)以后，可以再改一改，得到需要的信息。
- [python爬取WOS数据](https://mp.weixin.qq.com/s/XdZrUx22jwhJPkcDOnzrrw)里有上述工具和rwos，wosr(直接调用WOS API)的使用指南，可以根据需求选取。
- 还有一个可能的获取数据的途径就是直接向WOS进行申请，详见 [Web of Science as a data source for research on scientific and scholarly activity  ](https://doi.org/10.1162/qss_a_00018)。

## 一些需要注意的问题

- [Mapping the Backbone of Science](https://www.researchgate.net/publication/220365044_Mapping_the_Backbone_of_Science) 中提出，JCR中的数据无法分析inter-citing 和 co-citing ，因此选用了对文章的原始数据进行分析的的方法。
- [Google Scholar - A new data source for citation analysis](https://harzing.com/publications/white-papers/google-scholar-a-new-data-source-for-citation-analysis) 提出现在用Google Scholar 中的数据，并比较了他与Web of Science 中数据的优劣。

## 其他点

- [How to download Web of Science data for Bibliometrics Research](http://cluster.ischool.drexel.edu/~cchen/citespace/doc/tutorial/how_to/1.download_from_WOS.pdf) 是一份如何手动下载引用数据的使用指南，可以帮助理解字段的意思以及如何去对[WOS_Crawler](https://github.com/tomleung1996/wos_crawl) 进行修改，得到自己想要的指标。
- [Mapping the Structure and Evolution of Science](https://grants.nih.gov/grants/km/oerrm/oer_km_events/borner.pdf) 总结了近些年部分network data可视化的工作以及列出了一些常用的数据集。
- [Clickstream Data Yields High-Resolution Maps of Science](https://doi.org/10.1371/journal.pone.0004803) 不再使用citation之间的关系，而是使用log data。

# Reference

- [WOS website](http://apps.webofknowledge.com/UA_GeneralSearch_input.do?product=UA&search_mode=GeneralSearch&SID=7CROEqv8cv1x71Ns9tb&preferencesSaved=)
- [python爬取WOS数据](https://mp.weixin.qq.com/s/XdZrUx22jwhJPkcDOnzrrw)
- [WOS_Crawler](https://github.com/tomleung1996/wos_crawl)
- [Clickstream Data Yields High-Resolution Maps of Science](https://doi.org/10.1371/journal.pone.0004803)
- [Mapping the Structure and Evolution of Science](https://grants.nih.gov/grants/km/oerrm/oer_km_events/borner.pdf)
- [How to download Web of Science data for Bibliometrics Research](http://cluster.ischool.drexel.edu/~cchen/citespace/doc/tutorial/how_to/1.download_from_WOS.pdf)
- [Mapping the Backbone of Science](https://www.researchgate.net/publication/220365044_Mapping_the_Backbone_of_Science)
- [Google Scholar - A new data source for citation analysis](https://harzing.com/publications/white-papers/google-scholar-a-new-data-source-for-citation-analysis)
