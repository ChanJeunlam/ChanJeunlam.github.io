---
layout: post
title: "python进阶（二）: set(集合)，三元运算符"
date: 2023-01-18
description: "主要包括python一些不太常见的知识点以及python高阶编程需要用到的知识点等等"
tag: Python
---   

这一讲主要是介绍了set(集合)数据结构，三元运算符等等内容。


## set(集合)数据结构

set(集合)是一个非常有用的数据结构。它与列表(list)的行为类似，区别在于set不能包含重复的值。
这在很多情况下非常有用。例如你可能想检查列表中是否包含重复的元素，你有两个选择，第一个需要使用for循环，就像这样：

```python
some_list = ['a', 'b', 'c', 'b', 'd', 'm', 'n', 'n']

duplicates = []
for value in some_list:
    if some_list.count(value) > 1:
        if value not in duplicates:
            duplicates.append(value)

print(duplicates)
```

输出结果为：

```console
['b', 'n']
```

但还有一种更简单更优雅的解决方案，那就是使用集合(sets)，你直接这样做：
```python
some_list = ['a', 'b', 'c', 'b', 'd', 'm', 'n', 'n']
duplicates = set([x for x in some_list if some_list.count(x) > 1])
print(duplicates)
```

### 交集
你可以对比两个集合的交集（两个集合中都有的数据），如下：
```python
valid = set(['yellow', 'red', 'blue', 'green', 'black'])
input_set = set(['red', 'brown'])
print(input_set.intersection(valid))
```
输出结果为：{'red'}

### 差集

你可以用差集(difference)找出无效的数据，相当于用一个集合减去另一个集合的数据，例如：

```python
valid = set(['yellow', 'red', 'blue', 'green', 'black'])
input_set = set(['red', 'brown']) 
print(input_set.difference(valid)) 
```
```
输出结果为：{'brown'}

### 并集
你可以用并集（union）来合并两个集合，如下：

```python
valid = set(['yellow', 'red', 'blue', 'green', 'black'])
input_set = set(['red', 'brown'])
print(input_set.union(valid))
```
输出结果为：{'brown', 'red', 'green', 'black', 'blue', 'yellow'}

## 三元运算符


三元运算符通常在Python里被称为条件表达式，这些表达式基于真(true)/假(not)的条件判断，在Python 2.4以上才有了三元操作。

它允许用简单的一行快速判断，而不是使用复杂的多行if语句。 这在大多数时候非常有用，而且可以使代码简单可维护。

伪代码如下：

```console
condition_is_true if condition else condition_is_false
```
举例子：
```python
is_fat = True
state = "fat" if is_fat else "not fat"
print(state)
```

输出结果为：fat

另一个晦涩一点的用法比较少见，它使用了元组，请继续看：

伪代码:
```console
#(返回假，返回真)[真或假]
(if_test_is_false, if_test_is_true)[test]
```
```python
fat = True
fitness = ("skinny", "fat")[fat]
print("Ali is ", fitness)
```
输出结果为：Ali is fat

上面的例子没有被广泛使用，而且Python玩家一般不喜欢那样，因为没有Python味儿(Pythonic)。这样的用法很容易把真正的数据与true/false弄混。

另外一个不使用元组条件表达式的缘故是因为在元组中会把两个条件都执行，而 if-else 的条件表达式不会这样。


