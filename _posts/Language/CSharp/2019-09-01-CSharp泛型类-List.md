---
title: C#泛型类 - List
date: 2019-09-01 14:10:00 +0800
categories: [Language, C#]
tags: [c#]
mermaid: true
math: true

---





## List

[List源码](https://referencesource.microsoft.com/#mscorlib/system/collections/generic/list.cs)

## 使用注意

1. `List` 要按需求看是否指定 `Capacity`。

    - 太小会经常扩容，加重GC负担。

    - 太大会造成内存空间的浪费。

        

2. `List` 使用数组作为底层数据结构。

    - 优点是使用索引查找元素速度快。

    - 缺点是扩容时每次针对数组进行的 `new` 会造成内存垃圾，会给GC带来很大负担。

        

3. `List` 的操作接口大多没有做过优化，如果频繁使用，效率会降低，也会造成大量GC。

    

4. `List` 是线程不安全的。需要加锁机制保证线程的安全性。

    

## 一些接口

1. `Contains`
    - `Contains` 使用线性查找的方式比较元素，对数组执行循环操作，如果找到则返回 true，全部比较结束还没有找到则认为查找失败。
    - 时间复杂度为 $O(n)$.
2. `ToArray`
    - 重新创建了一个指定大小的数组，将本身数组上的内容复制到新数组上再返回，如果使用过多，会造成大量内存的分配。
    - 时间复杂度 $O(n)$.
3. `Find`
    - 也是循环查找，时间复杂度 $O(n)$.
    - 

