# Python基础

## 流程控制

### 三元运算符

```python
>>> a = 10
>>> b = 5
>>> c = a if a >= b else b
>>> print(c)
10
```

### 省略判断条件

| 数据类型            | 结果                      |
| ------------------- | ------------------------- |
| Str                 | 空字符串为False           |
| int                 | 0为False                  |
| bool                | False为False              |
| list/tuple/dict/set | 迭代对象为空时解析为False |
| object              | None为False               |



## 循环语句

### while 循环

```python
>>> i = 0 
>>> while i < 10:
...     i += 1
...     print(i)
... 
1
2
3
4
5
6
7
8
9
10

```

### while 嵌套

```python
i = 0
while i < 9:
    i += 1
    j = 0
    while j < i:
        j += 1
        r = i * j
        print(f'{i} * {j} = {r}', end='   ')
    print('\n', end='')
```

### for 循环

```python
>>> for i in range(10):
...     print(i)
...      
0
1
2
3
4
5
6
7
8
9
```

### for 嵌套

```python
>>> for i in range(10):
...     for j in range(1, i):
...         r = i * j
...         print(f'{j} * {i} = {r}', end='  ')
...     print('\n')

```

### break语句

```python
>>> for i in range(10):
...     if i == 6:
...         break
...     print(i)
...     
... 
0
1
2
3
4
5
```

### continue语句

```python
>>> for i in range(10):
...     if i == 4 or i == 7:
...         continue
...     print(i)
...     
... 
0
1
2
3
5
6
8
9
```

### 循环else子句

```python
>>> for i in range(0, 10, 2):
...     print(i)
... else:
...     print('没有遇到break，循环正常结束才会运行else里的命令')
...     
... 
0
2
4
6
8
没有遇到break，没有环正常结束才会运行else里的命令
```

 

