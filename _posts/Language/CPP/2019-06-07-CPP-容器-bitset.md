---
title: C++容器 - bitset
date: 2019-06-07 14:10:00 +0800
categories: [Language, CPP]
tags: [cpp]
---



1.  `bitset` 用来管理一系列 bit 位及二进制串。类似于数组，但每个元素只能是 0 或 1 且每个元素仅用 1bit 的空间。
2. 用字符串构造 bitset 时，字符串只能包含 0 或 1.

## bitset定义和初始化

```c++
#include <bitset>
// 申请一个长度为 5 的 bitset, 默认每位为0
std::bitset<5> a; 
// 将12(2进制)保存在b中，前面位补0
std::bitset<8> b(12);
// 将 s 保存在c中，前面位补0
string s = "1000010";
std::bitset<10> c(s);
```

<br>


## 查询操作

```c++
bitset<8> s("10011011");

s.count();	// 5, 返回s中1的个数
s.size();	// 8, 返回s的总位数

s.test(0);	// true, 检查下标为0的元素，0：false，1：true
s.any();	// true, 检查s中是否有1
s.none();	// false, 检查s中是否没有1
s.all();	// false, 检查s中是否全为1
```

<br>

## 置位操作

```c++
bitset<8> s("10011011");

s.flip();	// 01100100, 将s整个翻转
s.flip(2);	// 10011111, 将s下标为2处取反

s.set();	// 11111111, 将s每一位都 置1
s.set(3);	// 10011011, 将s下标为3处 置1
s.set(3,0);	// 10010011, 将s下标为3处 置0

s.reset();	// 00000000, 将s每一位都 置0
s.reset(3);	// 10010011, 将s下标为3处 置0

```

<br>

## 转换操作

```c++
bitset<8> t("10011011");
string s = t.to_string();
unsigned long = t.to_ustring();
unsigned long long = t.to_ullong();
```
