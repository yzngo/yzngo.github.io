---
title: C# - Object
date: 2021-01-03 14:10:00 +0800
categories: [Language, C#]
tags: [c#]

---



## Object

- `System.Object` 是所有类型的基类，任何类型都直接或间接继承自 `System.Object` 类。
- 没有指定基类的类型都默认继承于 `System.Object`。
- 所有值类型继承自 `System.ValueType`, 而 `System.ValueType` 继承自 `Object`



Object基类中的定义，经常需要**重写**的方法

## ToString

1. 默认情况下，对象调用 `ToString()` 方法将返回类型全名称，也就是命名空间加类型名全称

```c#
public virtual string ToString()
{
    return this.GetType().FullName.ToString();
}
```



## Equals

1. 默认的实现其实比较的是两个对象的内存地址
2. `System.ValueType()` 对 `Equals()` 和 `==` 操作符进行了重写，是逐字节比较的。
3. 值类型使用 `Equals()` 时，因为 `Equals()` 使用了反射，在比较时会影响效率。

```c#
public virtual bool Equals(object obj)
{
　　 if( obj == null ) return false;
　　 if(GetType() != obj.GetType()) return false;
　　 return true;
}
```



## GetHashCode

1. 重写 `Equals()` 也要重写 `GetHashCode()`

```c#
public virtual int GetHashCode() 
{
}
```