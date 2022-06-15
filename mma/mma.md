零散记录
========

## 学习资料
- [官方资料中心](https://reference.wolfram.com/language/)
  - 里面的资源里有两个入门文档,**一定要读，很短**
    - 快速编程入门 https://www.wolfram.com/language/fast-introduction-for-programmers/zh/
    - 面向数学学习的快速入门指南 https://www.wolfram.com/language/fast-introduction-for-math-students/zh/
  - ["How to" 分类主题](https://reference.wolfram.com/language/guide/HowToTopics.html)
    - [清除变量](https://reference.wolfram.com/language/howto/ClearMyDefinitions.html) 

## 清楚变量
- 清除所有变量：`ClearAll["Global`*"]`。
  - 麻烦的语法。稍微解释下。ClearAll包含两套功能: `Clear` + `ClearAttributes`。
- 其他相关的命令
  - 查看符号定义的信息：`?x`
  - 删掉变量: `Remove`。比如`Remove[x];?x`，会输出`Missing["UnknownSymbol", "x"]`
  - 查看所有的全局变量：`Names["Global`*"]`。
    - 特殊的：```Names["Global`*"];Names["Global`*"]```输出`{}`

## Wolfram Documentation Center 
- tutorial/Expressions
  - Everything Is an Expression
  - `FullForm[%]`可以转换成统一的模式，类似前缀表达式的函数调用。
  - 表达式有四种形式：`f[x,y]`,`f@(x,y)`,`x,y//f`,`x~f~y`，f可以理解成函数，**注意`@`的优先级很高。**

## 函数
在 Wolfram 语言中，函数定义只是给出模式变换规则的赋值.
一个斐波拉切+黄金分割的例子。
```mma
ClearAll[a,b];
a[0] = a[1] = 1;
a[n_] := a[n] = a[n - 1] + a[n - 2];(* 斐波拉契数列 *)
b[n_] := a[n]/a[n + 1] ~N~10;(* b逼近黄金比例 *)
```
这儿`a[n_]`的定义里一定要加上`a[n]=`，不然速度非常慢，加上后相当于记住里中间的结果。