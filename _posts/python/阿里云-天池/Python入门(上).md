---
layout: post
title: Python入门(上)
categories: [Python]
description: None
keywords: Python, 初学
---

## 前言
本人有一定的Java基础，最近准备做python相关的项目，其中的术语可能会和JAVA代码对比。

代码是写出来的，不是记出来的，动起来！

## 变量、运算符、数据类型与包的导入

#### 1. 注释
``` python
# 单行注释

'''
多行注释
单引号和双引号皆可
'''

print("hello")
```

#### 2. 运算符
##### 算数运算符
```python
# 常规的加减乘除
print(1 + 1)  # 2
print(2 - 1)  # 1
print(3 * 4)  # 12
print(3 / 4)  # 0.75
print(3 % 4)  # 3 

# 不相同的内容
print(3 // 4)  # 0  -地板除
print(2 ** 3)  # 8  -幂运算
```

##### 比较运算符

和其他语言无不同之处

#####  逻辑运算符

| 操作符 | 名称 | 示例                  | 结果                |
| ------ | ---- | --------------------- | --------------------- |
| and  | 与   | print((3 > 2) and (3 < 5)) | False |
| or   | 或   | (1 > 3) or (9 < 2)  | True |
| not  | 非   | not (2 > 1)        | False   |

##### 位运算符

| 操作符 | 名称     | 示例     |
| ------ | -------- | -------- |
| `~`    | 按位取反 | `~4`     |
| `&`    | 按位与   | `4 & 5`  |
| `      | `        | 按位或   |
| `^`    | 按位异或 | `4 ^ 5`  |
| `<<`   | 左移     | `4 << 2` |
| `>>`   | 右移     | `4 >> 2` |

##### 三元运算符

```python
x, y = 3,5
print(x if x < y else y)

# java
# int x = 3;
# int y = 5;
# int temp = x < y ? x : y;
```

**其他运算符**

| 操作符   | 名称   | 示例                         |
| -------- | ------ | ---------------------------- |
| `in`     | 存在   | `'A' in ['A', 'B', 'C']`     |
| `not in` | 不存在 | `'h' not in ['A', 'B', 'C']` |
| `is`     | 是     | `"hello" is "hello"`         |
| `is not` | 不是   | `"hello" is not "hello"`     |

in 和 not in 在列表、元组、字典中将会很常用，记牢哦

注意点：

- ==,  != 对比的是两个变量的值
- is, is not 对比的是两个变量的内存地址

简单来说，当类型为列表、元组、字典时，这两个数据是不相同的

#### 3. 变量和赋值

```python
my_teacher = "老马的程序人生"
your_teacher = "小马的程序人生"
our_teacher = my_teacher + ',' + your_teacher
# 只有变量，不用定义哦

set_1 = {"欢迎", "学习","Python"}
print(set_1.pop()) # 欢迎
```

#### 4. 数据类型和转换

```python
a = 1031
print(a, type(a))
# type直接查看变量a的类型

b = dir(int)
print(b)
# dir获取对象的属性和方法，类比Java：
# sout(Student.getClass())
```

#### 5. 两种方式导入包

导入包有两种方式：

```python
# 只导入了decimal
import decimal
from decimal import Decimal
```
在代码中比较一下两种方式的区别
<center>
    <img src="/images/posts/blog/Python入门/导入方式的区别.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>
可以发现在第四行，第一种方式有前缀，第二种方式没有前缀。

但是第二种方式在获取方法时报错，需要添加上第一种方式，才能找到对应的方法

**建议**：使用第一种方式，代码会更清晰
