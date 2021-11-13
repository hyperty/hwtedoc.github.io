---
author: Joy Li
date: 2020-3-10
title: Python Introdution -Joy
---
# Python Introdution

# Python3.x 环境配置

* Python 官网安装： 

  <span style="color:#000000"> _https://www.python.org/downloads/mac-osx/_ </span>

* 利用Anaconda安装python： 

  <span style="color:#000000"> *https://www.anaconda.com/download/* </span>

* 利用Homebrew安装Python：
```shell
usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
**python3.x Installation Directories:**

`/Applications/Python 3.7`

`/Library/Frameworks/Python.framework`

`/usr/local/bin/`

**MAC 自带Python2.x  Installation Directories:** 

`/System/Library/Frameworks/Python.framework`

 `/usr/bin/python`



------

# How to debug

`print()`

`assert()` 

if fail, 会抛出AssertionError.

`logging`

适用于大型程序，包含critical, error, warning, info, debug, notset六个依次递减的级别，默认生成的root logger的level是logging\.warning, 低于该级别的就不输出了，输出默认格式：\{level\}:\{logger\}:\{message\}. 

`pdb.set_trace()`

break point, 放置在可能出错的地方，就可以设置一个断点,  用命令p查看变量，用命令c继续运行。

```python
import "pdb"

s = '0'
n = int(s)
pbd.set_trace()
print(10/n)
```
> 读懂报错信息，分析出错原因，需要经过一行行代码的磨练
```
Note   
ImportError: No module named ‘xxx’ 解决方案：
1)install xxx； 2)若程序名字和包的名字一样,则需修改名称； 3)sys.path.append() and etc.
```



------

# 异常处理 

使程序继续运行，如果你未对异常进行处理，程序将停止，并显示一个traceback，其中包含有关异常的报告。

`try-except`

处理可能发生的异常，显示自己编辑的错误信息，而不是令人迷惑的traceback。

```python
try:
    with open(filename) as f_obj:
        contents = f_obj.read()
expect FileNotFoundError:
    msg = "Sorry, the file " + filename + "doesn't exist."
    print(msg)
```

`Try-except-else`

 try语句放置可能引发异常的代码；else代码块放置try 代码块成功执行时才需要运行的代码。

```python
while True:
first_number = input("\nFirst number: ")
if first_number == 'q':break
second_number = input("\nSecond number: ")
try:
answer = int(first_number) / int(second_number)
expect ZeroDivisionError:
    print("you can't divide by zero!")
else:
    print(answer)
    
```



------

# Python 标识符命名规则

 * 第一个字符是以字符与下划线开始；

* 其他部分可以是数字，字母或下划线；

* 大小写敏感，建议单词首字母大写；

* 不能用keyword/BIFs 命名，keyword/BIFs 查找方式如下：

​      `Keyword.kwlist  `

​      `dir (__builtins__)`

> 用keyword/BIFs 命名后, 为了正常使用keyword/BIFs重新安装python是解决方法之一

```
Note
isidentifier()：判断字符串是否是有效的 Python 标识符
```



------

# Basic syntax

**operater**

>算术运算符

| 符号     | 作用  |
| -------- | ----- |
| + | 加法 |
|  -  |减法|
| * |乘法|
| / |除法|
| // |除法取整|
| % |取余|
| ** |幂次|

>赋值运算符

| 符号     | 作用  | 描述 |
| -------- | ----- |----- |
| = | 赋值       | a = b |
| += | 加后赋值 | a += b 等效于 a = a+b |
| -= | 减后赋值 | a -= b 等效于 a = a-b |
| *= | 乘后赋值 | a *= b 等效于 a = ab |
| /= | 除后赋值 | a /= b 等效于 a = a/b |
| //= | 整除后赋值 | a //= b 等效于 a = a//b |
| %= | 取余后赋值 | a %= b 等效于 a = a%b |
| **= | 次方后赋值 | a **= b 等效于 a = a的b次方 |

>位运算符

| 符号     | 作用  | 描述 |
| -------- | ----- |----- |
| & | 按位与运算 | 参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0 |
| \| | 按位或运算 | 只要对应的二个二进位有一个为1时，结果位就为1。 |
| ^ | 按位异或运算 | 当两对应的二进位相异时，结果为1。 |
| ~ | 按位取反运算 | 对数据的每个二进制位取反,即把1变为0,把0变为1 。 |
| << | 左移动运算 | 运算数的各二进位全部左移若干位，运算符右边的数字指定了移动的位数，高位丢弃，低位补0。 |
| >> | 右移动运算 | 把">>"左边的运算数的各二进位全部右移若干位，运算符右边的数字指定了移动的位数 |

>逻辑运算符

| 符号     | 作用  | 描述 |
| -------- | ----- |----- |
| and | 布尔"与" | x and y, 如果 x 为 False，x and y 返回 False，否则它返回 y 的计算值 |
| or | 布尔"或" | x or y, 布尔"或" - 如果 x 是非 0，它返回 x 的值，否则它返回 y 的计算值 |
| not | 布尔"非" | not x, 布尔"非" - 如果 x 为 True，返回 False 。 |

>成员运算符

| 符号     | 描述 |
| :------- | ----- |
| in | 如果在指定的序列中找到值返回 True，否则返回 False。 |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 |

>身份运算符

| 符号     | 描述 |
| :------- | ----- |
| is | 如果引用的是同一个对象则返回 True，否则返回 False |
| is not | 如果引用的不是同一个对象则返回结果 True，否则返回 False。 |

**循环**

for迭代循环

```python
for i in range(3):
    if i == 1: pass
    else: print(i, "time") 
```

while(死循环，条件循环) 

```python
 i = 0
 while True:
    i += 1
    if i == 2: continue
    print(i, "time")
    if i == 4: break
```

> 循环控制：

`break`, `continue`, `pass`
​    

> 条件判断： 

`if else`, 三元表达式

```python
#三元表达式
a = "abcdefg"
print("yes") if "abc" in a else print("no")
```



------

# 基本变数类型

**不可变类型: **Number, String

初始化成功后, 对应内存地址上的数据不发生任何变化。

**可变类型:** List, Tuple, Set, Dictionary

初始化成功后, 对应内存地址上的数据可以发生多次局部变化。



------

## Number


Number：int, float, complex.

基本操作：

1\. 数值类型间转换；

`bin()`, `oct()`, `hex()`

`int()`, `float()`, `complex()`

2\. 绝对值 `abs()`，四舍五入`round()`等



------

## String

基本操作：

1\. 字符串初始化及转义

2\. 字符串长度  `len()` 

3\. 访问（循环、索引和切片）
```python
# 切片区间左闭右开
a = 'joy\'s book'
[Send:] print(a[6:-1:1])
[Rec :] boo
```
4\. 格式化输出 `{}  `
```python
u = "http://{}.com"
c = "happy"
[Send:] u.format(c)
[Rec :] 'http://happy.com'
```
5\. 拼接 `+`, 重复`*`

6\. 查找 `find()` , 替换 `replace()`

7\. 编码 `encode()`, 解码`decode()`

8\. 其他操作 `dir()`



------

## List

**基本操作：**

1\. `+` 连接, `*`重复

2\. 访问（索引、切片）
```python
l1 = [1,2,3,4,5,6]
[Send:] l1[::-1]
[Rec :] [6, 5, 4, 3, 2, 1]
```
3\. 类型转换:

`list()`, `str()`, `tuple()`

4\. BIF:

`zip()` , `append()`, `extend()`, `insert()`,

`count()`, `pop()`, `remove()`, `sorted()`,

`enumerate()`, `max()`, `min()`, and etc

5\. 列表推导式
 ```python
 l1 = list(range(200))
 [x for x in l3 if x>190]
 ```
6\. `dir()`

查询其他操作



------

## Tuple

Tuple可认为是只读列表，除了对其修改\(不支持不可变类型赋值，支持可变类型赋值), 许多操作与list相似, 不再一一列举。
```python
t1 = (1,2,3)
t2 = (1,2,[66,88])
[Send:] print(t1+(4,))
[Rec :] (1, 2, 3, 4)
#对不可变类型赋值
[Send:] t1[0] = 66
[Rec :] Traceback (most recent call last):
          File "<stdin>", line 1, in <module>
        TypeError: 'tuple' object does not support item assignment
#对可变类型赋值
[Send:] print(t2[2][0])
[Rec :] 66
```



------

## Set

**集合 \(Set\):** 一组key\(只有key, 没有value\)的无序组合, 无法用索引及切片访问。

**基本操作：**

1\. 主要用于去重

```python
l1 = [66,1,88,88]
s1 = set(l1)

[Send:] print(set(l1))
[Rec :] {88, 1, 66}
```
2\. 集合间操作\(交集、并集和差集\)
```python
# 并集
s1 = {11,22}
s2 = {66,11}

[Send:] print(s1|s2)
[Rec :] {66, 11, 22}
```



------

## Dictionary

**Dictionary: ** 

key: value对应, 且Key值必须可被 `hash()` \(number, string, Tuple\)

**基本操作：**

1\. 初始化及成员判断

2\. 访问

```python
d1 = {'name': 'Jack', 'age':3}
d1['address']='Shanghai'

[Send:] d1['name']
[Rec :] 'Jack'
[Send:] d1.get('name', -1)
[Rec :] 'Jack'

[Send:] d1.keys()
[Rec :] dict_keys(['name', 'age', 'address'])
[Send:] d1.values()
[Rec :] dict_values(['Jack', 3, 'Shanghai'])
[Send:] d1.items()
[Rec :] dict_items([('name', 'Jack'), ('age', 3), ('address', 'Shanghai')])
```



------

# Function

**语法格式：**

```python
#def 函数名(参数):
#        ____函数体
def ooo(num):
    a = 0
    for i in range(num):
        a += i
    return(a)
```

**参数：**
positional_args, keyword_args, *tuple_nonkw_args, **dict_kw_args

positional_args: 位置顺序(一一对应)；不能多参少参
```python
def foo1(x,y):
	print(x,y)
    print(y,x)

[Send:] foo1("green","blue")
[Rec :] green blue
        blue green
[Send:] foo1("green")
[Rec :] Traceback (most recent call last):
          File "<stdin>", line 1, in <module>
        TypeError: foo1() missing 1 required positional argument: 'y'
```
keyword_args: 不能多参少参
```python
def foo2(x,y,intro="nice"):
    print(x,y)
    print(intro)

[Send:] foo2("green","blue")
[Rec :] green blue
        nice
[Send:] foo2("green","blue",intro="xxxxx")
[Rec :] green blue
        xxxxx
```
*tuple_nonkw_args: 不确定参数个数时使用, 调用时自动组装成一个tuple
```python
def mysum(*args):
    print(type(args))
    return sum(args)

[Send:] mysum(1,2,3,4,5,6)
[Rec :] <class 'tuple'>
        21
```
**dict_kw_args: 不确定参数个数时使用,调用时自动组装为一个字典    
```python
def foo3(**kwargs):
    print(type(kwargs))
    for key, values in kwargs.items():
    	print(key,":" ,values)

[Send:] foo3(film="羞羞的铁拳", box=7, price=60)
[Rec :] <class 'dict'>
        film : 羞羞的铁拳
        box : 7
        price : 60
```



------

# Python serial communication

**功能：**

1\. 打开串口并收发十六进制数据

2\. 执行”nanocom \-h \-d /dev/cu\.usbmodem141202” command

​                                                                                                                                                                  —详情请见附件

