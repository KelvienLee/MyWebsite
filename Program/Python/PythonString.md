# Python 字符串

## 索引

> 索引越界会报错

```python
>>> content = "hello world."
>>> print(content[1])
e
>>> print(content[-2])
d
```

## 切片(不包含右值)

> 切片越界会自动处理

```python
>>> content = "hello world."
>>> print(content[1])
e
>>> print(content[-2])
d
>>> content = "hello world."
>>> print(content[2:4])
ll
>>> print(content[:5])
hello
>>> print(content[-1:])
.
>>> print(content[:-1])
hello world
```

## 字符串运算

| **操作符** | **描述**                                                     |
| ---------- | ------------------------------------------------------------ |
| +          | 字符串连接                                                   |
| *          | 重复输出字符串                                               |
| []         | 通过索引获取字符串中字符                                     |
| [ : ]      | 截取字符串中的一部分，遵循**左闭右开**原则                   |
| in         | 成员运算符 - 如果字符串中包含给定的字符返回 True             |
| not in     | 成员运算符 - 如果字符串中不包含给定的字符返回 True           |
| r/R        | 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 |
| %          | 格式字符串                                                   |



## 字符串内建函数



###  字符串查找

1. str.count(sub, [start= 0,end=len(string)])

   > 返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数

   ```python
   >>> str = "hello world."
   >>> print(str.count('l'))
   3
   ```

2. len(string)

    > 返回字符串长度


3. str.find(str, beg=0, end=len(string))

   > find() 方法检测字符串中是否包含子字符串 str ，如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回-1

   ```python
   >>> str = 'hello world.'
   >>> str.find('ll')
   2
   >>> str.find('x')
   -1
   ```

4. rfind(str, beg=0,end=len(string))

    > 类似于 find()函数，不过是从右边开始查找.


5. str.index(str, beg=0, end=len(string))

    > 查找指定字符的索引 ，该方法与find()方法相似，但如果str不在 string中会报一个异常。

    ```python
    >>> str = 'hello world.'
    >>> str.index('ll')
    2
    >>> str.index('x')
    Traceback (most recent call last):
      File "<input>", line 1, in <module>
        str.index('x')
    ValueError: substring not found
    ```

6. rindex( str, beg=0, end=len(string))

    > 类似于 index()，不过是从右边开始.


7. startswith()

    > startswith() 方法用于检查字符串是否是以指定子字符串开头，如果是则返回 True，否则返回 False。如果参数 beg 和 end 指定值，则在指定范围内检查。

    ```python
    >>> str = '2021-3_test.png'
    >>> str.startswith('2021')
    True
    ```

8. str.endswith(suffix[, start[, end]])

   > 判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回 True，否则返回 False。

   ```python
   >>> str = 'song.mp3'
   >>> print(str.endswith('mp3'))
   True
   >>> print(str.endswith('mp4'))
   False
   ```


### 字符串修剪


1. str.join(sequence)

    > Python join() 方法用于将序列中的元素以指定的字符连接生成一个新的字符串。

    ```python
    >>> list = ['life', 'is', 'short', 'i', 'use', 'python']
    >>> '-'.join(list)
    'life-is-short-i-use-python'
    ```

2. replace(old, new [, max])

    > 把 将字符串中的 old 替换成 new,如果 max 指定，则替换不超过 max 次。

    ```python
    >>> str = 'hello world'
    >>> str.replace('world', 'python')
    'hello python'
    >>> 
    ```

3. strip([chars])

    > 移除头尾指定字符

    ```python
    >>> str = '###this is a# test,# you # need py#thon.###'
    >>> str.strip('#')
    'this is a# test,# you # need py#thon.'
    # replace()可以移除所有指定字符
    >>> str.replace('#', '')
    'this is a test, you  need python.'
    ```

4. lstrip()

    > 截掉字符串左边的空格或指定字符。

    ```python
    >>> str = '     hello world'
    >>> str.lstrip()
    'hello world'
    ```

5. rstrip()

    > 删除字符串末尾的空格或指定字符。

    ```python
    >>> str = 'hello world    '
    >>> str.rstrip()
    'hello world'
    >>> str = 'hello world'
    >>> str.rstrip('ld')
    'hello wor'
    ```

6. split(str="", num=string.count(str))

    > 以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串

    ```python
    >>> str = 'this is a test.'
    >>> str.split('s')
    ['thi', ' i', ' a te', 't.']
    ```

7. splitlines([keepends])

    > 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。

    ```python
    >>> str = """hello world
    ... this is a test
    ... life is short , i use python.
    ... """
    >>> str.splitlines()
    ['hello world', 'this is a test', 'life is short , i use python.']
    ```



### 字符串转换

1. title()

   > 返回"标题化"的字符串,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle())

   ```python
   >>> str = 'hello world'
   >>> str.title()
   'Hello World'
   ```

2. upper()

   > 转换字符串中的小写字母为大写

   ```python
   >>> str = 'this is a test.'
   >>> str.upper()
   'THIS IS A TEST.'
   ```

3. lower()

    > 转换字符串中所有大写字符为小写.


4. swapcase()

    > 将字符串中大写转换为小写，小写转换为大写

    ```python
    >>> str = 'hello world'
    >>> str.swapcase()
    'HELLO WORLD'
    ```

5. capitalize()

   > 将字符串的第一个字符转换为大写

   ```python
   >>> str = "hello world."
   >>> print(str.capitalize())
   Hello world.
   ```

6. expandtabs(tabsize=8)

   > 把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8 。

   ```python
   >>> str = 'hello\tworld'
   >>> print(str)
   hello   world
   >>> print(repr(str))
   'hello\tworld'
   >>> print(str.expandtabs())
   hello   world
   >>> print(repr(str.expandtabs()))
   'hello   world'
   ```

7. str.encode(encoding='UTF-8',[errors='strict'])

   > encode() 方法以指定的编码格式编码字符串。

   ```python
   >>> str_zh = '微光小九'
   >>> str_zh_utf8 = str_zh.encode('UTF-8')
   >>> print(str_zh_utf8)
   b'\xe5\xbe\xae\xe5\x85\x89\xe5\xb0\x8f\xe4\xb9\x9d'
   >>> print(str_zh_utf8.decode('UTF-8'))
   微光小九
   ```



### 判断字符串

1. str.isdigit()

    > 如果字符串只包含数字则返回 True 否则返回 False。

    ```python
    >>> str = 'hello 0112'
    >>> str.isdigit()
    False
    >>> str = '0112'
    >>> str.isdigit()
    True
    ```

2. str.isnumeric()

    > 检测字符串是否只由数字组成，数字可以是： Unicode 数字，全角数字（双字节），罗马数字，汉字数字。指数类似 **²** 与分数类似 **½** 也属于数字。

    ```python
    >>> str = '1二'
    >>> str.isnumeric()
    True
    ```

3. str.isalnum()

    > 如果字符串至少有一个字符并且所有字符都是字母或数字或**中文字**则返回 True, 否则返回 False

    ```python
    >>> str = 'hello world.'
    >>> str.isalnum()
    False						# 包含空格和标点都不行
    >>> str = 'helloworld'
    >>> str.isalnum()
    True
    >>> str = 'hello8world'
    >>> str.isalnum()
    True
    >>> str_zh = '微光小九'
    >>> str_zh.isalnum()
    True
    >>> str_zh = '微光小九,'
    >>> str_zh.isalnum()
    False
    ```

4. str.isalpha()

    > 与isalnum()的区别是，此方法不能包含数字

    ```python
    >>> str = 'hello0112'
    >>> str.isalpha()
    False
    >>> str = 'hello九九'
    >>> str.isalpha()
    True
    >>> 
    ```

5. isupper()

    > 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False

6. islower()

    > 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False

7. isspace()

    > 如果字符串中只包含空白，则返回 True，否则返回 False.

8. istitle()

    > 如果字符串是标题化的(见 title())则返回 True，否则返回 False

9. isdecimal()

   > 检查字符串是否只包含十进制字符，如果是返回 true，否则返回 false。

   ```python
   >>> str = 'hello 0112'
   >>> str.isdecimal()
   False
   >>> str = '1212122121'
   >>> str.isdecimal()
   True
   ```




### 其他
1. center()

   > 返回一个指定的宽度 width 居中的字符串，fillchar 为填充的字符，默认为空格。

   ```python
   >>> str = "hello world."
   >>> print(str.center(50, '-'))
   -------------------hello world.-------------------
   ```

2. ljust()

   > ljust() 方法返回一个原字符串左对齐,并使用空格填充至指定长度的新字符串。如果指定的长度小于原字符串的长度则返回原字符串。

   ```python
   >>> str = 'hello'
   >>> str.ljust(50, '-')
   'hello---------------------------------------------'
   ```

3. rjust(width,[, fillchar])

   > 返回一个原字符串右对齐,并使用fillchar(默认空格）填充至长度 width 的新字符串

   ```python
   >>> str = 'world'
   >>> str.rjust(50, '-')
   '---------------------------------------------world'
   ```


4. max(str)

    > 返回字符串 str 中最大的字母或数字。

    ```python
    >>> str = 'abc'
    >>> max(str)
    'c'
    >>> str = '123'
    >>> max(str)
    '3'
    >>> 
    ```

5. min(str)

    > 返回字符串 str 中最小的字母或数字。
