---
title: C++容器 - vector
date: 2019-06-07 14:10:00 +0800
categories: [Language, CPP]
tags: [cpp]


---



## vector

[对比C#容器 - List]({%link _posts/Language/CSharp/2019-06-01-CSharp泛型类-List.md %})

 

## vector定义和初始化

1. 初始化时使用**圆括号 ()**代表调用构造函数构造 vector 对象。
2. 初始化时使用**花括号 {}**代表使用初始化列表初始化 vector 中的对象。

```c++
#include <vector>
using std::vector;

vector<int> v1; 			// 默认初始化，vector为空， size=0
vector<int> v2(v1); 		// 直接初始化
vector<int> v2 = v1;		// 拷贝初始化
		 // 会原样拷贝，这里没有指针的概念，注意和 C# 的引用类型区分
vector<int> v3 = {1,2,3.0,4,5,6,7};		// 初始化列表初始化
vector<int> v4(v3.begin() + 2, v3.end() - 1);  // v4 初始化为两个迭代器指定范围中元素的拷贝
vector<int> v5(7); 		// 默认值初始化，v5 中将包含7个元素，每个元素进行缺省的值初始化
vector<int> v6(7, 3); 	// 指定值初始化，v6 被初始化为包含7个值为 3 的 int

// 使用数组初始化 vector
int arr[] = {0, 1, 2, 3, 4, 5};
vector<int> v7(begin(arr), end(arr));
```

### 操作

```c++
vector<int> v;

// 向尾端添加对象
// c++一般使用 != 作为循环终止条件
for (int i = 0; i != 100; ++i) {	
    v.push_back(i);
}

// 判空
v.empty();

// 返回大小
v.size();

// 使用下标访问
// z使用下标运算符t访问已经存在的元素
for (decltype(v.size()) ix = 0; ix != 10; ++ix)
{
    v[ix] = ix;
}

sort(a.begin(), a.end());
if (a == c) {		// vector可直接判等
}
```
