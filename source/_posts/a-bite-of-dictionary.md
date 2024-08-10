---
title: a bite of dictionary
date: 2024-08-04 09:30:06
categories:
tags:
---

最近两天有很多意外的收获，值得记录一下。

最近听李笑来老师的演讲，提到了“寻找英文词汇中发音比较有挑战的词汇”这样的 idea，我深表认同，就我这半年朗读英语的体会是，像普通的 Hello，fine，这些日常司空见惯的英文单词，其实发音本身不存在挑战。我们纠正发音最重要的是找到日常生活中我们常用的，而在其他语言（如中文）中没有的特殊单词，将更多精力放在这里的训练，会起到事半功倍的效果。

比如对于我来说，常读错的英文单词类型有：

- 弹舌音 t，如 capital, battery, 在 Apple New Oxford American Dictionary字典中通常标注为“də”

- schwa 的儿化短元音、儿化长元音,，如workers /ˈwɝː.kɚ/，典型的既有儿化短元音，又有长元音

- 中间或者末尾是 小写L 的英文单词，meal, old, cool, capital, will。

- ts 在一起，如 fats

- tn 在一起，这里 t 不发音，如 Martin,Clinton

- tʃ，如children，question

- tə，

- də



然后看到了笑来老师的一个微博，Mac OS 词典 app 自带的New  Oxford American Dictionary在一些音节上标准比较特殊，譬如 tn 会标注为(t)n，这样的话，就可以借用 Python 和正则表达式把符合这些特征的单词都找出来。

经过一番搜索：

MacOS 14.0 的版本中，Mac 上词典 app 默认的字典文件下载路径是：

> /System/Library/AssetsV2/com_apple_MobileAsset_DictionaryServices_dictionaryOSX
