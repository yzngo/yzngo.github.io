---
title: Python - 处理Excel
date: 2019-10-03 14:10:00 +0800
categories: [Language, Python]
tags: [python]
---



## 处理Excel

```python
import xlrd #read

"""读取excel 第r列 从 第start行 到 第end行 的单元格内容, 并按照"","",""的格式输出"""
def read_cells(r, start, end):
    workbook = xlrd.open_workbook(r'c:\xx.xlsx')
    # print( workbook.sheet_names())
    sheet1 = workbook.sheets()[0]
    # nrows = sheet1.nrows
    # ncols = sheet1.ncols
    # print(nrows, ncols)

    value = []
    for i in range(start-1, end) :
        row = sheet1.row_values(i)
        value.append("\""+row[r]+"\"")

    str = ','.join(value)
    print(str)

if __name__ == '__main__':
    read_cells(8, 31, 40)

```

