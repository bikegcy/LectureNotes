#python

## Week 1
### 1.1  
between C and Shell.   
胶水语言，脚本语言，面向对象语言  

### 1.2  
Hello World.

```python
myString = 'Hello,world!'
print myString

```
运行方式：
  
- Shell方式
- 文件方式

Python(x,y)  
Use PyCharm   
>续行符： \

python用相同的**缩进**表示同级别语句块  

### 1.3 基础语法
变量
  
```python
p = 3.14159
myString =  'this is a string'
print p,myString
#大小写敏感
#支持增量赋值
m += 3
#支持多重赋值
PI = pi = 3.14
#多元赋值
x,y = 1,2
x,y = y,x
#交换（x,y）
#尽量写在括号里
(x,y) = (3,4)
```
python是动态的强类型语言，不需要事先声明  

### 1.4 数据类型

- 整型（后面加 L 为长整型）
- 布尔型 （True, False）
- 浮点型 （科学计数法9.8e3 = 9800）
- 复数型（虚数用 j 表示，2.4 + 2.3j, 虚部.imag, 实部.rael）
- 字符串（单引号，双引号，三引号）
- 映射类型，字典，用{}界别，类似哈希表键值对

### 1.5 基本运算

- 算数运算(+ - * **(乘方) //(整除) )
- 比较运算
- 逻辑运算(and,not,or)
- 位运算

### 1.6 函数，模块和包,库

四舍五入函数round(x)  
很多内建函数   

### 1.7 条件语句

```python
sd1 = 3
sd2 = 3
if sd1 == sd2:
    print 'yes they are equal'
elif sd1 > sd2:
	print 'sd1 is bigger'
```

### 1.8 range 和 xrange

```python
range(start,end,step)
range(start,end) #不包括 end
range(end)#从 0 开始

```
<center>

| 异同| range() | xrange() |    
| :-------:| :----:| :----:|
|语法| 一样 | 一样|
|返回| 列表 | 生成器 |
|生成|真实列表| 用多少生成多少|
</center>

### 1.9 循环

```python
sum = 1
j = 1
while j < 10:
	sum += 3
	j += 1
	
s = 'oython'
for c in s:
	print c
for i in range(3,11,2):
	print i
	if i == 9:
		break
	else continue

```
### 1.10 自定义函数

```python
def addMe2Me(x):
	'apply operation + to argument'#DocString
	return (x + x)

x = addMe2Me(3)

#函数的参数可以有一个默认值，如果提供有默认值，在函数定义中，默认参数以赋值语句的形式提供
#默认参数一般放到最后
#关键字参数
def f(x,y)
	print 'ds'
f(y = False,x = 87)

#传递函数
def addMe(x)
	return (x + x)
def self(f,y)
	print f(y)
self(addMe,2.2)

#lambda函数，匿名函数
r = lambda x: x + x
print r(5)
```

### 1.11 变量作用域

- 全局变量
- 局部变量

>global a

全局变量


## Week 2

### 2.1 本地数据处理／文件读写

```python

f1 = open(r'd:]]infile.txt)
f2 = open(r'd:\outlinr.txt','w')
f3 = open('frecord.csv','ab',0)
#file_obj = open(filename,mode = 'r', buffering = -1)
#mode为可选参数，默认值为r，buffering也为可选参数，默认值为-1（0代表不缓冲，1或大于1的值代表缓冲一行或制定区域的大小）

```

### 2.2 网络数据获取

- urllib
- urllib2
- httplib
- httplib2

### 2.3 序列

- 字符串(String)
- 元组(Tuple)
- 列表(list)

```python
week = ['Monday','Tuesday',Sunday']
print week[1],week[1:2]
,week[:2],week[::-1]
'apple' * 3
'apple' + 'pine'

#类型转换
list('Hello world!')
tuple("Hello world!")

```

### 2.4 字符串 ／ 列表 ／ 元组

```python

alist = [2,3,1,'dasd']
week = ['Monday','Tuesday',Sunday']
weekend = ['Saturday','Sunday']
week.extend(weekend)

#元组不可变，列表可变
#元组在映射中作为键使用
#元组作为函数的形式参数
#元组作为函数的返回类型

```


## Week 3

### 3.1 字典

- 键 key
- 值 value
- key-value 对

创建字典：

```python
ainfo =  {'Wangdachui':3000, 'Niuyun': 2000, 'Lining': 1000}
info = [('Wangdachui',3000), ('Niuyun',2000),('Lining',1000)]
binfo = dict(info)//dict函数创建字典
cinfo = dict(Wangdachui = 3000, Niuyun = 2000, Lining = 1000)

aDuct = {}.fromkeys(('Wangdachui','Niuyun',Lining'),3000)
sorted(aDict)//返回list

names = ['Wangdachui','Niuyun','Lining']
salaries = [3000, 2000, 1000]
dict(zip(names,salaries))
//使用zip构造字典

ainfo['Niuyun']//查找
ainfo['Niuyun'] = 8000//更新
ainfo['Fuyun'] = 500//添加
'Mayun' in ainfo//查询

for key in ainfo.keys()
	print ''

template = '''
	Welcome to the pay wall.
	Niuyun's salary is %(Niuyun)s.
	Wangdachui's salary is %(Wangdachui)s.
	'''
	//输出模版
print template % ainfo

ainfo.get('Mayun')
//没有则返回none，有则返回value
```

### 3.2 集合

```python
names = ['Wangdachui','Niuyun', 'Wangdachui']
namesSet = set(names)
print namesSet

//set 和 frozenset
```

<center>
![](https://github.com/bikegcy/MK_Pic/blob/master/python3.2.png?raw=true)

![](https://github.com/bikegcy/MK_Pic/blob/master/python3.2.2.png?raw=true)
</center>


























