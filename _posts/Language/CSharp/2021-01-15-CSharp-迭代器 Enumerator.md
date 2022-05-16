---
title: C# - 迭代器 Enumerator
date: 2021-01-15 14:10:00 +0800
categories: [Language, C#]
tags: [c#]

---





## 迭代器模式

1. 不需要一次返回所有数据，调用代码一次只需要获取一个元素，所以我们需要确定访问到了数组的哪个位置。



## 迭代器块

使用 `yield return` 语句实现迭代器块方法。

虽然编写的看上去是顺序执行的方法，但实际上是请求编译器创建一个状态机。

当编译器看到迭代器块时，会为状态机创建一个嵌套类型，来正确记录块中的位置和局部变量的值。

C#2提供的迭代器块，实际上可以让你再这个代码块所涉及的特定位置“暂停”当前执行流2021-01-13-CSharp-迭代器 Enumerator程，并随后携带着同样的状态返回同一位置。

```c#
public IEnumerator GetEnumerator()
{
    for (int i = 0; i < values.Length; ++i) {
        yield return value[i];
    }
}
```



## IEnumerable 接口

为自定义类型实现迭代的功能, 实现 `IEnumerable` 接口。

如果某个类型实现了IEnumerable接口，就意味着它可以被迭代访问。

把可迭代序列和迭代器分开，使得多个迭代器可以同时独立地操作同一个序列。

```c#
// IEnumerable相当于数据库中的表
public class CountingEnumerable : IEnumerable<int>		
{
    // 因为C#不能以返回类型区分两个重载方法
    // 隐式实现 IEnumerator  
    public IEnumerator<int> GetEnumerator()
    {
        return new CountingEnumerator();
    }

    // 使用显示接口实现 IEnumerable
    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
    
    // IEnumerator内部类相当于数据库中的游标
    private class CountingEnumerator : IEnumerator<int>		
    {
        private int current = -1;
        
        public bool MoveNext()
        {
            current++;
            return current < 10;
        }

        public void Reset()
        {
            current = -1;
        }

        public int Current => current;

        object IEnumerator.Current => Current;

        public void Dispose()
        {
        }
    }
}
```

