---
title: C# - StringBuilder
date: 2021-01-04 14:10:00 +0800
categories: [Language, C#]
tags: [c#]
mermaid: true
math: true
---



## 对比 String

1. String的值是不可变的，每次对string的操作都会生成新的string对象，然后指向新的对象。

    - 效率低下，大量浪费内存空间

2. StringBuilder是可变的，且是线程安全的。每次操作不会生成新的对象，而是修改缓冲区的数据。

    - 每个stringBuilder对象都有一定的缓冲区容量。

      ​    