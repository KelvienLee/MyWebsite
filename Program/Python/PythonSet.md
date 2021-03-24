# Python 集合

## 数据类型

> 集合是无序的不重复的元素序列。
>
> 集合是可变数据类型, 可以“增删改查”

## 创建集合

```python
>>> a = set('hello')
>>> a
{'e', 'h', 'l', 'o'}
>>> b = {'hello', 'world', 'this', 'is', 'a', 'test'}
>>> b
{'is', 'this', 'a', 'test', 'hello', 'world'}

```

## 集合间的运算

```python

>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # 集合a中包含而集合b中不包含的元素
{'r', 'd', 'b'}
>>> a | b                              # 集合a或b中包含的所有元素
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # 集合a和b中都包含了的元素
{'a', 'c'}
>>> a ^ b                              # 不同时包含于a和b的元素
{'r', 'd', 'b', 'm', 'z', 'l'}
```

## [集合的内置方法](https://www.runoob.com/python3/python3-set.html)

| 方法                          | 描述                                                                                           |
| ----------------------------- | ---------------------------------------------------------------------------------------------- |
| add()                         | 为集合添加元素                                                                                 |
| clear()                       | 移除集合中的所有元素                                                                           |
| copy()                        | 拷贝一个集合                                                                                   |
| difference()                  | 返回多个集合的差集                                                                             |
| difference_update()           | 移除集合中的元素，该元素在指定的集合也存在。                                                   |
| discard()                     | 删除集合中指定的元素                                                                           |
| intersection()                | 返回集合的交集                                                                                 |
| intersection_update()         | 返回集合的交集。                                                                               |
| isdisjoint()                  | 判断两个集合是否包含相同的元素，如果没有返回 True，否则返回 False。                            |
| issubset()                    | 判断指定集合是否为该方法参数集合的子集。                                                       |
| issuperset()                  | 判断该方法的参数集合是否为指定集合的子集                                                       |
| pop()                         | 随机移除元素                                                                                   |
| remove()                      | 移除指定元素                                                                                   |
| symmetric_difference()        | 返回两个集合中不重复的元素集合。                                                               |
| symmetric_difference_update() | 移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。 |
| union()                       | 返回两个集合的并集                                                                             |
| update()                      | 给集合添加元素                                                                                 |
