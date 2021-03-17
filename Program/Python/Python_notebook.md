# Python 学习笔记



## Chapter_8 函数基础

### 创建函数

* 函数命名应当使用小写字母加下划线的形式

  ```python
  def say_hi():
      print('hello world')
      print('welcome to weiguang19')
  
  
  say_hi()
  ```



### 使用函数的优点

1. 实现代码复用
2. 函数单一功能，便于管理和调用
3. 提高代码可读性



### 函数的参数

1. 普通参数
2. 默认参数
3. 关键字参数
4. 不定长参数

```python
# 函数的参数
# 普通参数
# 必须为每一个参数赋值，否则会报错
def window(width, height):
    print(f'window width:{width} \nwindow height: {height}')


# 普通参数按照顺序输出
window(25, 80)

# 定义参数(关键字参数）
window(height=18, width=9)


# 默认参数
def total(hour, salary=20):
    print(f'total salary of today: {hour*salary}')


# 定义了默认参数，在使用时如果不定义对应参数，会使用默认值，如果定义了参数则使用定义的参数
total(8)
total(12, 10)


# 关键字参数
def student(firstname, lastname):
    print(f'firstname is:{firstname}\nlastname is:{lastname}')


student('kelvin', 'Lee')


# 不定长参数
def my_function(height, age, *args, **kwargs):
    print(height)
    print(age)
    print(args)         # 将args输出为一个元组
    print(kwargs)       # 将kwargs输出为一个字典
    for arg in args:    # 遍历元组
        print(arg)
    for key, value in kwargs.items():       # 遍历字典
        print(f'{key}:{value}')


my_function(170, 18, 'hello', 'world', 'I', 'am', 'coming', lastname='kelvin', firstname='Lee')

```



### 函数的返回值

```python
# 函数的返回值
# 函数运行完成后返回的结果（值）
pi = 3.14


def area(r):
    return pi * (r ** 2)


print(area(2))


# 将分钟转换为时分
def minute_hour_exchange(input_minutes):
    hour = input_minutes // 60
    minute = input_minutes % 60
    return hour, minute


usr_input = int(input('input:'))
print(minute_hour_exchange(usr_input))                  # 返回元组
hours, minutes = minute_hour_exchange(usr_input)        # 将元组拆包
print(f'{usr_input}分钟是：{hours}小时 {minutes}分钟')
```



### 函数的作用域

```python
# 函数的作用域
# 全局变量
# 可变类型
a = 300
print(a)

# 不可变类型
b = [1, 2, 3]
print(b)


# 局部变量
def test1():
    a_fuc = 100
    print(a_fuc)
    # 对于不可变类型，需要使用global声明此操作可作用于全局
    global a
    a = 500
    # 对于可变类型，不需要任何声明也能作用于全局
    b.append(4)


test1()
print(a)
print(b)
```



### 函数的嵌套使用

```python
# 函数的嵌套
def get_up():
    print('睁开眼睛')
    print('穿衣服')
    print('洗脸')
    print('刷牙')


def breakfast():
    print('做早餐')
    print('吃早餐')


# 函数的内部嵌套调用
def to_work():
    get_up()
    breakfast()


to_work()


# 函数的内部嵌套定义编写
def test1():
    a = 10
    print('test1 starts execution.')
    print(f'test1 internal variable:{a}')

    def test2():
        nonlocal a
        a = 100
        print('test2 starts execution.')
        # 内部未定义变量的值会依次向外部寻找
        print(f'test2 internal variable:{a}')

    # 提示：使用了nonlocal函数便不能再使用global函数
    test2()
    print('test1 starts execution.')
    print(f'test1 internal variable:{a}')


test1()

```



### 函数的递归

```python
# 函数的递归（函数内部调用函数）
def fact(n):
    if n == 1:
        return 1
    result = n * fact(n - 1)
    return result


print(fact(3))

# 使用递归函数时要防止栈溢出，不要过多的使用递归次数
```



### 匿名函数

```python
# 匿名函数
# 使用lambda表达式创建匿名函数

# 普通函数形式
def add(x, y):
    return x + y


result = add(5, 3)
print(result)

# lambda匿名函数形式
expression = (lambda x, y: x + y)
# 可直接在lambda函数后赋默认值，但是在调用时不能再赋其他的值，否则会报错
expression2 = (lambda x, y: x + y)(10, 10)
print(expression(5, 10))
print(expression2)

# 注意：lambda是一个表达式，并不是一个语句
# 表达式：用一个公式去表达一个东西
# 语句：完成了某些功能

# 表达式的应用
# 列表中使用lambda函数
# 列表生成式
result_apply = [x ** 2 for x in range(10)]
print(result_apply)


# 普通函数
def multiple(x):
    return x ** 2


multiple_apply = [multiple(x) for x in range(10)]
print(multiple_apply)

# lambda表达式
expression = [(lambda x: x ** 2)(x) for x in range(10)]
print(expression)


# 结合sort()函数 list.sort(key=None, reverse=False)
# 使用函数自身特性排序
list_value = [1, 3, 5, 64, 35, 643]
# 从小到大排序
list_value.sort()
print(list_value)
# 从大到小排序(reverse=True)
list_value.sort(reverse=True)
print(list_value)

list_value2 = [(5, 6), (7, 3), (1, 8)]
# 默认使用元组中的第一个元素来排序
list_value2.sort()
print(list_value2)
list_value2.sort(reverse=True)
print(list_value2)


# 使用key定义如何排序
# 使用函数来定义排序规则
def second_num(list_val):
    return list_val[1]


list_value2.sort(key=second_num)
print(list_value2)

list_value2.sort(key=second_num, reverse=True)
print(list_value2)

# 使用lambda函数定义排序规则
list_value2.sort(key=lambda x: x[1])
print(list_value2)
list_value2.sort(key=lambda x: x[1], reverse=True)
print(list_value2)


# 匿名函数的作用
# 简化代码、提高可读性


```



### 函数是一等公民

* 可以赋值
* 可以作为参数
* 可以嵌套
* 可以作为返回值

```python

# 函数是一等公民
# 可以赋值
def func(message):
    print(f'You got a message:{message}')


# 将函数赋值给其他变量
# 注意将函数对象赋值给其他变量的时候<!没有括号>,如果有括号则表示<!输出一个结果了>
send_message = func
# 赋值之后就可以在这个变量中为定义的函数传递参数
send_message('hello world')


# 可以作为参数
def get_message(message):
    return f'You got a message:{message}'


def call(fun, message):
    print(fun(message))


call(fun=get_message, message='hello,world')
call(get_message, 'hello,world')


# 可以嵌套
def fun_3(message):

    def get_message_3(message_3):
        print(f'You got a message:{message_3}')
    return get_message_3(message)


fun_3('hello world')


# 可以作为返回值
def func_4():

    def get_message_4(message):
        return f'You got a message:{message}'
    # 返回这个函数,而不是返回函数的值
    # get_message_4()这个函数作为一个值被返回出去了
    return get_message_4


# 调用func_4()这个函数得到的值就是一个返回值,即调用了send_message_4()这个函数
send_message_4 = func_4()           # send_message_4 = get_message_4
message_string = send_message_4('hello world')            # get_message()
print(message_string)

```



### 函数装饰器

#### 函数装饰器的基本使用

```python
# 函数装饰器
import time


# 定义一个普通函数,用于计算程序运行时间
def my_decorator(func):
    def wrapper():
        print('wrapper starting')
        start_time_wrapper = time.perf_counter()
        func()
        end_time_wrapper = time.perf_counter()
        result_time_wrapper = end_time_wrapper - start_time_wrapper
        print(f'wrapper running time:{result_time_wrapper}')
        print('wrapper end')
    return wrapper


# 使用函数装饰
@my_decorator
def for_loop():
    print('for_loop starting')
    for i in range(100000):
        pass
    print('for_loop end')


# 使用函数装饰器
@my_decorator
def while_loop():
    print('while_loop starting')
    i = 0
    while i < 100000:
        i += 1
    print('while_loop end')

# 使用普通方法计算程序运行时间 (time.perf_counter()函数加减得出)
# start_time = time.perf_counter()
# for_loop()
# end_time = time.perf_counter()
# result_time = end_time - start_time
# print(result_time)


# 普通方法调用函数计算程序运行时间
# new_for = my_decorator(for_loop)        # wrapper()
# new_for()
#
# new_while = my_decorator(while_loop)
# new_while()

# 使用了函数装饰器后,调用函数时直接包含了装饰器函数的功能
for_loop()
while_loop()

```

#### 带参数的函数装饰器

```python
import time

# 带参数的函数装饰器
def time_counter(func):
    def time_wrapper(number):
        print('wrapper function starting')
        func_start_time = time.perf_counter()
        func(number)
        func_end_time = time.perf_counter()
        result = func_end_time - func_start_time
        print(f'wrapper running time:{result}')
        print('wrapper function end')
    return time_wrapper


@time_counter
def for_loop_wrapper(number):
    print('for_loop_wrapper starting')
    for i in range(number):
        pass
    print('for_loop_wrapper end')


for_loop_wrapper(10000000)
```



#### 带有可变参数的函数装饰器

```python
import time
# 带有可变参数的函数装饰器
def time_counter(func):
    def time_wrapper(*args, **kwargs):
        print('wrapper function starting')
        func_start_time = time.perf_counter()
        func(*args, **kwargs)
        func_end_time = time.perf_counter()
        result = func_end_time - func_start_time
        print(f'wrapper running time:{result}')
        print('wrapper function end')
    return time_wrapper


@time_counter
def welcome(*args, **kwargs):
    name, gender = args
    # if gender == '男':
    #     gender = '先生'
    # else:
    #     gender = '女士'
    gender = '男士' if gender == '男' else '女士'
    print(f'hello,{name}{gender}, you are {kwargs["age"]} years old, your hobby is {kwargs["hobby"]}')


welcome('kelvin', '男', age='18', hobby='football'),
```



#### 使用functools.wraps( )函数来保存原函数的元信息

```python
import functools


def time_counter(func):
    # 使用functools.wraps()函数来保存原函数的元信息
    @functools.wraps(func)
    def time_wrapper(*args, **kwargs):
        print('wrapper function starting')
        func_start_time = time.perf_counter()
        func(*args, **kwargs)
        func_end_time = time.perf_counter()
        result = func_end_time - func_start_time
        print(f'wrapper running time:{result}')
        print('wrapper function end')
    return time_wrapper


@time_counter
def welcome(*args, **kwargs):
    name, gender = args
    gender = '男士' if gender == '男' else '女士'
    print(f'hello,{name}{gender}, you are {kwargs["age"]} years old, your hobby is {kwargs["hobby"]}')


welcome('kelvin', '男', age='18', hobby='football')

# 打印函数的元名称
print(welcome.__name__)

```



#### 函数装饰器的嵌套使用

* 程序在执行时，本质是先执行装饰器2，再执行装饰器1
* 即就近原则

```python
def decorator1(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('wrapper1 function execution')
        func(*args, **kwargs)
    return wrapper


def decorator2(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('wrapper2 function execution')
        func(*args, **kwargs)
    return wrapper


@decorator1
@decorator2
def welcome(message):
    print(message)


welcome('hello world')

```



## Chapter_9  面向对象编程（类的使用）

### 类的创建

### 语法结构

* 类的命名应使用大驼峰法

> class ThisIsName(object):
>
> pass

```python
# 类的创建
class Person(object):
    pass


class Animal(object):
    pass


# 将类实例化
kelvin = Person()
lucy = Person()

dog = Animal()
cat = Animal()

```



### 创建类的方法以及调用方法

```python
# 创建类
class Animal(object):
    def eat(self, food):
        print(f'eating{food} ')

    def play(self):
        print('playing')

    def sleep(self):
        print('sleeping')

# 将类实例化
dog = Animal()
# 调用类的方法
dog.eat('dog food')
dog.play()
dog.sleep()
```



### 将类实例化的多种方法以及self 的使用

```python
class Animal(object):
    def eat(self, food):
        print(f'eating {food} ')

    def play(self):
        print('playing')

    def sleep(self):
        # 在类中调用类的方法
        self.eat('some food')
        print('sleeping')


# 将类实例化
dog = Animal()
dog.eat('dog food')
dog.play()
dog.sleep()

# 可以使用类名直接调用（将类直接实例化）
# 但是这种方法需要主动传播self元素才能使用，不如使用将类赋值实例化的方法
# 因此并不提倡这种实例化方法
Animal()
Animal.eat(dog, 'dog milk')
Animal.sleep(dog)
Animal.play(dog)
```



### ____init___初始化方法的使用

```python
class Animal(object):
    def __init__(self, name, age, hobby, food):
        """
        __init__初始化方法，在实例化对象的时候，直接调用
        """
        self.name = name
        self.age = age
        self.hobby = hobby
        self.food = food

    def information(self):
        print(f"hello, my name is {self.name}, I am {self.age} years old, my hobby is {self.hobby}.")

    def eat(self):
        print(f'I like eat {self.food} ')

    def play(self):
        print(f'{self.name} is playing')

    def sleep(self):
        # 在类中调用类的方法
        self.eat()
        print(f'After eat {self.food}, I always go to sleep.')


# 将类实例化
dog = Animal('peppa', '3', 'stepping mud', 'bread')
dog.sleep()
```



### 类属性动态添加修改

```python
class Animal(object):
    # 定义一个类属性
    age = 6

    # 定义类方法
    def eat(self, food):
        print(f'eating {food} ')

    def play(self):
        print('playing')


# 将类实例化
dog = Animal()
dog.eat('dog food')
dog.play()
# 可以通过方法直接调用类属性
print(dog.age)

# 如果实例对象自身有该属性，会优先使用自身的属性
dog.age = 10
print(dog.age)

# 类属性自身可以直接调用
print(Animal.age)
# 同样的，类属性也可以全局动态修改
Animal.age = 15
print(Animal.age)

```



### 类的继承

```python
# 类的继承

class Animal(object):
    age = 10
    
    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f'{self.name} is eating.')

    def play(self):
        print(f'{self.name} is playing.')

    def sleep(self):
        print(f'{self.name} is sleeping')


class Pig(Animal):
    # 子类可以继承父类的实例属性
    def food(self):
        print(f'Pig {self.name} like pig food.')


class Dog(Animal):
    def food(self):
        print(f'Dog like dog food.')


# 调用子类必须添加父类要求的必要属性
dog = Dog('Labrador')
print(dog)
# 子类可以调用父类的实例方法
dog.eat()
print(dog.age)

```



### 方法的重写 

```python
# 方法的重写

class Animal(object):

    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f'{self.name} is eating.')

    def play(self):
        print(f'{self.name} is playing.')

    def sleep(self):
        print(f'{self.name} is sleeping')


class Pig(Animal):
    # 子类可以继承父类的实例属性
    def food(self):
        print(f'Pig {self.name} like pig food.')


class Dog(Animal):

    # 方法被子类重写时，会优先使用子类中的方法
    def eat(self):
        print(f"{self.name} don't like pig food.")

    def food(self):
        print(f'{self.name} like dog food.')


dog = Dog('Labrador')
dog.eat()
```



### 子类调用父类的初始化方法

```python
# 子类调用父类的初始化方法

class Animal(object):

    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f'{self.name} is eating.')

    def play(self):
        print(f'{self.name} is playing.')

    def sleep(self):
        print(f'{self.name} is sleeping')


class Pig(Animal):

    def __init__(self, name, gender):
        # 子类的初始化方法会覆盖父类的初始化方法
        # 如果要在子类中调用父类的初始化方法，需要调用super()方法进行声明
        # 需要接受什么参数，就调用什么参数
        super().__init__(name)
        self.gender = gender

    def food(self):
        print(f'Pig {self.name} like pig food.')


pig = Pig('pep', 'girl')
# 成功调用了父类的初始化方法
pig.food()

```



## Chapter_10  模块的导入

###  系统内置模块的导入

```python
import time
from os import listdir
from tkinter import *           # 实际开发中并不提倡这种导入方法，因为这样可能造成与其他模块重名而出现Bug

start = time.perf_counter()

# 使用form...import...导入的模块使用时可以不声明模块名
print(listdir())

time.sleep(1)
end = time.perf_counter()
print(end - start)
```

### 自定义模块的导入

```python
# 在同一目录下的自定义模块可以直接导入
import my_function
from my_function import subtraction
import sys      # 查找模块目录函数

# 导入不在同一目录下的自定义模块
import utils.function_branch

print(sys.path)

add = my_function.add(8, 9)
print(add)

subtraction = subtraction(10, 3)
print(subtraction)

# 但是在使用其他目录导入的函数的时候，也要用带目录的全名
multiplication = utils.function_branch.multiplication(8, 9)
print(multiplication)


# 也可以这样导入
# 如果该模块中的内容不是函数，则直接输出该模块中内容
from Chapter_1 import hello
```

### if_ _name_ _ = "_ _main_ _" 的意义

> 此方法的调用场景一般用于编写自定义模块，在自定义模块中，会定义很多类和方法，在实际开发过程中，需要不断的调试这些类和方法，将需要调试的内容放到<_ _if_ _name_ _="_ _ _main_ _">中，其他函数在调用该模块时就不会导入该部分的函数方法。

### 从包中导入模块

```python
# 从包（文件夹）中导入模块（自定义模块）
from package1 import module1
from package2 import module3

print(dir(module1))
print(module1.__name__)
print(module3.__package__)

```

### init.py 初始化文件的作用

#### 1. 从包中导入模块的时候，会自动调用init文件中的方法。

##### 使用init初始化文件前：

```python
# my_main.py
# 在未使init.py初始化文件前，需要依次导入模块才能使用


from package2.module3 import *
from package2.module4 import *

add()
subtraction()
multiplication()
division()

student = Student('kelvin')
student.get_student_name()

```

##### 使用初始化文件后：

在同级目录的init.py文件中：

```python
# 可在初始化文件中导入想要的模块
from package2.module3 import *
from package2.module4 import *
```

调用时：

```python
# 可以直接使用方法
from package2 import add, subtraction, multiplication, division, Student

add()
subtraction()
multiplication()
division()

student = Student('kelvin')
student.get_student_name()

```
#### __all__选择性导入

```python
print('this is package2 module3')

# 使用__all__声明只能调用那些方法
# 未被声明的方法将不能被调用
__all__ = ['add', 'subtraction', 'multiplication', 'division']


def add():
    print('this is add_function')


def subtraction():
    print('this is subtraction function')


def multiplication():
    print('this is multiplication')


def division():
    print('this is division')


def test():
    print('this is a test.')
```

##### 使用初始化文件做预处理



## Chapter_13 异常处理

### 使用 try...except 处理异常
```python
# 使用 try...except处理异常
# 程序正常，执行try范围内的程序
try:
    age = int(input('请输入年龄：'))
    if age >= 18:
        print('你已成年')
    else:
        print('你未成年')

# 如果出现异常，执行except语句内的程序
except ValueError as error:
    print('输入不合法')
    print(error)

print('程序结束')
```

### 使用 try...except...else处理异常
```python
# 使用 try...except...else处理异常
try:                                      # 判断条件
    age = int(input('请输入年龄：'))

# 如果程序异常，执行except语句内的操作
except ValueError as error:
    print('输入不合法')

# 如果程序正常，执行else语句内的操作
else:
    if age >= 18:
        print('你已成年')
    else:
        print('你未成年')

print('程序结束')
```

### 使用try...except...finally 处理异常
```python
# 使用try...except...finally 处理异常

try:
    file = open('text.txt', 'w')
    s = 'hello world2.'
    file.write(s)

except:
    print('操作异常')

# 无论是否发生异常，都要执行的操作
finally:
    file.close()
    print('关闭文件')
```

### 处理多个异常
```python
# 处理多个异常
try:
    # 异常1: 用户输入是否正确
    age = int(input('请输入年龄:'))

    # 异常2: 运算是否有错误（0不能为除数）
    x = 10 / age

# 可以把错误写到一起
except (ValueError, ZeroDivisionError):
    print('请输入整数')

# 也可以把错误分开写
# except ZeroDivisionError:
#     print('年龄不能为0')
    
else:
    print(f'年龄是：{age}')
    print(f'x is {x}')

```

### 使用raise主动抛出异常
```python
# 使用raise主动抛出异常
age = int(input('请输入年龄:'))


def is_adult(age):
    if age < 18:
        raise Exception("你还未成年")
    

try:
    is_adult(age)
except ValueError as va:
    print(va)

print('continue')
```

### 自定义异常类
```python
# 自定义异常类

class ValidateError(ValueError):
    def __init__(self, message, *args, **kwargs):
        super().__init__(message, *args, **kwargs)


def validate_accout(username, password):
    if username == '':
        raise ValidateError('用户名不能为空')
    if password == '':
        raise ValidateError('密码不能为空')
    if username != 'kelvin' or password != '123456':
        raise ValidateError('用户名和密码不匹配')


username = input('请输入用户名：')
password = input('请输入密码：')
try:
    validate_accout(username, password)
except ValueError as va:
    print(va)
else:
    print('用户名和密码正确')
```

### 异常处理小结：
1. 将异常捕获做到最精确，不要一昧的使用大类。
2. 先捕获小异常，再捕获大异常。
3. 尽量使用Python标准库中的异常
4. 不要滥用异常
5. 使用异常会造成新性能损耗





## chapter_14 文件的操作



### 打开文件概述



```python
open (file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)

# file: 必需，文件路径（相对或者绝对路径）
# mode: 文件打开模式
# buffering: 设置缓冲
# encoding: 一般使用utf-8
# errors: 报错级别
# newline: 区分换行符
# closed: 设置打开底层文件描述符
# opener: 通过传递可调用的opener可以使用自定义开启器
```



#### 打开文件模式

> 基础模式：
>
> > w (write)
> >
> > r (read)
> >
> > x (xor)
> >
> > a (apend)

> 扩展模式（需配合基础模式使用）：
>
> > b (bytes)
> >
> > +(plus)

```python
# 打开文件
# r模式：当文件不存在时报错
# w模式：当文件不存在时会自动创建一个文件，覆盖源文件内容
# x模式：如果文件不存在就创建，如果存在就报错
# a模式：如果源文件中有内容，会追加到原文件后面
# b模式：不能单独使用，以二进制形式展示
# +模式：增强模式
file = open('zen.txt', 'a')
# 操作文件
# file.write('hello world.')
file.write('this is a test.')
# 关闭文件
file.close()
```



#### 操作文件指针的2种方法

```python
fileObject.tell()		# 获取文件指针当前位置
# 参数：无
# 返回值：文件指针当前位置
```

```python
fileObject.seek(offset[, whence])		# 用于移动文件读取指针到指定位置
# 参数
# - offset: 开始的偏移量，也就是代表需要移动偏移的字节数。
# - whecce: 可选，默认值为0.给offset一个定义，表示要从哪个位置开始偏移；
#     	    0代表文件开头开始算起，1代表从当前位置开始算起，2代表从文件末尾算起。
# 返回值
# 如果操作成功，则返回新的文件位置，如果操作失败，则函数返回-1.
```

```python
file = open('zen.txt', 'w+')

print(file.tell())
file.write('hello world.')
file.seek(6, 0)
print(file.tell())
content = file.read()
print(content)

file.close()
```



#### 写入文件的两种方法

> .write()		写入字符串
>
> .writelines()		写入字符串序列

```python
# 打开文件
file = open('test.txt', 'w', encoding='utf-8')

# 写入文件
# 写入字符串(write)
# file.write('hello \nworld')

# 写入字符串序列(writelines)
seq = ['人生苦短', '我用Python', 'hello', 'world']
file.writelines('\n'.join(seq))

# 关闭文件
file.close()
```



#### 读取文件的三种方法

> read()	读取全部，返回字符串
>
> readline()	读取一行，返回字符串
>
> readlines()	读取一行，返回列表

```python
# 打开文件
file = open('test.txt', 'r', encoding='utf-8')

# 操作文件
# read()方法
content = file.read()
print(content)


# readline()方法
# 一般不会使用这种方法：
line = file.readline()
print(line)             # hello\n
line = file.readline()
print(line)
line = file.readline()
print(line)
line = file.readline()
print(f'结束：{line}')

# 使用while语句依次读取：
line = file.readline()
while line != '':
    print(line, end='')
    line = file.readline()


# readlines()方法
# 返回列表
lines = file.readlines()
print(lines)

for line in lines:
    print(line, end='')

# 关闭文件
file.close()

```



#### 关闭文件

>  ❗️ 课程回顾：揭秘with语句



#### 查看目录或文件

```python
# 查看目录和文件
print(os.getcwd())     # 查看当前目录
print(os.stat('handle_directory.py'))       # 获取指定路径的信息（文件或目录）
print(os.path.abspath('zen.txt'))       # 获取当前路径的绝对路径
print(os.path.getsize('zen.txt'))       # 获取文件大小（单位：字节）
print(os.path.getctime('zen.txt'))      # 获取文件创建时间
print(os.path.getatime('zen.txt'))      # 获取文件访问时间
print(os.path.getmtime('zen.txt'))      # 获取文件修改时间
```



#### 创建目录或文件

```python
# 创建目录和文件
os.mkdir('test1')       # 目录如果存在再次创建会报错
os.mkdir('test1/test2')       # 在已经存在的目录下递归创建目录
os.makedirs('python1/python2')      # 在不存在目录的情况下递归创建目录,同样的，目录如果存在再次创建会报错
使用open()函数创建文件
with open('test.py', 'w') as f:
    pass
判断目录或文件是否存在
if os.path.exists('test1/test2'):
    print('文件已存在')
else:
    os.makedirs('test1/test2')
```



#### 删除目录或文件

```python
# 删除目录或文件
os.rmdir('python1/python2')       #只能删除空文件夹
os.removedirs('test1/test2')        # 可以递归删除，只能删除空文件夹，如果上级文件夹下有文件，则无法删除
os.remove('python1/test1.py')       # 如果文件不存在则会报错
```



#### 修改目录或文件（名字/权限）

```python
# 修改目录或文件（名字/权限）
os.mkdir('log.txt', mode=0o755)
print(oct(os.stat('log.txt').st_mode))
print(os.access('log.txt', os.R_OK))
os.chmod('log.txt', 0o777)      # stat.S_I  更改权限
print(os.stat('log.txt'))
os.chown('log.txt', uid=2000, gid=3000)     # 更改用户组,根据实际情况填写
os.rename('log.txt', 'log')         # 修改名称
os.rename('log', 'python1/log')       # 修改名称的同时可以更改名字
print(os.getcwd())
os.chdir('python1/log')         # 修改目录
print(os.getcwd())

```



#### 判断是文件还是目录

```python
# 判断是目录还是文件
print(os.path.isfile('python1/python2/test2.py'))
print(os.path.isdir('python1/python2/test2.py'))

if os.path.isfile('python1/python2/test2.py'):
    os.remove('python1/python2/test2.py')
elif os.path.isdir('python1/python2/test2.py'):
    os.rmdir('python1/python2/test2.py')
else:
    print('既不是文件也不是目录')
```



#### 合并和分割目录

```python
# 合并和分割目录
path = os.getcwd()      # 获取当前目录
filename = 'log.txt'
# file_path = '\\'.join([path, filename])     # 字符串合并方式
file_path = os.path.join(path, filename)        # os目录合并方式
print(file_path)

# 拆分目录
print(os.path.split(file_path))         # 获取文件名及其目录
print(os.path.splitext(file_path))      # 获取文件的后缀
```



#### 遍历子目录

```python
# 遍历子目录
path = os.getcwd()
# 遍历当前目录的一级内容
print(os.listdir(path))

# 分层从根目录遍历所有层级内容
walk_obj = os.walk(path)
for num, item in enumerate(walk_obj):
    print(f'第{num + 1}层：{item}')
```





## chapter 15 MySQL 操作

### connection 连接对象

#### connection 对象方法

> cursor()				获取游标对象，操作数据库
>
> commit()			  提交事务
>
> rollback()           回滚事务
>
> close()				  关闭数据库连接

### Python 操作数据库基本流程

```python
import pymysql

try:
    connect = pymysql.connect(
        host='localhost',
        user='root',
        password='*********',
        db='shop',
        charset='utf8'
    )
except Exception as e:
    print(e)

try:
    # 获取游标对象
    with connect.cursor() as cursor:
        # SQL语句
        sql = """
        create table test(
        id int auto_increment primary key,
        name varchar(255) not null
        );
        """
        # 执行SQL语句
        cursor.execute(sql)
        # 提交操作
        connect.commit()
        # 获取数据
        # result = cursor.fetchone()
        # print(result)

except Exception as e:
    print(e)

finally:
    # 关闭数据库连接
    connect.close()


```

### Python 操作MySQL -- 增改删

```python
import pymysql

try:
    connect = pymysql.connect(
        host='localhost',
        user='root',
        password='WGX9.mysql',
        db='shop',
        charset='utf8'
    )
except Exception as e:
    print(e)

try:
    # 如果要批量操作 a
    # data = [(0, '小米11', '3800', '小米手机', 1, '2021-01-30'),
    #         (0, 'OPPO', '4800', '欧珀手机', 1, '2021-02-15'),
    #         (0, 'VIVO', '2800', '维蜗手机', 1, '2021-03-30')]
    # 获取游标对象
    with connect.cursor() as cursor:
        # SQL语句
        # sql_update = 'update goods set description = "维沃手机" where id = 14'
        sql_delete = 'delete from goods where id = 8'

        # 如果要批量操作 b
        # sql_create = """
        # insert into goods values(%s, %s, %s, %s, %s, %s)
        # """

        # 执行SQL语句
        # cursor.execute(sql_update)
        cursor.execute(sql_delete)

        # 如果要批量操作 c
        # cursor.executemany(sql_create, data)

        # 提交操作
        connect.commit()

except Exception as e:
    print(e)

finally:
    # 关闭数据库连接
    connect.close()

```

### Python 操作My3SQL -- 查询

```python
import pymysql

try:
    connect = pymysql.connect(
        host='localhost',
        user='root',
        password='WGX9.mysql',
        db='shop',
        charset='utf8',
        cursorclass=pymysql.cursors.DictCursor          # 设置为字典游标
    )
except Exception as e:
    print(e)

try:
    # 获取游标对象
    with connect.cursor() as cursor:
        # SQL语句
        # 设置筛选条件
        sql_select = 'select * from goods where price > 4000'
        # 不设置筛选条件
        # sql_select = 'select * from goods'

        # 执行SQL语句
        cursor.execute(sql_select)

        # 查找数据
        # 只获取一条数据
        # result = cursor.fetchone()
        # 获取多条数据
        # result = cursor.fetchmany(3)
        # 获取所有数据
        result = cursor.fetchall()


except Exception as e:
    print(e)

finally:
    # 关闭数据库连接
    connect.close()

print(result)
# 只打印一条数据
# print(f'商品名称：{result["name"]}， 价格：{result["price"]}')

# 打印多条数据
for goods in result:
    print(f'商品名称：{goods["name"]}， 价格：{goods["price"]}')

```



## chapter_16 网络爬虫基础

### requests 模块

#### requests 模块请求方法

| 方法    | 描述                                                        |
| ------- | ----------------------------------------------------------- |
| GET     | 请求页面，并返回页面内容                                    |
| HEAD    | 类似get请求，只不过返回的响应中没有具体的内容，用于获取报头 |
| POST    | 大多用于提交表单或上传文件，数据包含在请求中                |
| PUT     | 从客户端向服务器传送的数据取代指定文档中的内容              |
| DELETE  | 请求服务器删除指定的页面                                    |
| CONNECT | 把服务器当作跳板，让服务器代替客户端访问其他网页            |
| OPTIONS | 允许客户端查看服务器的性能                                  |
| TRACE   | 回显服务器受到的请求，主要用于测试或诊断                    |

```python
import requests

url = 'https://httpbin.org/get'
response = requests.get(url)
print(response)

```

#### 模块请求参数

```python
import requests

url = 'https://httpbin.org/post'
username = input('username:')
password = input('password:')
age = input('age:')
payload = {
    'username': username,
    'password': password,
    'age': age
}

# get请求带参数
# response = requests.get(url, params=payload)

# post请求带参数,数据不会被显示在网址中
response = requests.post(url, data=payload)
print(response)
print(response.url)

```



#### 添加请求头

```python
# 添加请求头
headers = {
'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36'
}
response = requests.get(url, headers=headers)
print(response)
print(response.url)

```

#### 伪造请求头

```python
# 伪造请求头
ua = UserAgent(verify_ssl=False)
user_agent = ua.random
headers = {
    'User-Agent': user_agent
}
response = requests.get(url, headers=headers)
print(response)
print(response.url)

```

### BeautifulSoup4 模块基础

#### 常用解析器

| 解析器          | 使用方法                             | 优势                                                         | 劣势                       |
| --------------- | ------------------------------------ | ------------------------------------------------------------ | -------------------------- |
| Python标准库    | BeautifulSoup(markup, "html.parser") | Python内置标准库  <br />速度适中  <br />文档容错能力强       | 老旧版本中文档容错能力差   |
| lxml HTML解析器 | "lxml"                               | 速度快<br />文档容错能力强                                   | 需安装C语言库              |
| lxml XML 解析器 | "xml"                                | 速度快<br />唯一支持XML的解析器                              | 需安装C语言库              |
| html5lib        | "html5lib"                           | 最好的容错性<br />以浏览器的方式解析文档<br />生成HTML格式的文档 | 速度慢<br />不依赖外部扩展 |

#### 四大对象

```python
from bs4 import BeautifulSoup
import requests
import lxml

url = 'http://8.135.6.248/'
try:
    response = requests.get(url)
except RuntimeError:
    print('请求失败')


html_content = response.text

# BeautifulSoup类型  获取整个html文档
soup = BeautifulSoup(html_content, 'xml')
print(type(soup))

# Tag类型  获取html标签
print(soup.title)
print(type(soup.title))

# NavigableString类型，获取标签内容
print(soup.title.string)
print(type(soup.title.string))

# 只能获取到匹配到的第一个标签
print(soup.a)
# 标签下还有嵌套标签的话无法获取字符串内容
print(soup.a.string)             # 返回None

# Comment类型 获取html中的注释
```

#### 常用操作

```python
# 获取页面em标签, 获取兄弟节点
print(soup.em)
# 获取文档原始内容（如空格等不显示的内容）
print(repr(soup.em.next_sibling))
print(soup.em.next_sibling.next_sibling)

# 获取em标签的父节点
print(soup.em.parent.parent.parent)
print(soup.em.parents)      # 返回生成器
for item in soup.em.parents:
    print(item)
    print()
```

> find语法
>
> find(name, attrs, recursive, string, **kwargs)
>
> > - name 参数可以查找所有名为name的tag，字符串对象会被自动忽略。
> > - attrs 搜索时会把该参数当作指定名字tag的属性来搜索
> > - recursive 检索当前tag的所有子孙节点
> > - string 搜索字符串

```python
# find方法
nav = soup.find('ul', {'class': 'top-nav-right'})
# print(nav)
for item in nav.children:
    # print(repr(item))
    if item != '\n':
        print(item.span.string)

# find_all方法
nav = soup.find_all('div', {'class': 'top-nav-items'})
for item in nav:
    if item.span:
        print(item.span.string)

# select方法
nav = soup.select('.top-nav-items .login-event')
for item in nav:
    print(item.span.string)

```

