---
title: C++ string
date: 2019-06-07 14:10:00 +0800
categories: [Language, CPP]
tags: [cpp]


---



## string

1.  `string` 表示可变长的字符序列。

    

## string和char数组

1. string常用
    优点：有大量匹配的库函数

2. char数组 - 只有需要运行效率特别高时才需要用char数组
    优点：效率高



## 字符串定义和初始化

```c++
string s1;					// 默认初始化成空字符串
string s2(s1);				// s2 是 s1 的副本 - 直接初始化
string s2 = s1;				// s2 是 s1 的副本 - 拷贝初始化

string s3("hello world");	 // s3 是该字面值的副本 - 直接初始化
string s3 = "hello world";	 // s3 是该字面值的副本 - 拷贝初始化

string s4(100, 'a');		// 构造100个a组成的字符串

// y
const char* vertexShaderSource = R"(
1. XXX
2. XXX
3. XXX
    )";
```



## 字符操作

```c++
#include <cctype>

int main()
{
    char c;
    isalnum(c);		// 是数字或字母时返回 true
    isalpha(c);
    iscntrl(c);		// 控制字符
    isdigit(c);		// 是数字
    isgraph(c);
    islower(c);
    isprint(c);
    ispunct(c);
    isspace(c);
    issupper(c);
    isxdigit(c);
    tolower(c);
    toupper(c);
}
```



## 字符串处理

```c++
string s1;

// string转换成c风格字符串
const char *str = s1.c_str();
char *str = s1;	// e

// 判断字符串是否为空
s1.empty();		

// 返回 string 对象的长度 (无符号整数)
string::size_type len = s1.size();

// 使用下标访问
for (decltype(s1.size()) index = 0; index != s1.size() && !isspace(s1[index]); ++index)
{
    s1[index] = toupper(s1[i])
}

// 查找
// 从前往后查找
int index = s1.find(s);
// 从位置pos开始往后查找（包括pos）
int index = s1.find(s, pos);
// 从后往前查找
int index = s1.rfind(s);
// 从位置pos开始往前查找（包括pos）
int index = s1.rfind(s, pos);
// 若不存在则 i == string::epos

// 求子串
str.substr(2,3); // 起始序号，长度
// 删除
// 从位置pos=10处开始删除，直到结尾。
str.erase(pos); 
// 位置pos=6处开始，删除count=4个字符。
str.erase(pos, count); 
  

//字符串反转
reserve(str.begin(), str.end());  

```



## C风格字符串相关

```c++

//字符串拼接
strcat(dest, src);

//字符串复制
strcpy(dest, src);

//求字符数组的长度
strlen(str);

// 字符转换成小写/大写
tolower(c);
toupper(c);

// 字符串和数字相互转换
to_string()  // 数字转换成字符串
atoi(c_str)  // 字符串转换为数字
    

```

