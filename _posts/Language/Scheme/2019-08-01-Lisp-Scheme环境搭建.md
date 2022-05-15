---
title: Lisp - Scheme环境搭建
date: 2019-08-01 14:10:00 +0800
categories: [Language, Scheme]
tags: [scheme]
---



## Scheme

Scheme是一种多范型的编程语言，并主要支援函数式范型。它是Lisp两种主要的方言之一（另一种为Common Lisp）。与Common Lisp不同的是，Scheme强调极简主义设计与简约而可扩展的语言特性。它的精简性与优雅的语法广受计算机科学教育者以及语言设计学者的欢迎，并经常被用于基础计算机科学教育上。麻省理工学院与其他院校曾利用Scheme教授入门课程，并且著名的入门教材《计算机程序的构造和解释》（SICP，或称“魔法书”）就是利用Scheme来解释程式设计。Scheme的广泛受众被视为它的一个主要优势，然而不同实现之间的差异成为了它的一个劣势。

Scheme最早由麻省理工学院的盖伊·史提尔二世与杰拉德·杰伊·萨斯曼在1970年代发展出来，并由两人发表的“λ论文集”推广开来。 Scheme语言与λ演算关系十分密切。小写字母“λ”是Scheme语言的标志。

Scheme的哲学是：设计计算机语言不应该进行功能的堆砌，而应该尽可能减少弱点和限制，使剩下的功能显得必要。Scheme也是第一个使用静态而非动态变量区域的Lisp方言。

<br>

## 安装Scheme解释器

[ChezScheme](https://cisco.github.io/ChezScheme/)

<br>

## VSCode配置

1. VSCode 安装 `code runner`
2. 添加配置

    ```
    "code-runner.executorMap": {
        "scheme": "scheme"
    }
    ```



