# Python 字典

## 数据类型

> 字典是可变数据类型，元组的元素能够被修改。
>
> 键必须是唯一的，但值则不必要。
>
> 键必须是不可变数据类型（字符串，数字, 元组）
>
> 注意：

1. 如果同一个键出现两次，后一个的值会被记住
2. 因为列表是可变数据类型, 所以列表不能作为字典的键

```python
>>> dict = {"key": "value", 5: 10, 8: "test", (1, 2, 3): "tuple"}
>>> dict
{'key': 'value', 5: 10, 8: 'test', (1, 2, 3): 'tuple'}

```

## 访问字典的值

```python
>>> dict = {"key": "value", "number": 1}
>>> dict["key"]
'value'
```

## 修改字典

```python
>>> dict = {"name" : "kelvin", "age": 18, "gender": "boy"}
>>> dict
{'name': 'kelvin', 'age': 18, 'gender': 'boy'}
>>> dict["name"] = "lucy"
>>> dict["hobby"] = "basketball"
>>> dict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
```

## 字典内置函数

1. len(dict)

> 计算字典元素个数，即键的总数。

```python
>>> dict = {'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> len(dict)
4
```

2. str(dict)

> 输出字典，以可打印的字符串表示。

```python
>>> dict = {'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> str(dict)
"{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}"
```

3. type(variable)

> 返回输入的变量类型，如果变量是字典就返回字典类型。

## 字典内置方法

1. radiansdict.clear()

> 删除字典内所有元素

```python
>>> dict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> dict.clear()
>>> dict
{}
```

2. radiansdict.copy()

> 返回一个字典的浅复制

```python
>>> dict = {'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> newdict = dict.copy()
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
```

3. radiansdict.fromkeys()

> 创建一个新字典，以序列 seq 中元素做字典的键，val 为字典所有键对应的初始值

```python
>>> seq = ("name", "age", "gender")
>>> dict = dict.fromkeys(seq)
>>> dict
{'name': None, 'age': None, 'gender': None}
```

4. dict.get(key, default=None)

> 返回指定键的值，如果键不在字典中返回 default 设置的默认值

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> newdict.get('name')
'lucy'
>>> newdict.get('undefined')
>>>

```

5. radiansdict.items()

> 以列表返回可遍历的(键, 值) 元组数组

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> newdict.items()
dict_items([('name', 'lucy'), ('age', 18), ('gender', 'boy'), ('hobby', 'basketball')])

```

6. radiansdict.keys()

> 返回一个迭代器，可以使用 list() 来转换为列表

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> newdict.keys()
dict_keys(['name', 'age', 'gender', 'hobby'])
```

7. radiansdict.setdefault(key, default=None)

> 和 get()类似, 但如果键不存在于字典中，将会添加键并将值设为 default

```python
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}
>>> newdict.setdefault('name')
'lucy'
>>> newdict.setdefault('other')
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'other': None}

```

8. radiansdict.update(dict2)

把字典 dict2 的键/值对更新到 dict 里

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'other': None}
>>> dict1 = {'address': 'China'}
>>> newdict.update(dict1)
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'other': None, 'address': 'China'}

```

9. radiansdict.values()

> 返回一个迭代器，可以使用 list() 来转换为列表

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'other': None, 'address': 'China'}
>>> newdict.values()
dict_values(['lucy', 18, 'boy', 'basketball', None, 'China'])
```

10. pop(key[,default])
    > 删除字典给定键 key 所对应的值，返回值为被删除的值。key 值必须给出。 否则，返回 default 值。

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'other': None, 'address': 'China'}
>>> newdict.pop('other')
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'address': 'China'}
```

11. popitem()

随机返回并删除字典中的最后一对键和值。

```python
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball', 'address': 'China'}
>>> newdict.popitem()
('address', 'China')
>>> newdict
{'name': 'lucy', 'age': 18, 'gender': 'boy', 'hobby': 'basketball'}

```
