---
title: C#泛型类 - Dictionary
date: 2019-09-02 14:10:00 +0800
categories: [Language, CSharp]
tags: [csharp]

---





## Dictionary

`Key -> Value`

[Dictionary源码](https://referencesource.microsoft.com/#mscorlib/system/collections/generic/dictionary.cs)

`Dictionary` 使用**散列表**作为底层数据结构。



## Hash表

### Hash函数

1. `Dictionary` 会针对每一个Key进行一次Hash运算，从而确定自己在索引中的位置。

    >注意区分Key和索引
    >
    >Hash函数本质上是从 Key 范围到索引范围的映射，Key的范围要远远大于索引的范围。

2. Hash函数有很多种算法，最简单的可以直接做取余运算。

    - `hask_key = key % 30 = 3`

3. 实例对象和字符串，通过内存地址计算 `HashCode`。

4. 编写类时可以重写 `Object.GetHashCode() ` 方法提供自己的 `HashCode` 计算方法。

### 处理冲突

1. 处理 Hash 冲突的方法有：开放定址法，再Hash法，拉链法，建立公共溢出区等。

2. `Dictionary` 使用拉链法解决冲突。

3. 查找过程：

    - 给定Key，根据Hash函数求得Hash地址。
    - 如果桶中此索引处没有记录，表示查找不成功。
    - 否则依次比较链表中的关键字，若找到与给定值相等的，则查找成功，否则失败。

    ![image-20220509005715544](https://cdn.jsdelivr.net/gh/yzngo/picture/img/202205090057599.png)

    

### 复杂度

1. 如果冲突发生很多次，最坏情况下的时间复杂度是 $O(N) $，其中 N 是键的数量。
2. 如果有一个不错的实现方式会将冲突数量保持在最低水平，在此情况下，时间复杂度是 $O(1)$。
