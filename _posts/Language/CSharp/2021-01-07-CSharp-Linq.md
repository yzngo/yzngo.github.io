---
title: C# - Linq
date: 2021-01-07 14:10:00 +0800
categories: [Language, C#]
tags: [c#]

---




# Linq

**L**anguage **In**tegrated **Q**uery 语言集成查询

`using System.Linq;`

- 注意区分 Where(过滤)，Select(投影)，Take，Skip



## 聚合操作符 `Sum Count Average Min Max Aggregate`

```c#
string[] words = {"zero", "one", "two", "three", "four"};
int[] numbers = {0, 1, 2, 3, 4};

// 聚合操作符 ---------------------------------------------------
numbers.Sum();                              // 求和   10
numbers.Count();                            // 计数   5
numbers.Average();                          // 求平均 2
words.Min(word => word.Length); // 求符合selector的最小的项     3
words.Max(word => word.Length); // 求符合selector的最大的项
numbers.Aggregate("seed", (current, item) => current + item, result => result.ToUpper()); // 结果 "SEED01234"
	
```



## 连接操作符 `Concat`

```c#
string[] words = {"zero", "one", "two", "three", "four"};
int[] numbers = {0, 1, 2, 3, 4};

// 连接操作符 ---------------------------------------------------
numbers.Concat(new[] {2,3,4,5,6});		// 连接 0,1,2,3,4,2,3,4,5,6
    
```



## 转换操作符 `ToArray ToList ToDictionary ToLookup`

```c#
string[] words = {"zero", "one", "two", "three", "four"};
int[] numbers = {0, 1, 2, 3, 4};
// 转换操作符 ---------------------------------------------------
numbers.ToArray();			// 转换为 int[]
numbers.ToList();			// 转换为 List<int>
words.ToDictionary(w => w.Substring(0,2));	// 每个键只能出现一次，否则会抛出异常
words.ToLookup(word => word[0]);
```



## 元素操作符 `ElementAt First Last Single`

```c#
    // 元素操作符 --------------------------------------------------
    string[] words = {"zero", "one", "two", "three", "four"};
    int[] numbers = {0, 1, 2, 3, 4};
    
    words.ElementAt(2);				// "one"
    words.ElementAtOrDefault(10);		// null
    
    words.First();							// "zero"
    words.First(w => w.Length == 3);				// "one"
    words.First(w => w.Length == 10);				// 异常
    words.FirstOrDefault(w => w.Length == 10);		// null
    
    words.Last();				// "four"
    words.Single();					// 异常，不止一个
    words.SingleOrDefault();			// 异常，不止一个
    words.Single(word => word.Length == 5);			// "three"
    words.Single(word => word.Length == 10);			// 异常
    words.SingleOrDefault(w => w.Length == 10);			// null
    
```



## 相等操作符 `SequenceEqual`

```c#

    // 相等操作符 --------------------------------------------------
	words.SequenceEqual(new []{"zero", "one", "two", "three", "four"});
    words.SequenceEqual(new[] {"zero", "one", "two", "three", "four"}, StringComparer.OrdinalIgnoreCase);


```



## 生成操作符 `DefaultIfEmpty Range Repeat`

```c#
    // 生成操作符 --------------------------------------------------
    numbers.DefaultIfEmpty();	// 序列不为空，返回原始序列，否则返回含有单个元素的序列，其中的元素是相应类型的默认值
    Enumerable.Range(15, 2);		// 15，16
    Enumerable.Repeat(26, 2);		// 26，26
    
```



## 分组操作符 `ToLoopup GroupBy Take Skip TakeWhile SkipWhile`

```c#

	// 分组操作符 --------------------------------------------------
	string[] words = {"zero", "one", "two", "three", "four"};
    int[] numbers = {0, 1, 2, 3, 4};
	
    words.ToLookup(word => word[0]);

    words.GroupBy(word => word.Length);			// 括号内为分组的键
    words.GroupBy(word => word.Length, word => word.ToUpper());
    
    words.Take(2);			// 取前2个
    words.Skip(2);			// 跳过前2个
    words.TakeWhile(word => word.Length <= 4);	// 取，直到不满足谓词要求 "zero", "one", "two"
    words.SkipWhile(word => word.Length <= 4);	// 跳过，直到不满足谓词要求 "three", "four"
```



## 投影操作符 `Select`

```c#

	// 投影操作符 --------------------------------------------------
	// 依照给定的规则，由序列中的每一项生成另一个元素。即：从源元素到结果元素的一对一投影。
    words.Select(word => word.Length);		// 4，3，3，5，4
    words.Select((word, index) => index.ToString() + ": " + word);	// "0: zero"......
    
```



## 检查操作符 `All Any Contains`

```c#
    // 检查操作符 --------------------------------------------------
    words.All(word => word.Length > 3);				// 是否任意一个都满足	false
    words.Any();						// 存在元素					true
    words.Any(word => word.Length == 6);			// 是否存在一个满足		false
    words.Contains("FOUR");					// 是否包含			false
    words.Contains("FOUR", StringComparer.OrdinalIgnoreCase);		// 是否包含  true
    
```



## 过滤操作符 `Where`

```c#
    // 过滤操作符 --------------------------------------------------
	// 返回符合谓词要求的
    // 注意和Select区分
    words.Where(word => word.Length > 3);	// "zero", "three", "four"
    words.Where((word, index) => index < word.Length);  	// "zero", "one", "two", "three"
    
```



## 集合操作符 `Distinct Intersect Union Except`

```c#
    // 集合操作符 --------------------------------------------------
    string[] abbc = {"a", "b", "b", "c"};
    string[] cd = {"c", "d"};
    
    abbc.Distinct();		// 去重  "a", "b", "c"
    abbc.Intersect(cd);		// 交集  "c"
    abbc.Union(cd);			// 并集  "a", "b", "c", "d"
    abbc.Except(cd);		// 差集  "a", "b"
    cd.Except(abbc);		// 差集  "d"
    
```



## 排序操作符 `OrderBy Reverse`

```c#
    words.OrderBy(w => w);
    words.OrderBy(w => w[1]);
    words.OrderByDescending(w => w.Length);
    words.OrderBy(w => w.Length).ThenBy(w => w);
    words.OrderBy(w => w.Length).ThenByDescending(w => w);
    words.Reverse();
```
