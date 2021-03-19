# Python 元组 

## 数据类型

> 元组是不可变数据类型，这意味着元组的元素不能被修改。

> **注意** 元组中只包含一个元素时，需要在元素后添加逗号， 否则会被当作运算符使用。

	```python
	>>> tuple = (10)
	>>> type(tuple)
	<class 'int'>
	>>> tuple = (10,)
	>>> type(tuple)
	<class 'tuple'>
	```

## 索引

```python
>>> tuple = (1, 2, "hello", 5, 6.89)
>>> tuple[2]
'hello'
```

## 切片（不含右值）

```python
>>> tuple = (1, 2, "hello", 5, 6.89)
>>> tuple[0:1]
(1,)
>>> tuple[0:2]
(1, 2)
```

## 修改元组

> 一般来说，因为元组是**不可变类型**数据,所以元组是不能被修改的，因此元组只能被删除或“运算”。

```python
>>> tuple = ("hello", "world", 1, 3.14)

# 元组不能被修改,修改元组是非法的。
>>> tuple[2] = 6
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment

>>> del tuple
>>> print(tuple)
>>>
>>> tuple1 = (1, 2, 3)
>>> tuple2 = ('hello', 'world')
>>> tuple3 = tuple1 + tuple2
>>> tuple3
(1, 2, 3, 'hello', 'world')

```

## 元组运算符

| 表达式                | 结果                        |
|-----------------------|-----------------------------|
| len((1, 2, 3))        | 3                           |
| (1, 2, 3) + (4, 5, 6) | (1, 2, 3, 4, 5, 6)          |
| ('hello',) * 3        | ('hello', 'hello', 'hello') |
| 3 in (1, 2, 3)        | True                        |
| for x in (1, 2, 3)    | 1  2  3                     |

## 元组内置函数

1. len(tuple) 
	> 计算元素个数

	```python
	>>> tuple = ('hello', 'world')
	>>> len(tuple)
	2
	```

2. max(tuple)
	> 返回元组中最大值

	```python
	>>> tuple = (1, 3, 8, 0, 2, 8)
	>>> max(tuple)
	8
	
3. min(tuple)
	> 返回元组中最小值

	```python
	>>> tuple = ('a', 'c', 'd', 'z')
	>>> min(tuple)
	'a'
	```

4. tuple(iterable)
	> 将可迭代对象转换为元组

	```python
	>>> list1 = ['hello', 'world']
	>>> tuple1 = tuple(list1)
	>>> tuple1
	('hello', 'world')
	```

	


