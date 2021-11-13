---
title: Lua introduction
---
# Lua introduction

# 一、环境安装

## Mac OS X 系统上安装

1. 复制 http://www.lua.org/ftp/lua-5.3.0.tar.gz 到浏览器，“5.3.0”为版本号，可换成需要下载的版本号。

2. 解压上述压缩文件

3. cd 到解压完的路径		cd /Users/rally/Downloads/lua-5.3.0

4. 在terminal 下输入 make macosx test

5. 在terminal 下输入sudo make install

6. 目前切换版本的方式是通过重复上述3-5步



## Mac 通过homebrew 安装

brew install lua

# 二、基本语法

## 交互式编程

1. 在terminal下输入lua

2. 直接输入需要执行的lua命令



## 脚本式编程

```shell
lua /Users/rally/Desktop/Pyfolder/test.lua
```



## 注释

### **单行注释**

```lua
--
```

也可先选中需要注释的模块，再用快捷键command + /



### **多行注释**

```lua
--[[
 多行注释
 多行注释
 --]]
```

多行注释推荐使用 **--[=[注释内容]=]**，这样可以避免遇到table[table[idx]]时就将多行注释结束了。



## 标示符

Lua 标示符用于定义一个变量，函数获取其他用户定义的项。标示符以一个字母 A 到 Z 或 a 到 z 或下划线 _ 开头后加上0个或多个字母，下划线，数字（0到9）。



## 关键词

以下列出了 Lua 的保留关键字。保留关键字不能作为常量或变量或其他用户自定义标示符：

|          |       |       |        |
| -------- | ----- | ----- | ------ |
| and      | break | do    | else   |
| elseif   | end   | false | for    |
| function | if    | in    | local  |
| nil      | not   | or    | repeat |
| return   | then  | true  | until  |
| while    | goto  |       |        |

一般约定，以下划线开头连接一串大写字母的名字（比如 _VERSION）被保留用于 Lua 内部全局变量。



## 全局变量

在默认情况下，变量总是认为是全局的。

全局变量不需要声明，给一个变量赋值后即创建了这个全局变量，访问一个没有初始化的全局变量也不会出错，只不过得到的结果是：nil。

```lua
> print(b)
nil
> b=10
> print(b)
10
>
```

如果你想删除一个全局变量，只需要将变量赋值为nil。

```lua
b = nil
print(b)      --> nil
```

这样变量b就好像从没被使用过一样。换句话说, 当且仅当一个变量不等于nil时，这个变量即存在。



局部变量需要加local



# 三、数据类型

##  基本类型

| 数据类型 | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| nil      | 这个最简单，只有值nil属于该类，表示一个无效值（在条件表达式中相当于false）。 |
| boolean  | 包含两个值：false和true。                                    |
| number   | 表示双精度类型的实浮点数                                     |
| string   | 字符串由一对双引号或单引号来表示                             |
| function | 由 C 或 Lua 编写的函数                                       |
| userdata | 表示任意存储在变量中的C数据结构                              |
| thread   | 表示执行的独立线路，用于执行协同程序                         |
| table    | Lua 中的表（table）其实是一个"关联数组"（associative arrays），数组的索引可以是数字、字符串或表类型。在 Lua 里，table 的创建是通过"构造表达式"来完成，最简单构造表达式是{}，用来创建一个空表。 |



* **nil**

nil 作比较时应该加上双引号 **"**：

```lua
--并未定义X
> type(X)
nil

> X == nil
true

> type(X)==nil
false

> type(X)=="nil"
true

> print(type(X))
nil

> print(type(type(X)))
string
```

**type(X)==nil** 结果为 **false** 的原因是因为 **type(type(X))==string**。



* **boolean**

boolean 类型只有两个可选值：true（真） 和 false（假），Lua 把 false 和 nil 看作是 false，其他的都为 true，数字 0 也是 true。true={任意数字, true}, false={nil, false}

实例：

```lua
t={
    [1]=true,
    [2]=false,
    [3]=-1,
    [4]=nil,
    [5]=True,
    [6]=False,
}

for i =1,6,1 do
    y=t[i]
    if y then
        print("第"..i.."个值“"..tostring(t[i]).."”的布尔值为: ".."True")

    else
        print("第"..i.."个值“"..tostring(t[i]).."”的布尔值为: ".."False")
    end
end

output：
第1个值“true”的布尔值为: True
第2个值“false”的布尔值为: False
第3个值“-1”的布尔值为: True
第4个值“nil”的布尔值为: False
第5个值“nil”的布尔值为: False
第6个值“nil”的布尔值为: False
```



* **number**

Lua 默认只有一种 number 类型 -- double（双精度）类型（默认类型可以修改 luaconf.h 里的定义），以下几种写法都被看作是 number 类型：

```lua
print(type(2))
print(type(2.2))
print(type(0.2))
print(type(2e+1))
print(type(0.2e-1))
print(type(7.8263692594256e-06))

output:
number
number
number
number
number
number
```

虽然小数也属于number类型，但是不能直接用%d进行捕获，在后续string.find()方法中会提及到小数的捕获方法。

* **tonumber()**

把非数字的原始值转换成数字，示例：

```lua
local num = tonumber("10");    -- 返回十进制数10
local num = tonumber("AF",16); -- 返回十六进制数175
local num = tonumber("0xA");   -- 返回10
local num = tonumber("56.9");  -- 返回56.9
local num = tonumber("0102");  -- 返回102
local num = tonumber("123456red");     -- 返回nil
local num = tonumber("red");           -- 返回nil
local num = tonumber("true");          -- 返回nil
local num = tonumber({x  =10, y = 20});-- 返回nil

```



* **string**

字符串由一对双引号或单引号来表示。

```lua
string1 = "this is string1"
string2 = 'this is string2'
```

 也可以用 2 个方括号 "[[]]" 来表示"一块"字符串。

```lua
string = [[
aaa
]]
print(string)

output:
aaa

```

转义字符可用\

```lua
print('\"aa\"\'')

output:
"a"'
```

在对一个数字字符串上进行算术操作时，Lua 会尝试将这个数字字符串转成一个数字：

```lua
> print("2" + 6)
8.0
> print("2" + "6")
8.0
> print("2 + 6")
2 + 6
> print("-2e2" * "6")
-1200.0
```



字符串连接使用的是 .. ，如：

```lua
> print("a" .. 'b')
ab
> print(157 .. 428)
157428
>
```



使用 # 来计算字符串的长度，放在字符串前面，如下实例：

```lua
> str1 = "apple and pear"
> print(#str1)
14
> print(#"apple and pear")
14
>
```

也可以用string.len(str)方法来计算字符串的长度，如下实例：

```lua
>a="abc"
>print(string.len(a))
3
```



文件编码格式是UTF-8，所以一个中文是3个字节，

想了解更多关于Lua中含中文字符串长度计算可点击下方链接：

https://blog.csdn.net/folliker/article/details/74178993?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param

实例：

```lua
str1=[[我我w]]
str2=[[123456w]]
str3=[[我，我]]
print(#str1)
>7
print(#str2)
>7
print(#str3)
>9
```



* **table**

在 Lua 里，table 的创建是通过"构造表达式"来完成，最简单构造表达式是{}，用来创建一个空表。也可以在表里添加一些数据，直接初始化表:

```lua
-- 创建一个空的 table
local tbl1 = {}

-- 直接初始表
local tbl2 = {"apple", "pear", "orange", "grape"}
```



Lua 中的表（table）其实是一个"关联数组"（associative arrays），数组的索引可以是数字或者是字符串。

```lua
a={}
a={['k3']='v4',['k3']='v3','v1','v2',}
a[1]='v5'

for k,v in pairs(a) do
    print(k..":"..v)
end

output:
1:v5
2:v2
k3:v3
```



1.索引为'k3'的值会被后面定义的值所覆盖掉：['k3']='v4'  --->  ['k3']='v3'

2.无索引的值，默认从1开始：a[1]='v1',a[2]='v2'，并且想重新赋值索引为数字的值，只能通过a[number]='value' 这种方式来赋值

3.存在无索引值的值时，优先给无索引的值赋予索引（1～∞），并且不得在表中重新定义该索引的值，如下实例：

```lua
b={
    "v1",
    [2]="v2",
    [3]="v3",
    [4]="v4",
    [1]="v5",
  	[2]="v6",
}

for k,v in pairs(b) do
    print(k..":"..v)
end

output:
1:v1
2:v6
3:v3
4:v4
```



4.默认的输出顺序是：先数字索引由小到大(**发现当数字索引最大值为2的n次方时，最后一项索引会优先输出，然后再按大到小输出**)，再按随机顺序输出字符串索引。



```lua
--索引最大值为8:
b={
    [1]="v1",
    [2]="v2",
    [3]="v3",
    [4]="v4",
    [5]="v5",
    [6]="v6",
    [7]="v7",
    [8]="v8",
    -- [9]="v9",
    -- [10]="v10",
    -- [11]="v11",
    -- [12]="v12",
    -- [13]="v13",
    -- [14]="v14",
    -- [15]="v15",
    -- [16]="v16",
}

for k,v in pairs(b) do
    print(k..":"..v)
end

output:
8:v8
1:v1
2:v2
3:v3
4:v4
5:v5
6:v6
7:v7
```

```lua
--索引最大值为9:
b={
    [1]="v1",
    [2]="v2",
    [3]="v3",
    [4]="v4",
    [5]="v5",
    [6]="v6",
    [7]="v7",
    [8]="v8",
    [9]="v9",
    -- [10]="v10",
    -- [11]="v11",
    -- [12]="v12",
    -- [13]="v13",
    -- [14]="v14",
    -- [15]="v15",
    -- [16]="v16",
}

for k,v in pairs(b) do
    print(k..":"..v)
end

output:
1:v1
2:v2
3:v3
4:v4
5:v5
6:v6
7:v7
8:v8
9:v9
```

```lua
--索引最大值为10:
b={
    [1]="v1",
    [2]="v2",
    [3]="v3",
    [4]="v4",
    [5]="v5",
    [6]="v6",
    [7]="v7",
    [8]="v8",
    [9]="v9",
    [10]="v10",
    -- [11]="v11",
    -- [12]="v12",
    -- [13]="v13",
    -- [14]="v14",
    -- [15]="v15",
    -- [16]="v16",
}

for k,v in pairs(b) do
    print(k..":"..v)
end

output:
1:v1
2:v2
3:v3
4:v4
5:v5
6:v6
7:v7
8:v8
9:v9
10:v10
```



* **function**

在 Lua 中，函数是被看作是"第一类值（First-Class Value）"，函数可以存在变量里:

```lua
function factorial1(n)
    if n == 0 then
        return 1
    else
        return n * factorial1(n - 1)
    end
end
print(factorial1(5))
factorial2 = factorial1
print(factorial2(5))

output:
120
120
```



function 可以以匿名函数（anonymous function）的方式通过参数传递:

```lua
function testFun(tab,fun)
        for k ,v in pairs(tab) do
                print(fun(k,v));
        end
end


tab={key1="val1",key2="val2"};
testFun(tab,
function(key,val)--匿名函数
        return key.."="..val;
end
);

output:
key1=val1
key2=val2
```



* **thread**

在 Lua 里，最主要的线程是协同程序（coroutine）。它跟线程（thread）差不多，拥有自己独立的栈、局部变量和指令指针，可以跟其他协同程序共享全局变量和其他大部分东西。

线程跟协程的区别：线程可以同时多个运行，而协程任意时刻只能运行一个，并且处于运行状态的协程只有被挂起（suspend）时才会暂停。



* **userdata**

userdata 是一种用户自定义数据，用于表示一种由应用程序或 C/C++ 语言库所创建的类型，可以将任意 C/C++ 的任意数据类型的数据（通常是 struct 和 指针）存储到 Lua 变量中调用。



# 四、字符串

## Lua的字符串模式匹配

**string中功能较为强大的函数：**

* string.find（字符串查找）
* string.gsub（全局字符串替换）
* string.gfind（全局字符串查找）
* string.gmatch(返回查找到字符串的迭代器)

这些函数都是基于模式匹配的。与其他脚本语言不同的是，Lua并不使用POSIX规范的正则表达式（也写作regexp）来进行模式匹配。主要的原因出于程序大小方面的考虑：实现一个典型的符合POSIX标准的RegExp大概需要4000行代码，这比整个Lua标准库加在一起都大。权衡之下，Lua中的模式匹配的实现只用了500行代码，当然这意味着不可能实现POSIX所规范的所有更能。然而，Lua中的模式匹配功能是很强大的，并且包含了一些使用标准POSIX模式匹配不容易实现的功能。

你还可以在模式串中使用字符类。字符类指可以匹配一个特定字符集合内任何字符的模式项。比如，字符类%d匹配任意数字。所以你可以使用模式串'%d%d/%d%d/%d%d%d%d'搜索dd/mm/yyyy格式的日期：

```lua
s = "Deadline is 30/05/1999, firm"
date = "%d%d/%d%d/%d%d%d%d"
print(string.sub(s, string.find(s, date)))

output:
30/05/1999
```

**Lua 支持的字符类有：**

> . 任意字符  
 %s 空白符  
 %p 标点  
 %c 控制字符  
 %d 数字  
 %x 十六进制数  
 %z 代表0的字符  
 %a 字母  
 %l 小写字母  
 %u 大写字母  
 %w 字母数字  
字符类的大写形式代表相应集合的补集， 比如 %A 表示除了字母以外的字符集
另外，* + - ?四个，作为通配符分别表示：

>*： 匹配前面指定的 0 或多个同类字符， 尽可能匹配更长的符合条件的字串  
+： 匹配前面指定的 1 或多个同类字符， 尽可能匹配更长的符合条件的字串  
-： 匹配前面指定的 0 或多个同类字符， 尽可能匹配更短的符合条件的字串  
?: 	它与该类中字符的零次或一次匹配。如果可能，它总是匹配一次  

**由于Lua中的正则没有指定{x,y}次数的匹配方式，从网上找到了自定义匹配次数的方法**

网址：http://blog.sina.com.cn/s/blog_6bcf42010102wvbz.html

```lua
local function n_gmatch(str,regex)
    local rs
    local match_str_all = '' -- 累计匹配到的字符串
    if type(str) == 'string' and str ~= '' and type(regex) == 'string' and regex ~= '' then
       local _start,_end,reg_pre,min_num,comma,max_num,reg_end = string.find(regex, '^([^%{%}]+)%{(%d*)(,?)(%d*)%}([^%{%}]*)$')
       if _start and _end then
           -- 正则包含{}
           if min_num == '' and max_num == '' then
               -- {}内容为空
               -- print('{}内容为空')
           else
               if comma == '' then
                   -- {n} 格式
                   max_num = min_num
               end
               min_num = tonumber(min_num) or 0
               max_num = tonumber(max_num) or 99999999

               if min_num <= max_num then

                   -- print('前置正则:'..reg_pre,'后置正则:'..reg_end,'最小次数:'..min_num,'最大次数:'..max_num)

                   local start_est,end_est = false,false --是否是从最开始或最结尾匹配
                   if string.sub(reg_pre,1,1) == '^' then
                       start_est = true
                       reg_pre = string.sub(reg_pre,2)
                   end

                   local match_num = 0
                   for match in string.gmatch(str, reg_pre) do
                       match_num = match_num + 1
                       match_str_all = match_str_all..match
                       -- print('match_str_all:'..match_str_all)
                       -- 判断是否是连续匹配
                       local _start,_end = string.find(str,match_str_all,1,false)
                       if not _start or not _end then
                           -- print('非连续匹配')
                           match_num = 0
                           break
                       elseif match_num == 1 and start_est then
                           -- 正则中包含^ 判断第一次匹配到的字符串是否在str的开头
                           if _start ~= 1 then
                               -- print('第1次匹配内容:'..match..'不在str开头,结束匹配')
                               match_num = 0
                               break
                           end
                       end

                       if max_num and match_num >= max_num then
                           -- print('匹配次数到达上限'..max_num..',结束{...}前字符匹配')
                           break
                       end
                   end

                   if match_num < min_num then
                       -- print('匹配次数小于最小匹配次数'..min_num)
                   else
                       local str_remain = ''
                       if match_str_all == '' then
                           str_remain = str
                       else
                           local _start,_end = string.find(str,match_str_all,1,false)
                           str_remain = string.sub(str,_end+1)
                       end

                       -- print('str已匹配:'..match_str_all,'str剩余:'..str_remain,'reg剩余:'..reg_end)

                       if reg_end == '' then
                           rs = match_str_all
                       else
                           -- 拿剩余字符和{}后面的正则匹配
                           local _start,_end =string.find(str_remain,'^'..reg_end)
                           if _start and _end then
                               local str_match = string.sub(str_remain,_start,_end)
                               match_str_all = match_str_all..str_match
                               rs = match_str_all
                           end
                       end
                   end
               else
                   -- print('最大值小于最小值')
               end
           end
       else
           -- 沿用普通正则 find
           -- print('正则不符合...{}...格式，沿用普通正则匹配')
           local _start,_end = string.find(str,regex)
           if _start and _end then
               match_str_all = string.sub(str,_start,_end)
               rs = match_str_all
           end
       end
    else
       -- str或regex格式不正确
       -- print('str或regex格式不正确')
    end
    return rs
end

local str = "aaaaa123,456,10,5"
print(n_gmatch(str,'^(%d+,){1,3}%w+$')) -- nil
print(n_gmatch(str,'(%d+,){1,3}%w+$')) -- 123,456,10,5
print(n_gmatch(str,'%d+,')) -- 123,
```

**关于控制字符：**

红色字体的为控制字符

![](LuaScript/NULSOH.jpeg)



## 字符串的常用处理方法

**`string.find( s,pattern[, init][, plain] )`**

```lua
string.find(s,pattern[, init][, plain] ) ==  s:find(pattern[, init][, plain] )
```

s: 源字符串
pattern: 待搜索模式串
init: 可选， 起始位置，默认为1
plain: 分为true 和 false，默认为false，true时返回的值为nil



1. 子串匹配：

```lua
s="Become a pig"
a,b=string.find(s,"%a+")
print(a) ----输出1
print(b) ----输出6
```

 **注意： lua 里面数组或者字符串的字符， 其下标索引是从 1 开始， 不是 0** string.find 默认情况下返回两个值， 即查找到的子串的起止下标， 如果不存在匹配返回 nil。
 如果我们只想要 string.find 返回的第二个值， 可以使用 **虚变量**（即 下划线）

```lua
s="Become a pig"
_,b=string.find(s,"%a+")
-- print(a)
print(b)


----输出6
```



2. 模式匹配：

```lua
pair = " Bean = Rainbow horse "
--print(string.find(pair, "(%a+)%s*=%s*(%a+)%s*(%a+)"))
a,b,c,d,e=string.find(pair, "(%a+)%s*=%s*(%a+)%s*(%a+)")

print("StartIndex:  "..a)
print("EndIndex:  "..b)
print(c.." is "..d.." "..e)


--输出:
--StartIndex:  2
--EndIndex:  21
--Bean is Rainbow horse
```

**解释：**
 如果 find 的第二个参数使用了某种匹配模式， 并且模式串里面带括号。 那么表示会“捕捉”括号括起来的模式匹配到的字符串。 捕捉， 当然会把他们作为返回值。这里捕捉了三下， 所以 find 多返回了三个值



```lua
s=[[Bean "it's a Rainbow fart"]]
--  s="Bean \"it's a Rainbow fart\""
pattern1 = [[(%a+)(%s)([\"'])(%C+)([\"'])]]
pattern2 = [[%a+%s([\"'])(%C+)(%1)]]
--[\"']代表匹配"或者'，加上()表示捕获，%C代表匹配控制字符(例如\n)的补集，最后的(%1)表示捕获与第一次捕获内容相同的内容，即"
_,_,a,b,c,d,e=string.find(s,pattern1)
print(a)					--Bean
print(b)					--
print(c)          --"
print(d)					--it's a Rainbow fart
print(e)					--"
_,_,p,q,t=string.find(s,pattern2)
print(p)					--"
print(q)					--it's a Rainbow fart
print(t)					--"
```



还有， '-' 与 '*' 到底有什么不同呢？ 在上面， "([\"'])(.*)%1" 匹配到的结果与 '-' 是一样的。尽可能匹配更长， 尽可能匹配更短 究竟什么不同呢？看例子：

```lua
print( ("\"hello\"\"hello\""):find('"(.+)"') )  ----输出 1 14 hello""hello
print( ("\"hello\"\"hello\""):find('"(.-)"') )  ----输出 1 7 hello
```

\* 尽可能长， 所以匹配了首尾两个 引号， 捕获了中间的 (hello""hello)
\- 尽可能短， 所以碰到第二个引号就说匹配完了， 因此只捕获了第一个 (hello)

匹配的时候是根据双引号来匹配字符，可以看出 - 就是遇到第一个字符串就停止了，而*就是尽可能的捕获更多的字符串。



%d只能匹配到整数位，匹配小数的实例如下：

```lua
s = -1.55
print(string.find(s, "^([+-]?%d+%p%d+)$"))

output:
1       5       -1.55
```



* **`string.gmatch (s, pattern [, init])`**

```lua
string.gmatch(s,pattern [, init]) ==  s:gmatch(pattern [, init])
```

回一个迭代器函数，每一次调用这个函数，返回一个在字符串 str 找到的下一个符合 pattern 描述的子串。如果参数 pattern 描述的字符串没有找到，迭代函数返回nil，init默认为1，从1开始匹配。

与string.find区别在于不会返回捕获到的内容的起止下标。

```lua
> for word in string.gmatch("Hello Lua user", "%a+") do
  print(word)
end

output：
Hello
Lua
user
```



这里是一个捕获并将配对字符分别存到不同变量的例子:

```lua
t = {}
s = "from=world, to=Lua"
for k, v in string.gmatch(s, "(%w+)=(%w+)") do
    t[k]=v
end
for k, v in pairs(t) do
    print(k, v)
end
```



* **`string.gsub (s, pattern, repl [, n])`**

```lua
string.gsub(s,pattern,repl [, n]) ==  s:gsub(pattern,repl [, n])
```

在字符串中替换。

s: 源字符串
pattern: 需要替换的模式串
repl: 替换的内容
n: 替换次数



**string.gsub()函数根据给定的配对表达式对源字符串str进行配对, 同时返回源字符串的一个副本, 该副本中成功配对的所有子字符串都将被替换. 函数还将返回成功配对的次数.实际的替换行为由repl参数的类型决定:**

1.当repl为字符串时, 所有成功配对的子字符串均会被替换成指定的repl字串.
2.当repl为table时, 对每个成功配对的子字符串, 函数均会试图寻找以其为key值的table中的元素, 并返回该元素. 如果该配对包含任何捕获信息, 则以编号为1号的捕获作为key值进行查找.
3.当repl为函数时, 每个成功配对的子字符串均会作为参数被传入到该函数中去.
4.在repl是table或函数时, 如果该table或函数返回了字串或数字的值, 这个值依然会被用于替换副本字串中的配对子字串. 如果该table/函数返回的值为空, 将不发生替换.

n参数可选, 当它被指定时, string.gsub()函数只对源字符串中的前n个成功配对的成员进行操作.

以下是几个例子:

```lua
print(string.gsub("hello world", "(%w+)", "%1 %1"))
--> hello hello world world       2

print(string.gsub("hello world", "%w+", "%0 %0", 1))
--> hello hello world       1

print(string.gsub("hello world from Lua", "(%w+)%s*(%w+)", "%2 %1"))
--> world hello Lua from       2

print(string.gsub("home = $HOME, user = $USER", "%$(%w+)", os.getenv))
--> home = /Users/rally, user = rally       2


local t = {name="lua", version="5.4"}
print(string.gsub("name-version.tar.gz", "(%w+)", t))
--> lua-5.4.tar.gz       4

function func(a,b,c)
    return a.."="..b+c
end

print(string.gsub("return= 4+5", "(%w+)%p%s(%d)%p(%d)", func))

--> return=9        1
```



* **`string.match(s, pattern, init)`**

```lua
string.match(s,pattern, init) ==  s:match(pattern, init)
```

string.match()只寻找源字串str中的第一个配对. 参数init可选, 指定搜寻过程的起点, 默认为1。
在成功配对时, 函数将返回配对表达式中的所有捕获结果; 如果没有设置捕获标记, 则返回整个配对字符串. 当没有成功的配对时, 返回nil。

```lua
> = string.match("I have 2 questions for you.", "%d+ %a+")
2 questions

> = string.format("%d, %q", string.match("I have 2 questions for you.", "(%d+) (%a+)"))
2, "questions"
```


# 五、错误处理

## 错误处理基本函数

* **assert(conditions,message)**：

```lua
local function test(a)
	assert(type(a) == "number", a.."不是数字")

	print("hello world")
end

test(1)
test("abcd")

--output:
--hello world
--lua: /Users/rally/Desktop/Pyfolder/test.lua:350: abcd不是数字
--stack traceback:
--        [C]: in function 'assert'
--        /Users/rally/Desktop/Pyfolder/test.lua:350: in local 'test'
--        /Users/rally/Desktop/Pyfolder/test.lua:356: in main chunk
--        [C]: in ?
```

帮助知道是这个地方传参出错了

* **error(message[,level]**：

  error的功能是终止正在执行的函数，并返回message的内容作为错误信息(error函数永远都不会返回)，通常情况下，error会附加一些错误位置的信息到message头部。
Level参数指示获得错误的位置：
Level=1[默认]：为调用error位置(文件+行号)
Level=2：指出哪个调用error的函数的函数
Level=0:不添加错误位置信息

```lua
print("input data：")
n = io.read()
if not tonumber(n) then
	error("invalid input")
else
	print("you input data is :",n)
end


正常运行结果：
input data：
1
you input data is :     1

错误运行结果：
input data：
a
lua: /Users/rally/Desktop/Pyfolder/test.lua:381: invalid input
stack traceback:
        [C]: in function 'error'
  			/Users/rally/Desktop/Pyfolder/test.lua:381: in main chunk
        [C]: in ?
```



* **pcall(function,parameter):**


* **lua 中的 try … catch ...**

通过pcall和error可以实现类其它程序语言的try/catch的异常捕获操作

pcall接收一个函数和要传递给该函数的参数，执行结果无错误则返回true，有错误则返回false，errorinfo，**如果参数1中这个函数也会return值，则可以通过定义第二个值来接收**

```lua
function foo()
	n = io.read()
	if not tonumber(n) then
		error("invalid input")
	else
		return "you input data is :"..n
	end
end
local status,result = pcall(foo)
print(status,result)


错误运行结果：
a
false   /Users/rally/Desktop/Pyfolder/test.lua:389: invalid input

正常运行结果:
1
true    you input data is :1
```



* **xpcall(function1,function2,parameter)：**

Lua提供了xpcall函数，function1为将要执行的函数，xpcall接收第二个参数是一个错误处理函数，后面的参数为提供给function1函数的参数，当错误发生时，Lua会在调用桟展开（unwind）前调用错误处理函数，于是就可以在这个函数中使用debug库来获取关于错误的额外信息了。

debug库提供了两个通用的错误处理函数：
1.debug.debug：提供一个Lua提示符，让用户来检查错误的原因
2.debug.traceback：根据调用桟来构建一个扩展的错误消息

```lua
function myfunction ()
    n = n / nil
end

function myerrorhandler(err)
    print("ERROR:", err)
end

status = xpcall(myfunction, myerrorhandler)
print(status)

output:
ERROR:    test2.lua:2: attempt to perform arithmetic on global 'n' (a nil value)
false
```



# 六、调试

# 七、变量

## 变量定义

变量在使用前，需要在代码中进行声明，即创建该变量。

编译程序执行代码之前编译器需要知道如何给语句变量开辟存储区，用于存储变量的值。

Lua 变量有三种类型：全局变量、局部变量、表中的域。

Lua 中的变量全是全局变量，那怕是语句块或是函数里，除非用 local 显式声明为局部变量。

局部变量的作用域为从声明位置开始到所在语句块结束。

变量的默认值均为 nil。



```lua
a = 5               -- 全局变量
local b = 5         -- 局部变量

function joke()
    c = 5           -- 全局变量
    local d = 6     -- 函数内的局部变量
    print(c,d)      --> 5 6
end

joke()
print(c,d)          --> 5 nil

do
    local a = 6     -- 局部变量
    b = 6           -- 对局部变量重新赋值
    print(a,b);     --> 6 6
end

print(a,b)      --> 5 6
```

## 变量赋值

遇到赋值语句Lua会先计算右边所有的值然后再执行赋值操作，所以我们可以这样进行交换变量的值：

```lua
x, y = y, x                     -- swap 'x' for 'y'
a[i], a[j] = a[j], a[i]         -- swap 'a[i]' for 'a[j]'
```

当变量个数和值的个数不一致时，Lua会一直以变量个数为基础采取以下策略：

```lua
a. 变量个数 > 值的个数             按变量个数补足nil
b. 变量个数 < 值的个数             多余的值会被忽略

a, b, c = 0, 1
print(a,b,c)             --> 0   1   nil
 
a, b = a+1, b+1, b+2     -- value of b+2 is ignored
print(a,b)               --> 1   2
 
a, b, c = 0
print(a,b,c)             --> 0   nil   nil 注意：如果要对多个变量赋值必须依次对每个变量赋值。

a, b, c = 0, 0, 0
print(a,b,c)             --> 0   0   0
```

## 索引

对 table 的索引使用方括号 []。Lua 也提供了 . 操作。

```lua
t[i]
t.i                 -- 当索引为字符串类型时的一种简化写法
gettable_event(t,i) -- 采用索引访问本质上是一个类似这样的函数调用

site = {}
site["key"] = "value"
print(site["key"])       -->value

print(site.key)          -->value
```

# 八、循环

## Lua循环类型

Lua 语言提供了以下几种循环处理方式：

| 循环类型         | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| [while 循环]     | 在条件为 true 时，让程序重复地执行某些语句。执行语句前会先检查条件是否为 true。 |
| [for 循环]       | 重复执行指定语句，重复次数可在 for 语句中控制。              |
| [repeat...until] | 重复执行循环，直到 指定的条件为真时为止                      |
| [循环嵌套]       | 可以在循环内嵌套一个或多个循环语句（while do ... end;for ... do ... end;repeat ... until;） |

**1. [while 循环]**

```lua
a=10
while( a < 15 )
do
   print("a 的值为:", a)
   a = a+1
end

output:
a 的值为:       10
a 的值为:       11
a 的值为:       12
a 的值为:       13
a 的值为:       14
```

**2. [for 循环]**

    数值for循环

Lua 编程语言中数值 for 循环语法格式:

```lua
for var=exp1,exp2,exp3 do  
    <执行体>  
end  
```

var 从 exp1 变化到 exp2，每次变化以 exp3 为步长递增 var，并执行一次 **"执行体"**。exp3 是可选的，如果不指定，默认为1。

```lua
for i=5,1,-1 do
    print(i)
end

output:
5
4
3
2
1
```



```lua
function f(x)  
    print("function")  
    return x*2  
end

for i=1,f(3) do 
  print(i)  
end

output:
function
1
2
3
4
5
6
```

for的三个表达式在循环开始前一次性求值，以后不再进行求值。比如上面的f(x)只会在循环开始前执行一次，其结果用在后面的循环中。



    泛型for循环

泛型 for 循环通过一个迭代器函数来遍历所有值。

Lua 编程语言中泛型 for 循环语法格式:

```lua
--打印数组a的所有值  
a = {"one", "two", "three"}
for i, v in ipairs(a) do
    print(i..":"..v)
end 

output:
1:one
2:two
3:three
```

i是数组索引值，v是对应索引的数组元素值。ipairs是Lua提供的一个迭代器函数，用来迭代数组。

**3. [repeat...until]**

Lua 编程语言中 repeat...until 循环语句不同于 for 和 while循环，for 和 while 循环的条件语句在当前循环执行开始时判断，而 repeat...until 循环的条件语句在当前循环结束后判断。

```lua
a = 10
--执行循环
repeat
   print("a的值为:", a)
   a = a + 1
until( a > 15 )

output:
a的值为:        10
a的值为:        11
a的值为:        12
a的值为:        13
a的值为:        14
a的值为:        15
```

**4. [循环嵌套]**

```lua
j =1
for i=1,3 do
   for j=1,3 do 
        print("j 的值为："..j.."    i 的值为："..i)
    end
end

output:
j 的值为：1    i 的值为：1
j 的值为：2    i 的值为：1
j 的值为：3    i 的值为：1
j 的值为：1    i 的值为：2
j 的值为：2    i 的值为：2
j 的值为：3    i 的值为：2
j 的值为：1    i 的值为：3
j 的值为：2    i 的值为：3
j 的值为：3    i 的值为：3
```



# 九、流程控制

Lua if 语句可以与 elseif...else 语句搭配使用, 在 if 条件表达式为 false 时执行 elseif...else 语句代码块，用于检测多个条件语句。

```lua
for i=1,5 do
    if(i<3)
    then
        print("case1")
    elseif(i<5)
    then
        print("case2")
    else
        print("case3")
    end
end

output:
case1
case1
case2
case2
case3
```



# 十、函数

## 内置函数

Lua 5.3参考手册：https://www.lua.org/manual/5.3/

### **基础函数**

**rawequal(v1,v2)**

rawequal检查v1与v2是否相等，返回比较结果。

```lua
a=v1
b=v2
c={v2}
d=1
e=2
print(rawequal(a,b))  -->true
print(rawequal(b,c))  -->false
print(rawequal(d,e))  -->false
print(rawequal(a,e))  -->false
```

**rawget(table,index)**

获取table中键index的关键值，table参数必须是一个表，找不到返回nil。

```lua
t={"a","b","11","22",x=3}
print(rawget(t,"x"))   -->3
print(rawget(t,1))     -->a
print(rawget(t,5))     -->nil
```

**rawset(table,index,value)**

将table[index]的值设置为value。table必须是一张表，index不能是nil，value可以是任何值。

```lua
function showtable(t)
    for k,v in pairs (t) do
       print (k.."="..v)
    end
    return 
end

t1={"a",11,x=3}
rawset(t1,1,"aa")
showtable(t1)
--[[   
1=aa
2=11
x=3   
--]]
rawset(t1,"c","cc") 
showtable(t1)
--[[ 
1=aa
2=11
c=cc
x=3  
--]]
rawset(t1,"c",nil) 
showtable(t1)
--[[ 
1=aa
2=11
x=3  
--]]
```

**select(index, ...)：**

如果index是数字，则返回参数number index之后的所有参数；负数从末尾开始索引（-1是最后一个参数）。否则，index必须是字符串“#”，select返回参数的总数。

```lua
print(select(2, 1, 6, 8, 8, 9))  -->6  8	 8	9
a=select(2, 1, 6, 8, 8, 9)   
print (a)           -->6
a,b,c=select(2, 1, 6, 8, 8, 9)
print (a,b,c)       -->6 8 8
d=select(-1, 1, 6, 8, 8, 9)
print(d)            -->9
```

**tonumber（e,[,base]）**

尝试把e转换为10进制并返回。如果无法转换返回nil。

base表示传入参数的进制，默认为10进制。base范围[2.36]。

```LUA
print(tonumber(123))    -->123
print(tonumber("ab",16))  -->171
print(tonumber("111",2))  -->7
```

**tostring(e)**

可以将任意类型的值转换为字符串

```lua
function test()
    print("这是一个function")
end
tab1={1,2,3}

print(tostring(1))-->1
print(tostring(1+2))-->3
print(type(1+2))-->number
print(type(tostring(1+2)))-->string
print(tostring(tab1))-->table: 0x7fb74bc08d60
print(tostring(test))-->function: 0x7fb74bc08d30
```

### string函数

**string.len(s)**     
返回字符串s的长度

**string.rep(s, n)**
返回重复n次字符串s的串,使用string.rep("a", 2^20)可以创建一个1M bytes的字符串

**string.lower(s)**
将s中的大写字母转换成小写（string.upper将小写转换成大写）

```lua
print(string.len("Rachel is 小孬孬"))  -->19（中文字符占三个字节）
print(string.rep("CMSW ",3))          -->CMSW CMSW CMSW 
print(string.upper("hank的名字要大写")) -->HANK的名字要大写
```

**string.match(s,d)**
s是源字符串，d是目标字符串或者模式。

```lua
today="today is 2020/08/04"  
print(string.match(today,"%d"))           -->2
print(string.match(today,"%d+/%d+/%d+"))  -->2020/08/04 
```

**string.format()**

生成具有特定格式的字符串

%c - 接受一个数字, 并将其转化为ASCII码表中对应的字符
%d, %i - 接受一个数字并将其转化为有符号的整数格式
%o - 接受一个数字并将其转化为八进制数格式
%u - 接受一个数字并将其转化为无符号整数格式
%x - 接受一个数字并将其转化为十六进制数格式, 使用小写字母
%X - 接受一个数字并将其转化为十六进制数格式, 使用大写字母
%e - 接受一个数字并将其转化为科学记数法格式, 使用小写字母e
%E - 接受一个数字并将其转化为科学记数法格式, 使用大写字母E
%f - 接受一个数字并将其转化为浮点数格式
%g(%G) - 接受一个数字并将其转化为%e(%E, 对应%G)及%f中较短的一种格式
%q - 接受一个字符串并将其转化为可安全被Lua编译器读入的格式
%s - 接受一个字符串并按照给定的参数格式化该字符串

(1) 符号: 一个+号表示其后的数字转义符将让正数显示正号. 默认情况下只有负数显示符号.
(2) 占位符: 一个0, 在后面指定了字串宽度时占位用. 不填时的默认占位符是空格.
(3) 对齐标识: 在指定了字串宽度时, 默认为右对齐, 增加-号可以改为左对齐.
(4) 宽度数值
(5) 小数位数/字串裁切: 在宽度数值后增加的小数部分n, 若后接f(浮点数转义符, 如%6.3f)则设定该浮点数的小数只保留n位, 若后接s(字符串转义符, 如%5.3s)则设定该字符串只显示前n位.
在这些参数的后面则是上述所列的转义码类型(c, d, i, f, ...).

```lua
d = 5; m = 11; y = 1990  
print(string.format("%02d/%02d/%04d", d, m, y))--> 05/11/1990  
tag, title = "h1", "a title"  
print(string.format("<%s>%s</%s>", tag, title, tag))  --> <h1>a title</h1>  
print(string.format("%c", 83))               -->输出S  
print(string.format("%05d", 17))             -->输出00017  
print(string.format("%o", 10))               -->输出12   
print(string.format("%x", 666))              -->输出29a  
print(string.format("%X", 666))              -->输出29A
print(string.format("%6.3f", 13))            -->输出13.000  
print(string.format("%s", "happy"))          -->输出happy          
print(string.format("%5.3s", "happy"))       -->输出  hap 
```

## 自定义函数

### 函数格式

Lua 编程语言函数定义格式如下：

```lua
optional_function_scope function function_name( argument1, argument2, argument3..., argumentn)
    function_body
    return result_params_comma_separated
end
```

解析：

- **optional_function_scope:** 该参数是可选的制定函数是全局函数还是局部函数，未设置该参数默认为全局函数，如果你需要设置函数为局部函数需要使用关键字 **local**。
- **function_name:** 指定函数名称。
- **argument1, argument2,..., argumentn:** 函数参数，多个参数以逗号隔开，函数也可以不带参数。
- **function_body:** 函数体，函数中需要执行的代码语句块。
- **result_params_comma_separated:** 函数返回值，Lua语言函数可以返回多个值，每个值以逗号隔开。

```lua
--[[ 函数返回两个值的最大值 --]]

--默认全局函数，max为函数名，“num1, num2”为参数
function max(num1, num2) 
--函数执行代码语句   
  if (num1 > num2) then
      result = num1;
   else
      result = num2;
   end
--函数返回值
   return result;
end
-- 调用函数
print("两值比较最大值为 ",max(10,4)) -->10
print("两值比较最大值为 ",max(5,6))  -->6
```

Lua 中我们可以将函数作为参数传递给函数

```lua
function slap(num1)
   print("Rally拍了拍Bean说你",num1,"斤了")
end

function add(num1,num2,functionPrint)
   result = num1 + num2
   functionPrint(result)  -- 调用传递的函数参数
end

slap(200)
print("过了一个月")
add(200,50,slap) -- slap 函数作为参数传递

--[[
Rally拍了拍Bean说你	200	斤了
过了一个月
Rally拍了拍Bean说你	250	斤了
]]--
```

### 多返回值

Lua函数可以返回多个结果值

```lua
function maximum (a)
    local mi = 1             -- 最大值索引
    local m = a[mi]          -- 最大值
    for i,val in ipairs(a) do
       if val > m then
           mi = i
           m = val
       end
    end
    return m, mi
end

print(maximum({8,10,23,12,5}))  -->23  3
```

### 可变参数

Lua 函数可以接受可变数目的参数，和 C 语言类似，在函数参数列表中使用三点 **...** 表示函数有可变的参数。

```lua
function add(...)  
local s = 0  
  for i, v in ipairs{...} do   --> {...} 表示一个由所有变长参数构成的数组  
    s = s + v  
  end  
  return s  
end  
print(add(3,4,5,6,7))  --->25

function average(...)
   result = 0
   local arg={...}    --> arg 为一个表，局部变量
   for i,v in ipairs(arg) do
      result = result + v
   end
   print("总共传入 " .. #arg .. " 个数")
   return result/#arg
end

print("平均值为",average(10,5,3,4,5,6))
--[[
总共传入 6 个数
平均值为	5.5
--]]

```



# 十一、运算符

# 十二、数组

### :one: 一维数组

- 定义数组的时候是{} 而不是[]。
- 未定义索引的时候，数组的索引是从0开始的。
- 对于未定义的超出索引范围的引用不会报类似"IndexError: list index out of range"的Error,而是会返回`nil`。
- lua 的数组可以跳着定义，例如可以直接a[10]=10。
- 直接print(array)的时候不会把所有数组都打印出来，而是会返回array的类型和数据地址。
- lua里没有append函数但是有类似操作，可以直接在最后一个索引处给它赋值。

```lua
array = {"Lua", "Tutorial"}

for i= 0, 3 do
   print(array[i])
end

output:
nil
Lua
Tutorial
nil

> a={1,2,3,4}
> a[10]=5
> a[10]
5
>

> a={1,2,3,4}
> a
table: 0x7faa695041f0

> type(a)
table

> for k,v in ipairs(a) do
>> print(k,v)
>> end
1	1
2	2
3	3
4	4
> a[10]=10
> a[10]
10
------- 直接在第10位上插入数据，循环读取的时候并没有读到这个数，长度是4
> for k,v in ipairs(a) do                                                                                     print(k,v)                                                                                                    end
1	1
2	2
3	3
4	4
> #a
4
> a[5]=5
-------- 在接下来的第5位上插入数据，相当于做append操作，循环读取可以读到,长度也是5
> for k,v in ipairs(a) do                                                                                     print(k,v)                                                                                                    end
1	1
2	2
3	3
4	4
5	5
> #a
5
---------- insert ----------
>> table.insert(a,3,"yu")
> a
table: 0x7faa695041f0
> for k,v in ipairs(a) do                                                                                     print(k,v)                                                                                                    end
1	1
2	2
3	yu
4	3
5	4
6	5

----- 进行插入操作后第10位的10，移到第11位了,也就是说虽然循环操作没有没有读到table里a[10]的值，但这个vaule确实是存在a这个table里的。
> a[10]
nil
> a[11]
10


-- ipars 和 pars的区别
array = {"Lua", nil, "Tutorial"}
> for k,v in ipairs(array) do                                                                                     print(k,v)                                                                                                    end
1	Lua
> for k,v in pairs(array) do                                                                                     print(k,v)                                                                                                    end
1	Lua
10	orr
3	Tutorial
>
```



```lua
---- Why ??
> array = {"Lua", nil, "Tutorial"}
> #array
3
> array[10]="orry"
> #array
1
```





### :two:多维数组

```lua
-- 多维数组即数组中包含数组或一维数组的索引键对应一个数组。
-- 以下是一个三行三列的阵列二维数组：

-- 初始化数组
array = {}
for i=1,3 do
   array[i] = {}
      for j=1,3 do
         array[i][j] = i*j
      end
end

-- 访问数组
> array[1][2]
2
> array[1][4]
nil

```

# 十三、迭代器

# 十四、table(表)

table 是 Lua 的一种数据结构用来帮助我们创建不同的数据类型，如：数组、字典等。

Lua是通过table来解决模块（module）、包（package）和对象（Object）的。 例如string.format表示使用"format"来索引table string。

Lua的表中元素类似于下图中的桌子，是拼接而成的。

<img src="https://upload-images.jianshu.io/upload_images/2133677-676cf65650a39318.png" alt="2133677-676cf65650a39318" style="zoom:50%;" />

###  :one:数组是表的一种

```lua
-- 初始化表
mytable = {}

-- 指定值
mytable[1]= "Lua"

-- 移除引用
mytable = nil
-- lua 垃圾回收会释放内存
```

### :two:Table 操作常用的方法：
####  1. `table.concat(list, sep, i, j)`
- 依次为:指定的list，分隔符sep(默认为空)，开始位置 i (默认为1)，结束位置 j (默认为#table)，如果i大于j，则返回空字符串。

```lua
> a={"b","c","d","e","f","g"}
> table.concat(a)
bcdefg

> table.concat(a,":")
b:c:d:e:f:g

> table.concat(a,nil,2,3)
cd

> table.concat(a,":",2,3)
c:d

-- concat list 中不能有nil
> tbl2 = { "orange", "apple", nil, "pear", "banana" }
> table.concat(tbl2)
stdin:1: invalid value (nil) at index 3 in table for 'concat'
stack traceback:
	[C]: in function 'table.concat'
	stdin:1: in main chunk
	[C]: in ?
>> for i, v in pairs(tbl2) do
>>     print(i, '=', v)
>> end
1	=	orange
2	=	apple
4	=	pear
5	=	banana
```

#### 2. `table.insert(list, [pos,] value)`
- 将元素值插入列表中的pos位置，向上移动元素列表[pos]、列表[pos+1]、···、列表[#list]。
- pos的默认值是#list+1，因此table.insert(t,x)是将x插入到列表t的末尾。

```lua
--- pos 为空则默认将它插入到list的最后
> a={"b","c","d","e","f","g"}
> table.insert(a,"yu")
> table.concat(a)
bcdefgyu
> a[1]
b
> a[7]
yu
> a[6]
g
> a[8]
nil
> table.concat(a,":")
b:c:d:e:f:g:yu

---- pos 为一个数
> a={"b","c","d","e","f","g"}
> table.insert(a,3,"yu")
> table.concat(a,",")
b,c,yu,d,e,f,g

-- value 不能为list
> table.insert(a,5,{me,yu})
> table.concat(a,",")
stdin:1: invalid value (table) at index 5 in table for 'concat'
stack traceback:
	[C]: in function 'table.concat'
	stdin:1: in main chunk
	[C]: in ?
> a[5]
table: 0x7fc8194156c0
> a[5][1]
nil

```

#### 3. `table.move(a1, f, e, t [,a2])`
- 将元素从表a1移动到表a2，执行如下多重赋值操作:a2[t],··· = a1[f],···,a1[e]。
- a2的默认值是a1。
- 函数作用: 把表a1中从下标f到e的value移动到表a2中，位置为a2下标从t开始。
- 函数参数: 表a1，a1下标开始位置f，a1下标结束位置e，选择移动到的a2的开始位置t。

```lua
--- 指定a2参数，会改变a2的数据元素
> atab={"b","c","d","e","f","g"}
> newtab={1,2,3,5}
> table.move(atab,2,3,2,newtab)
table: 0x7fd67a4153e0
> table.concat(newtab,",")
1,c,d,5
> table.concat(atab,",")
b,c,d,e,f,g
>

--- 不指定a2参数，会修改本身a1的数据元素
> atab={"b","c","d","e","f","g"}
> table.move(atab,2,3,4)
table: 0x7fd67a604d00
> table.concat(atab,",")
b,c,d,c,d,g
>

--- 将第三位替换成table的len，相当于把atab从2开始依次后挪了一位
> atab={"b","c","d","e","f","g"}
> table.move(atab, 1, #atab, 2)
table: 0x7fc8197048f0
> table.concat(atab,",")
b,b,c,d,e,f,g
```

- insert 是将一个值插入到table中，move可以将一组数插入到table中。

####  4.`table.remove(list [, pos])`

- 从列表中删除位置为pos的元素，返回被删除元素的值。
- 当pos为1和#list之间的整数时，向下移动元素list[pos+1]， list[pos+2]，···，list[#list]并擦除元素list[#list];
    当#list为0或#list + 1时，索引pos也可以为0;
    在这些情况下，函数会擦除元素列表[pos]。

```lua
---- 默认删除最后一个元素
> a={"b","c","d","e","f","g"}
> table.remove(a)
g
> table.concat(a,",")
b,c,d,e,f

```

#### 5. `table.sort (list [, comp])`

[Lua的table.sort踩坑点](https://zhuanlan.zhihu.com/p/85949548)

- 如果参数`comp`不省略，则它必须是一个函数，可以接收表`tab_table`的两个元素，并且在第一个元素小于第二个元素时返回`true`，其他情况返回`false`。

- 如果省略参数`comp`，则Lua彼岸准运算符`operator <`将会被使用。

```lua
> a={"g","f","e","d","c","b"}
> table.concat(a,",")
g,f,e,d,c,b
> table.sort(a)
> table.concat(a,",")
b,c,d,e,f,g

----- sort 排序的时候没有 2^n的顺序问题
> a={6,5,4,3,2,1}
> table.sort(a)
> table.concat(a,",")
1,2,3,4,5,6
>

```

自定义 sort 函数

```lua
local tabLanguage = {
    "q",
    "ab",
    "z",
    "w",
    "stuvw",
    "xyz",
    "e",
    "def",
    "c",
};

print("\nLUA>>>>>>the source elements of table tabLanguage is:")
for k,v in pairs(tabLanguage) do
    print(k,v)
end

-- 使用默认函数排序
table.sort(tabLanguage)
print("\nLUA>>>>>>After sort, the elements of table tabLanguage is:")
for k,v in pairs(tabLanguage) do
    print(k,v)
end

-- 定义自己的比较函数
local function my_comp(element1, elemnet2)
    return string.len(element1) < string.len(elemnet2)
end

-- 使用自己的比较函数排序（按字符由短到长排序）
table.sort(tabLanguage, my_comp)
print("\nLUA>>>>>>After sort using my_comp, the elements of table tabLanguage is:")
for k,v in pairs(tabLanguage) do
    print(k,v)
end

-- 再定义一个自己的比较函数
local function my_comp_new(element1, elemnet2)
    return element1 > elemnet2
end

-- 使用自己的比较函数排序（按字符长段排序）
table.sort(tabLanguage, my_comp_new)
print("\nLUA>>>>>>After sort using my_comp_new, the elements of table tabLanguage is:")
for k,v in pairs(tabLanguage) do
    print(k,v)
end

-- 定义处理nil的函数
local function my_comp_new_with_nil(element1, elemnet2)
    if element1 == nil then
        return false;
    end
    if elemnet2 == nil then
        return true;
    end
    return element1 > elemnet2
end

-- 创造一个空洞
tabLanguage[2] = nil
-- 使用默认函数排序
--table.sort(tabLanguage, my_comp_new_with_nil)
print("\nLUA>>>>>>After sort using my_comp_new_with_nil, the elements of table tabLanguage is:")
for k,v in pairs(tabLanguage) do
    print(k,v)
end
```

#### 6. `table.pack(···)`

```lua

```



#### 7. `table.unpack (list [, i [, j]])`



# 十五、模块与包

# 十六、元表(Metatable)

# 十七、协同程序(coroutine)

# 十八、文件 I/O

# 十九、面向对象