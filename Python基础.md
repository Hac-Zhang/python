# 基本数据类型

## 数字类型及操作

### int 整数 可正可负 没有取值范围
- 四种进制:
    - 十进制：1010，99，-219
    - 二进制：(以0b或0B开头) 0b010, -0B101
    - 八进制：(以0o或者0O开头) 0o123, -0O456
    - 十六进制：(以0x或者0X开头) 0x9a， -0X89

### double 浮点数 
- 取值范围 -10^308到10^308,精度数量级10^-16      
    &emsp; **不确定尾数**

- round(x, d) 函数：  
    &emsp;对x进行四舍五入，d是小数截取位数

- 科学计数法:  
    使用字母E或者e为幂的符号，以10为基数，格式如下：   
    > <a>e<b> 表示 a*10^b

### 复数类型

- 复数是由一个实数和一个虚数组合构成,表示: x+yj
    - 实部： 可用 z.real获得实部
    - 虚部： 可用 z.imag获得虚部

### global声明使用全局变量
- 关键字global，后跟一个或多个变量名
    > global x   
    > x = 2
### 数值运算操作符
一元操作符:
- x + y: 相加
- x - y: 相减
- x * y: 相乘
- x / y: 相除
- x // y: 整除 结果为整数
- +x : x 本身
- -x : x 的负值
- x % y: 余数, 模运算 10%3结果为1
- x ** y: 幂运算，x的y次幂**(当y为小数时,为开方运算)**

二元操作符:
- x op= y
- x = x op y, 其中,op为二元操作符
- x += y, x -= y, x *= y, x /= y,
- x //= y, x %= y, x **= y

数据类型的关系:  
> 整数 -> 浮点数 -> 复数  
**如果三种类型存在运算时,则会向右侧转型**

## 字符串类型及操作
    字符串由一对单引号或者一对双引号表示
### python 对字符串进行编号

正向递增序号 和 反向递减序号
- 正向递增从0开始
- 反向递减从-1开始
- 使用方法为:
    ```
    a = "我正在学习python"
    a[0] = "我"
    a[-1] = "n"
    ```

### 字符串切片用法

使用[M:N:k]对字符串进行切片: M, N, K均可省略
- M:为起始位置(默认从0开始)
- N:为中止位置(默认到结尾)
- K:为步长(意义为间隔, 默认为1)

### 字符串的特殊字符:
转义符：

转义符| 含义
---|---
\\\ | 输出为'\'
\\n | 输出为换行
\\t | 输出为制表符
\\a | 响铃
\\b | 退格,删除键
\\' | 输出"'",单引号
\\" | 输出'"',双引号
\\r | 表示回车
\\v | 纵向位置添加制表符 为回车+制表符
\\f | 换页符
\\000| 表示空
\\x..| ..表示两位,意思是用两个16进制的数来表示一个字符
\\...| 表示用三个8进制数表示一个字符
### 字符串操作符
- x + y:   
    &emsp;连接两个字符串
- n * x 或 x * n:   
    &emsp;复制n次字符串x
- x in s :   
    &emsp;如果 x 是 s 的子串,返回True, 否则返回False
### 字符串处理函数
函数名称及用法

名称|   用法
---|---
len(x)  |    长度, 返回字符串x的长度(中文字符仍为 一个文字为一个字符)
str(x)  |    任意类型x所对应的字符串形式
eval(x) |    将x字符串去除最外层分号,转换为python可运行的命令
bin(x),oct(x),hex(x)|  将整数x转化为, 二进制, 八进制, 十六进制并返回
chr(u)  |    u为Unicode编码, 返回其对应的字符
ord(x)  |    x为字符, 返回其对应的Unicode编码

### 字符串处理方法
- str.lower() / str.upper()  
    &emsp;返回字符串的副本, 全部字符小写/大写
- str.split(sep = None)
    返回一个列表, 由str根据sep被分割的部分组成   
    >"A,B,C".split(",")
    
    >`['A', 'B' ,'C']`
- str.count(sub)  
    &emsp;返回字串sub在str中出现的次数

- str.rplace(old, new)  
    &emsp;返回字符串str副本, 所有old字串被替换为new
- str.center(width[,fillchar])  
    返回一个原字符串居中
    - width &emsp; 总宽度
    - fillchar (可选) 为填充字符 默认为空格  

    > python".center(20,"=") 

    >`======python======` 

- str.strip(chars)  
    &emsp;从str中去掉在其左侧和右侧 chars 中列出的字符 
    > "= python=".strip(" =np")
    
    > `"ytho"`

- str.join(iter)  
    &emsp;在iter变量除元素为每一个元素后增加一个str
    > ",".join("12345") 

    >`1,2,3,4,5`
### 字符串格式化
> `print("今天是d%月d%日, 我跑了%f米"%(1,1,100.2)) `  
> `printf(f"这是{n}")`
- format()  
    基本语法是通过 {} 和 : 来代替以前的 % 。  
    format 函数可以接受不限个参数，位置可以不按顺序。
- 数字格式化见表格
    ([表格来源](https://www.runoob.com/python/att-string-format.html))

    数字|	格式|	输出|	描述
    ---|---|---|---|
    3.1415926|	{:.2f}|     3.14|	保留小数点后两位
    3.1415926|	{:+.2f}|	+3.14|	带符号保留小数点后两位
    -1|	        {:+.2f}|	-1.00|	带符号保留小数点后两位
    2.71828|	{:.0f}|	    3|	    不带小数
    5|	        {:0>2d}|	05| 	数字补零 (填充左边, 宽度为2)
    5|      	{:x<4d}|    5xxx|  	数字补x (填充右边, 宽度为4)
    10|     	{:x<4d}|	10xx|	数字补x (填充右边, 宽度为4)
    1000000|	{:,}|   	1,000,000|	以逗号分隔的数字格式
    0.25|	    {:.2%}| 	25.00%|	百分比格式
    1000000000|	{:.2e}| 	1.00e+09|	指数记法
    13|     	{:>10d}|    13| 	右对齐 (默认, 宽度为10)
    13|     	{:<10d}|	13| 	左对齐 (宽度为10)
    13|     	{:^10d}|    13| 	中间对齐 (宽度为10)
    11|  	'{:b}'.format(11)<br>'{:d}'.format(11)<br>'{:o}'.format(11)<br>'{:x}'.format(11)<br>'{:#x}'.format(11)<br>'{:#X}'.format(11)|1011<br>11<br>13<br>b<br>0xb<br>0XB|	进制

# 分支结构

## 单分支结构

    if <条件> :
        <语句块>
## 二分支结构
    if <条件> :
        <语句块1>
    else :
        <语句块2>
## 多分支结构
    if <条件1> :
        <语句块1>
    elif <条件2> :
        <语句块2>
        ······
    else :
        <语句块n> 

## 条件判断:
### 操作符
- <: 小于
- <=: 小于等于
- &gt;: 大于
- &gt;=: 大于等于
- == ： 等于
- != : 不等于

### 条件组合

- x and y :  
    &emsp;两个条件x和y的逻辑 与 
- x or y :  
    &emsp;两个条件x和y的逻辑 或 
- not x :  
    &emsp;条件x的逻辑 非 

## 异常处理
```
try语句
    try:
        代码块（可能出现错误的语句）
    except 异常类型 as 异常名:
        代码块（出现错误以后的处理方式）
    except 异常类型 as 异常名:
        代码块（出现错误以后的处理方式）
    except 异常类型 as 异常名:
        代码块（出现错误以后的处理方式）
    else：
        代码块（没出错时要执行的语句）    
    finally:
        代码块（该代码块总会执行）    
```
>注意：
1. try是必须的 else语句有没有都行
2. except和finally至少有一个    
3. 可以将可能出错的代码放入到try语句，这样如果代码没有错误，则会正常执行，如果出现错误，则会执行expect子句中的代码，这样我们就可以通过代码来处理异常避免因为一个异常导致整个程序的终止

# 循环结构

## 遍历循环
    - for <循环变量> in <遍历结构>:
        <语句块>

## 无限循环
    - while <条件>:
        <语句块>
        
## 循环控制保留字
    - break
        结束整个循环
    - continue
        结束当前循环

## 循环的的扩展
可以在循环后面加如下:

    - else 
        //当循环没有被break语句推出时,执行else语句块
        - for <循环变量> in <遍历结构>:
                <语句块1>
            else :
                <语句块2>

        - while <条件>:
                <语句块1>
            else :
                <语句块2>

# 集合
1. 集合是多个元素的无序组合
2. 每个元素唯一，不存在相同元素
3. 集合元素不可更改,不能是可变数据类型
    
## 集合类型定义
1. 集合用大括号{}表示,元素间用逗号隔开
2. 建立集合类型用{} 或 set()
3. 建立空集合类型, 必须使用set()

## 集合操作符

1. S|T: 
    > 返回一个新的集合,包括在集合S和T中的所有元素
2. S-T: 
    > 返回一个新的集合,包括在集合S但不在T中的元素
3. S&T: 
    > 返回一个新的集合,包括同时在集合S和T中的元素
4. S^T: 
    > 返回一个新的集合,包括集合S和T中的非相同元素
5. S <= T或 S < T:
    > 返回True/False,判断S和T的子集关系
6. S >= T 或 S < T: 
    > 返回True/False,判断S和T的包含关系

## 增强操作符

- 增强操作符

    增强| 等价于
    ---|---
    S \|= T |   S = S\T
    S -= T  |   S = S - T
    S &= T  |   S = S&T
    S ^= T  |   S = S^T

## 集合处理方法

- 函数及其作用

    函数|   作用
    ---|---
    S.add(x)       | 如果x不再集合S中,将x增加到S
    S.discard(x)   | 移除S中元素x,如果x不在集合S中,不报错
    S.remove(x)    | 移除S中元素x,如果x不在集合S中,产生KeyError异常
    S.clear()      | 移除S中所有元素
    S.pop()        | 随机返回S的一个元素,更新S,若S为空产生KeyError异常
    S.copy()       | 返回集合S的一个副本
    len(S)         | 返回集合S的元素个数
    x in S         | 判断S中元素x, x在集合S中, 返回True， 否则返回False
    x not in S     | 判断S中元素x, x不再集合S中,返回True， 否则返回False
    set(x)         | 将其他类型变量x转变为集合类型

# 序列

## 序列类型定义

> 序列是一位元素向量,元素类型可以不同

> 类似数学元素序列: S1, S2,……,Sn-1

> 元素间由序号引导,通过下标访问序列的特定元素

> 正向递增序号  
> 反向递减序号

## 序列操作符

- 操作符实例及作用:

    实例|       作用
    ---|---
    x in s        | 查看x是否为s的元素,返回bool值
    x not in s    | 查看x是否为s的元素,返回bool值
    s + t         | 连接两个序列
    s\*n \*n\*s   | 将序列复制n次
    s[i]          | 索引， 返回s中的第i个元素
    s[i, j, k]    | 切片,与字符串相同
## 函数和方法

函数|作用
---|---
len(s)| 返回序列的长度
min(s)| 返回序列s的最小元素
max(s)| 返回序列s的最大元素
s.index(x), s.index(x,i,j)| 返回序列s从i到j位置中第一次出现的元素x位置
s.count(x)| 返回序列s中出现x的总次数

## 元组
- 元组的定义
    > 元组是一种序列类型,一旦创建就不能被修改  

    > 使用小括号()或tuple()创建,元素间用逗号,分隔  
    
    > 可以使用或不使用小括号

## 列表

### 列表的定义
1. 列表是一种序列类型, 创建后可以随意被更改
2. 使用方括号[]或者List()创建,元素间用逗号,分隔
3. 列表中个元素类型可以不用,无长度限制
> 注意：列表赋值时,仅仅将一个列表名只想前一个列表而并没有复制源列表本身
### 列表操作函数及方法

函数|   作用
---|---
 ls[i] = x         | 替换列表ls第i元素为x
 ls[i:j:k] = lt    | 用列表lt替换ls切片后所对应元素子列表
 del ls[i]         | 删除列表ls中第i元素
 del ls[i:j:k]     | 删除列表ls中第i到第j以k为步长的元素
 ls += lt          | 更新别来ls,将列表lt元素增加到列表ls中
 ls *= n           | 更新列表ls,其元素重复n次
 ls.append(x)      | 在列表最后增加一个元素x
 ls.clear()        | 删除列表ls中所有元素
 ls.copy()         | 生成一个新列表,复制ls中所有元素
 ls.insert(i, x)   | 在列表的第i个文职增加元素x
 ls.pop(i)         | 将列表中第i文职元素取出并删除该元素
 ls.remove(x)      | 将列表中出现的第一个元素x删除
 ls.reverse()      | 将列表ls中元素反转

## 字典

## 字典类型定义

1. 键值对: 键是数据索引的扩展
2. 字典是键值对的组合, 简直对之间无序
3. 采用大括号{}和dict()创建,键值对用冒号:表示

## 字典类型操作函数和方法

函数|   作用
---|---
 del d[k]              | 删除字典d中键k对应的数据
 k in d                | 判断键k是否在字典d中,返回bool类型
 d.keys()              | 返回字典d中所有的键信息
 d.values()            | 返回字典d中所有的值的信息
 d.items()             | 返回字典d中所有的键值对信息
 d.get(k, <defualt>)   | 键k存在,则返回相应值,不再则返回<default>值
 d.pop(k, <defualt>)   | 键k存在,则返回相应值,不再则返回<default>值
 d.popitem()           | 随机从字典d中取出一个键值对,以元组形式返回
 d.clear()             | 删除所有的键值对
 len(d)                | 返回字典d中元素的个数

# 函数

## 函数的定义

1. 函数是一段具有特定功能的、可重用的语句组
2. 函数是一种功能的抽象,一般函数表达特定功能
3. 两个作用: 降低编程难度 和 代码复用
    ```
     def <函数名>(<参数(0个或多个)>):
        <函数体>
        return <返回值>
    ```

## 函数参数个数
- 函数可以有参数,也可以没有, 但必须保留括号  
- 函数定义时可以为某些参数指定默认值,构成可选参数  
    &emsp;(但是需要放在非可选参数后面)  
    &emsp;`def <函数名>(<非可选参数>, <可选参数>):`  
    &emsp;&emsp;&emsp;`<代码块>`
- 函数定义时可以设计可变数量参数,即不确定参数总数  
    &emsp;`def <函数名>(<参数>, *b):`

## 参数传递的两种方式
- 按照位置传递
- 按照名称方式传递

## 函数的返回值
- return保留字用来传递返回值
- 函数可以有返回值,也可以没有,可以有return,也可以没有
- return 可以传递0个返回值,也可以传递任意多个返回值
## lambda函数 (谨慎使用)
 
- lambda函数是一种匿名函数,即没有名字的函数
- 使用lambda保留字定义,函数名是返回结果
- lambda函数勇于定义简单是、能够在一行内表示的函数
    ```
    <函数名> = lambda<参数>:<表达式>
    
    等价于 => def <函数名>(<参数>):
                  <函数体>
              return <返回值>
    ```

#  文件的数据格式化

## 文件的类型
- 文件是数据的抽象和集合
    1. 文件是储存在辅助器的数据序列
    2. 文件是数据储存的一种形式
    3. 文件展现形态: 文本文件和二进制文件

###  文本文件
- 有单一特定编码组成的文件, 如UTF-8编码
- 由于存在编码,也被堪称是存储着的长字符串

### 二进制文件
- 直接由比特0和1的组织结构,没有同意字符编码
- 一般存在二进制0和1的组织结构,即文件格式

##  文件的打开及关闭
> open("路径", “打开模式”)

- 打开模式

    标示|   作用
    ---|---
    'r'| 只读模式,默认值,如股票文件不存在,返回FileNotFoundError
    'w'| 覆盖写模式,文件不存在则创建,存在则完全覆盖
    'x'| 创建写模式,文件不存在则创建,存在则返回FileExistsError        
    'a'| 追加写模式,文件不存在则创建,存在则在文件最后追加内容
    'b'| 二进制文件模式
    't'| 文本模式,默认值
    '+'| 与r/w/x/a一同使用,在原功能基础上增加同时读写功能

- close()
    > <变量名>.close()


##  文件内容的读取

>` <f>.read(size = -1)`  
&emsp; 读入全部内容, 如果给出参数,读入前size长度

> `<f>.readline(size = -1)`  
&emsp; 读入一行内容,如果给出参数,读入改行前size长度
- `<f>.readlines(hint = -1)`  
&emsp; 读入文件所有行, 以每行为元素形成列表如果给出参数,读入前hint行
 ## 文件内容的写入
- `<f>.write(s)`  
    向文件写入一个字符串或字节流
- `<f>.writelines(lines)` 
    将一个元素全为字符串的列标写入文件
- `<f>.seek(offset)` 
    改变当前文件操作指针的位置,offset含义如下:  
    - 0 文件开头;   
    - 1 当前位置;  
    - 2 文件结尾; 




