---
title: Python - numpy
date: 2019-10-06 14:10:00 +0800
categories: [Language, Python]
tags: [python, http]
---



## 安装numpy

1.  `python -m pip install numpy`

## 简单使用

```python
import numpy as np
from numpy import linalg as la
from matplotlib import pyplot as plt

# matplotlib 画图
x = np.arange(1, 11)
y = 2 * x + 5
plt.title("Matplotlib demo")
plt.xlabel("x axis caption")
plt.ylabel("y axis caption")
plt.plot(x, y)
plt.show()
 
# 求矩阵的秩
a = np.array([[1,-3,4],[0,4,-10],[0,0,0]])
rank = la.matrix_rank( a )
print( rank )

# 求解线性方程组
# solusion / singular matrix
a = np.array([[1,-3,4],[0,4,-10],[0,0,0]])
b = np.array([-4,8,3])
x = np.linalg.solve( a,b )
print(x)
```



