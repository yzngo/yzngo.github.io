---
title: Python - 工具-把目录下文本输出到txt
date: 2019-10-07 14:10:00 +0800
categories: [Language, Python]
tags: [python]
---







## 文本文件输出到txt

申请软著时需要把代码复制到一份 word 文档中，一个个复制比较麻烦，故写了这个小工具。

可以递归的把某个文件夹下指定后缀的代码文件统一输出到一个TXT文件中。

<br>

#### 使用方法

1. 把以下代码保存为 .py 格式
2. 修改 `indir` 目录为代码所在目录
3. 修改 `outfilePath` 为输出文件
4. 修改 `wildcards` 为需要的代码文件后缀
5. 运行Python脚本

```python
# _*_ coding:utf-8 _*_
import os

def list_files_to_txt(indir, outfile, wildcards, recursion):
    exts = wildcards.split(" ")
    filelist = os.listdir(indir)
    for name in filelist:
        fullname = os.path.join(indir, name)
        if os.path.isdir(fullname) & recursion:
            list_files_to_txt(fullname, outfile, wildcards, recursion)
        else:
            for ext in exts:
                if name.endswith(ext):
                    with open(fullname, encoding='UTF-8') as infile:
                        code = infile.read()
                        outfile.write(code + "\n")
                        break


def RW():
    indir = r"C:\InputFiles\Scripts"
    outfilePath = r"C:\Users\output.txt"
    wildcards = ".cs"
    outfile = open(outfilePath, "w", encoding='UTF-8')
    if not outfile:
        print("cannot open output file")
    list_files_to_txt(indir, outfile, wildcards, 1)
    outfile.close()

RW()

```



## Debug

1. `UnicodeEncodeError: 'gbk' codec can't encode character '\ufeff' in position 0: illegal multibyte sequence`

    打开输入文件和输出文件时都要加上 `encoding='UTF-8'`
