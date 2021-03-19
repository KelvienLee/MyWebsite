# Python 列表基础操作

## 索引

```python

>>> list = ['hello', 'world', 'this', 'is', 'a', 'test']
>>> lsit[1]
'world'

```

## 切片

```python

>>> list = ['hello', 'world', 'this', 'is', 'a', 'test']
>>> list[2:]
['this', 'is', 'a', 'test']

```

## 更新列表

```python

>>> list = ['hello', 'world']
>>> list
['hello', 'world']
>>> list[1] = 'python'
>>> list
['hello', 'python']

```

## 删除列表元素

```python

>>> list
['hello', 'python']
>>> del list[1]
>>> list
['hello']

```

## 列表操作符

| 表达式                | 结果                        |
|-----------------------|-----------------------------|
| len([1, 2, 3])        | 3                           |
| [1, 2, 3] + [4, 5, 6] | [1, 2, 3, 4, 5, 6]          |
| ['hello'] * 3         | ['hello', 'hello', 'hello'] |
| 3 in [1, 2, 3]        | True                        |


## 列表函数

1. len(list)
	> 返回元素个数

2. max(list)
	> 返回列表元素最大值

	```python
	>>> list = ['a', 'b', 'c', 'd']
	>>> max(list)
	'd'
	```
	
3. min(list)
	> 返回列表元素最小值

	```python
	>>> list = [1, 2, 3, 4]
	>>> min(list)
	1
	```

4. list(seq)
	> 将元组转换为列表


## 列表方法

1. list.append(obj)
	> 在列表末尾添加新的对象

	```python
	>>> a = [4, 5]
	>>> list = [1, 2, 3]
	>>> list.append(a)
	>>> list
	[1, 2, 3, [4, 5]]
	>>> b = 6
	>>> list.append(b)
	>>> list
	[1, 2, 3, [4, 5], 6]
	```
	
2. list.count(obj)
	> 统计某个元素在列表中出现的次数

	```python
	>>> list = [1, 3, 4, 2, 3, 6, 3, 9, 3, 5, 9]
	>>> list.count(3)
	4
	```
	
3. list.extend(seq)
	> 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）

	```python
	>>> list = [1, 2, 3]
	>>> list2 = [4, 5, 6]
	>>> list.append(list2)
	>>> list
	[1, 2, 3, [4, 5, 6]]
	
	# 注意与append()方法的区别
	>>> list = [1, 2, 3]
	>>> list2 = [4, 5, 6]
	>>> list.extend(list2)
	>>> list
	[1, 2, 3, 4, 5, 6]
	```
	
4. list.index(obj)
	> 从列表中找出某个值第一个匹配项的索引位置

	```python
	>>> list = [1, 2, 3, 5, 8, 5]
	>>> list.index(5)
	3
	```
	
5. list.insert(index, obj)
	> 将对象插入列表

	```python
	>>> list = ['this', 'is', 'test']
	>>> list.insert(2, 'a')
	>>> list
	['this', 'is', 'a', 'test']
	```
	
6. list.pop([index=-1])
	> 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值

	```python
	>>> list = ['this', 'is', 'a', 'test']
	>>> list.pop()
	'test'
	>>> list
	['this', 'is', 'a']
	>>> list.pop(1)
	'is'
	>>> list
	['this', 'a']
	```
	
7. list.remove(obj)
	> 移除列表中某个值的第一个匹配项

	```python
	>>> list = [1, 3, 5, 8, 6, 3, 3]
	>>> list.remove(3)
	>>> list
	[1, 5, 8, 6, 3, 3]
	```
	
8. list.reverse()
	> 反向列表中元素

	```python
	>>> list = [1, 2, 3, 4, 5]
	>>> list.reverse()
	>>> list
	[5, 4, 3, 2, 1]
	```
	
9. list.sort( key=None, reverse=False)
	> 对原列表进行排序

	```python
	>>> list = [3, 5, 1, 8, 0, 6]
	>>> list.sort()
	>>> list
	[0, 1, 3, 5, 6, 8]
	>>> list.sort(reverse=True)
	>>> list
	[8, 6, 5, 3, 1, 0]
	```
	
10. list.clear()
	> 清空列表

	```python
	>>> list = ['hello', 'world']
	>>> list.clear()
	>>> list
	[]
	```
	
11. list.copy()
	> 复制列表

	```python
	>>> list = [1, 3, 5]
	>>> list2 = list.copy()
	>>> list2
	[1, 3, 5]
	```
	
