# 文件读写与OS模块基础

## 文件读写

### 打开文件常用模式

```python
# 打开文件常用模式

# r模式，当文件不存在时会报错
file = open('zen.txt', 'r')

# w模式，文件不存在时自动创建文件,写入的内容会覆盖原文件内容
file_w = open('zen.txt', 'w')

# x模式,如果文件不存在则创建，如果文件存在则报错
file_x = open('zen.txt', 'x')

# a模式，如果原文件有内容，会将内容追加在原文件之后
file_a = open('zen.txt', 'a')

# b模式,不能单独使用，必须结合基础模式，读取和写入二进制文件
# wb，写入二进制文件
file_wb = open('zen_b.txt', 'wb')
file_wb.write(bytes('hello world', encoding='utf-8'))

# rb，读取二进制文件
file_rb = open('zen_b.txt', 'rb')
content = file_rb.read()
print(content)

# plus模式,增强模式
# 理论上可读可写，但是此模式受文件指针的影响，写入文件会默认从文件指针0开始写入，所以新内容会从开始覆盖源内容，新内容超过源内容则完全覆盖了源内容
file_rp = open('zen_b.txt', 'r+')
# 理论上可写可读,但该模式同样受文件指针的影响，其实是读取不到文件内容的
# 如果想要读取内容，可以使用seek()方法操作文件指针获取内容
file_wp = open('zen_b.txt', 'w+')
# 可追加写入也可读
file_ap = open('zen_b.txt', 'a+')

```



### 操作文件指针的常用方法

```python
# 操作文件指针的常用方法

file = open('zen.txt', 'w+')
# 显示文件指针位置
print(file.tell())
file.write('人生苦短，我用Python.')

# 将文件指针调到起始位置
file.seek(0, 0)

print(file.tell())
content = file.read()
print(content)

file.close()
```



### 写入文件的两种常用方法

```python
# 打开文件
file = open('test.txt', 'w')

# 写入文件
file.write('人生苦短，我用Python。')
# 如果要换行，可使用\n
file.write('人生苦短，\n我用Python。')

# 字符串序列可使用列表或元组
sep = ['人生苦短', '我用Python。']
# 默认紧密拼接字符，不会自动换行
file.writelines(sep)
# 如果想要实现自动换行的效果，可使用字符串join()方法
file.writelines('\n'.join(sep))

# 关闭文件
file.close()

```



### 打开文件的三种方法

```python
# 打开文件
file = open('test.txt', 'r')

# 操作文件
content = file.read()               # 读取所有内容
line = file.readline()              # 读取第一行

# 遍历所有行
for line in file:
    print(line, end='')

lines = file.readlines()            # 返回列表
# 遍历内容列表
for line in lines:
    # 可使用end为空去除空行
    print(line, end='')

# 关闭文件
file.close()

```



## OS 模块基础

### 查看目录和文件

```python
import os

# 查看目录和文件
# 查看当前目录
cwd = os.getcwd()
print(cwd)
# 获取指定路径信息(可以是文件或目录）
stat = os.stat('handle_directory.py')
print(stat)
abspath = os.path.abspath('test.txt')
# 获取文件的绝对路径
print(abspath)
# 获取文件大小
getsize = os.path.getsize('test.txt')
print(getsize)
# 获取文件创建时间(时间戳）
getctime = os.path.getctime('test.txt')
print(getctime)
# 访问时间
os.path.getatime('test.txt')
# 修改时间
os.path.getmtime('test.txt')

```



### 创建目录和文件

```python
# 创建目录
# mkdir()
# mkdir只能创建一个文件夹，不能递归创建，文件夹已存在则报错
os.mkdir('test1')
# test1 已经存在，在其下创建子文件夹不会报错
os.mkdir('test1/test2')
# python1 不存在，不能直接递归创建文件夹
os.mkdir('python1/python2')

# makedirs()
# 可以递归创建文件,如果文件夹已存在，同样会报错
os.makedirs('python1/python2')


# open()创建空文件
with open('test_file.txt', 'w') as file:
    pass


# 判断文件或文件夹是否存在
if os.path.exists('test1/test2'):
    print('File exists')
else:
    os.makedirs('test1/test2')
```



### 删除目录和文件

```python
# 删除目录和文件
# os.rmdir()
# 删除空目录,文件夹不为空则报错
os.rmdir('python1')
# 可以递归式删除，目标目录为空则可以成功删除
os.rmdir('test1/test2')

# os.removedirs()
# 递归删除空文件夹，不为空则报错，如果上层文件夹存在文件则无法删除
os.removedirs('test1/test2')

# os.remove()
# 删除文件，文件不存在则报错
os.remove('test_file.txt')

```



### 补充

> 一般删除文件时使用os库，然后利用os.remove(path)即可完成删除，如果删除空文件夹则可使用os.removedirs(path)即可，
> 但是如果需要删除整个文件夹，且文件夹非空时使用os.removedirs(path)就会报错了，此时可以使用shutil库，该库为python内置库，是一个对文件及文件夹高级操作的库，可以与os库互补完成一些操作，如文件夹的整体复制，移动文件夹，对文件重命名等。
>

```python
import os
import shutil

os.remove(path)   #删除文件
os.removedirs(path)   #删除空文件夹

shutil.rmtree(path)    #递归删除文件夹
```

### 修改目录和文件

```python
# 修改目录和文件
# 可以在创建目录时为其设置权限
os.mkdir('log.txt', mode=0o755)

# 使用函数命令更改权限
os.chmod('log.txt', 0o777)
print(os.stat('log.txt').st_mode)

# 更改用户组(根据实际情况填写）
# os.chown('log.txt', uid=, gid=)

# 重命名文件或文件夹
os.rename('test.txt', 'text_rename.txt')
os.rename('log.txt', 'log')
# 可以和移动文件同时执行
os.rename('test1.txt', 'log/tes1.txt')
os.rename('text_rename.txt', 'log/test.txt')

```

### 判断目录和文件

```python
# 判断目录和文件
is_file = os.path.isfile('./log/test.txt')
is_dir = os.path.isdir('./log/test.txt')
print(is_file)
print(is_dir)
if os.path.isfile('./log/test.txt'):
    os.remove('./log/test.txt')
else:
    print('这不是一个文件')

```



### 合并和分割目录

```python
# 合并和分割目录
path = os.getcwd()
file_name = 'log.txt'

# 字符串拼接方法
# file_path = '/'.join([path, file_name])
# 合并目录
file_path = os.path.join(path, file_name)

# 分割目录
# 获取文件绝对目录和文件名
print(os.path.split(file_path))
# 获取文件绝对目录、文件名、后缀
print(os.path.splitext(file_path))

```



### 遍历子目录

```python
# 遍历子目录
path = os.getcwd()
# print(os.listdir(path))
walk_obj = os.walk(path)
for num, item in enumerate(walk_obj):
    print(f'第{num+1}层:{item}')
    
```



## 补充

### 根据当前时间创建目录并将文件写入该目录当中

```python
from datetime import datetime
import os

# 获取当前时间并格式化时间
time_now = datetime.now().strftime('%Y-%m-%d_%H%M%S')
# 获取当前目录
root_path = os.getcwd()
# 将当前目录与目标目录拼接并添加目录路径分隔符
path = os.path.join(root_path, f'{time_now}{os.sep}')
os.mkdir(path)
with open(f'{path}' 'test.txt', 'w', encoding='utf-8') as file:
    file.write('hello world')

```

> 提示：创建文件夹时不能包含特殊字符，否则会出错。例如
>
> :  / 
