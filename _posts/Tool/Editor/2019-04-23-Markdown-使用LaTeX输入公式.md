---
title: Markdown-使用LaTeX输入公式
date: 2019-04-23 14:10:00 +0800
categories: [Tool, Editor]
tags: [markdown,blog]
mermaid: true
math: true

---

>如果使用Jekyll发布，FrontMatter中需要添加 `math: true`
{: .prompt-info }



##  上标和下标

| 符号                 | 示例            | LaTeX             | 备注                 |
| -------------------- | --------------- | ----------------- | -------------------- |
| 上标                 | $x^2$           | `x^2`             | `^`                  |
| 下标                 | $x_0$           | `x_0`             | `_`                  |
| 上下标同时出现       | $x_0^2$         | `x_0^2` / `x^2_0` |                      |
| 上下标由多个字符组成 | $x^{n+m}_{a^2}$ | `x^{n+m}_{a^2}`   | 上下标用 `{}` 框起来 |
| 上下标嵌套           | $x^{x^{x^{x}}}$ | `x^{x^{x^{x}}}`   |                      |



## 二元运算符



 ## 二元关系符

| 符号     | 示例   | LaTeX  | 备注             |
| -------- | ------ | ------ | ---------------- |
| 不等于   | $\ne$  | `\ne`  | not equal        |
| 小于等于 | $\le$  | `\le`  | less or equal    |
| 大于等于 | $\ge$  | `\ge`  | greater or equal |
|          |        |        |                  |
| 相似     | $\sim$ | `\sim` | similar          |
|          |        |        |                  |
|          |        |        |                  |
|          |        |        |                  |



## 分式

| 符号  | 示例              | LaTeX             | 备注                  |
| ----- | ----------------- | ----------------- | --------------------- |
| 分式1 | $\frac {1} {1+x}$ | `\frac {1} {1+x}` | `\frac {分子} {分母}` |
| 分式2 | $1 \over 1+x$     | `1 \over 1+x`     | `分子 \over 分母`     |
|       |                   |                   |                       |

## 特殊字符

| 符号 | 示例 | LaTeX | 备注 |
| ---- | ---- | ----- | ---- |
| 换行 |      | `\\`  |      |
|      |      |       |      |
|      |      |       |      |
|      |      |       |      |
|      |      |       |      |





## Demo

```mathematica
$$ \sum_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6} $$
When $a \ne 0$, there are two solutions to $ax^2 + bx + c = 0$ and they are
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$
```

$$ \sum_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6} $$

When $a \ne 0$, there are two solutions to $ax^2 + bx + c = 0$ and they are

$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$



## Reference

1. [LaTex编辑器帮助文档](https://latexlive.com/help)
1. [Learn LaTeX in 30 minutes](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
2. [LaTeX-Tutorial.com](https://latex-tutorial.com/)
