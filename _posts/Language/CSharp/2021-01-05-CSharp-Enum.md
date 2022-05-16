---
title: C# - Enum枚举
date: 2021-01-05 14:10:00 +0800
categories: [Language, C#]
tags: [c#]
mermaid: true
math: true
---



## Enum

1. enum类型默认继承自 int
    ```c#
    // 其他可用类型有：byte(1B)、sbyte、short、ushort、int(4B)、uint、long、ulong
    public enum Month : int {
        
    }
    ```
    
    
## 位域 

1. 使用 `[System.Flags]` 特性, 可以把枚举作为位域处理(不一定继承byte)
   
2. 去掉一个元素的写法
   `per = per & (~Permission.R);`

    ```c#
       [Flags]
   public enum WeekDay
   {
           None =      0x00,       //0000 0000
           Sunday =    0x01,       //0000 0001
           Monday =    0x02,       //0000 0010
           Tuesday =   0x04,       //0000 0100
           Wednesday = 0x08,       //0000 1000
           Thursday =  0x10,       //0001 0000
           Friday =    0x20,       //0010 0000
           Saturday =  0x40        //0100 0000
   };
    ```

3. 使用场景举例：  
     - Unity的层级定义
     - 访问权限
     - 执行状态等



## 和String相互转换

1. 枚举值转换成字符串

    ```c#
    WeekDay.Sunday.ToString();
    ```

2. 字符串转换成枚举值

    ```c#
    System.Enum.TryParse("Idle", out WeekDay day);    // 转换失败返回false
    ```



## 和 int 相互转换

1. 枚举转换成整形, 强转就可以

    ```c#
    (int)Color.Red;
    (byte)Color.Green
    ```
    
2. 整形转换成枚举值
   
   ```c#
   // 可以强转
   (Color)2;
   // 也可以例用Enum的静态方法 
   Color color = (Color)Enum.ToObject(typeof(Color), 2);
   ```
   
3. 判断某个整形是否定义在枚举中

    ```c#
    Enum.IsDefined(typeof(Color), 2);
    ```

    

## 遍历枚举值

```c#
foreach (Suits suit in Enum.GetValues(typeof(Suits)))
{
	Console.WriteLine((int)suit+ ":" + suit);
}
```