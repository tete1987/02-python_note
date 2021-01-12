# 四、python函数
## （一）函数的定义
### 1.定义
函数代码块以def关键词开头，后接函数标识符名称和圆括弧（）。

任何传入参数和自变量必须放在圆括弧中间，圆括弧直接可以用于定义参数。

函数的第一行语句可以选择性地使用文档字符串-用于放存函数说明。

函数内容以冒号起始，并且缩进。

return表达式结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回none。
示例：
```
def mathod(a):
    print(a)
    
mothod(1)    
```
增加return表达式：
```
def mathod(a):
    print(a)
    return a+2
    
print(mathod(1))   
```


## （二）函数的各类参数
### 1.定义
1）必需参数
- 必需参数的含义就是，如果在函数内有参数，且我们在调用的过程中，没有给参数进行传参，就会报错。

2）默认参数
- 调用函数时，如果没有传递参数，则会使用默认参数。
- 默认参数在定义函数的时候定义。
- 默认值只会执行一次。这规则在默认值为可变对象时很重要。

示例：
```
def method(a,b=[]):
    b.append(a)
    return b
  
print(method(1))      
print(method(2))
```

### 2.函数的参数
1）关键字参数
- kwarg=value形式，在调用函数时添加
- 在函数调用/定义中，关键字参数必须跟随在位置参数的后面。
- 当存在一个形式为**name的一个形参时，它会接收一个字典。
- 形式为*name，接收一个包含除了与已有形参列表以外的位置参数的元组的形参。

示例1：
```
def method(a,b):
    print(a)
    print(b)
    return b
    
print(method(a=1,b=2))   
```

示例2(传入字典)：
```
def method(**a):
    print(a.keys())
    
method(a=1,b=2,c=3)    
```

示例3（传入元组）：
```
def method(*a):
    print(a[0])
    print(a[1])
    print(a[2])
    print(a[3])

method(1,2,3,4)
```

### 3.特殊参数

`* `：仅限关键字参数，在【仅限关键字】形参前放置一个 *

示例1：
```
def method(*,a):
    print(a)
    
method(a=1)    
```
注：
仅限关键字必须由显式的名称参数填充，不可使用位置参数填充。


4.解包参数列表

`*` ：用来解包元组

`**` ：用来解包字典

示例1（字典解包）：
```
def method(a,b,c):
    print(a)
    print(b)
    print(c)
    return a,b,c

dict1 = {"a":1,"b":2,"c":3}
print(method(**dict1))
```

## （三）Lambda表达式
### 1.定义：
- 可以用lambda关键字来创建一个小的匿名函数。

- 关键字为lambda

- lambda的主体是一个表达式，而不是一个代码块。仅仅能在lambda表达式中封装有限的逻辑进去。

示例1：
```python
y = lambda x:x+2

print(y(2))
```

示例2：
```python
y = lambda x,y,z:x+y+z

print(y(2,3,4))

```


## （四）高阶函数
### 1.map函数
map()函数接收两个参数，一个是函数，一个是Iterable，map将传入的函数依次作用到序列的每个元素，并把结果作为新的Iterator返回。

示例：
```python
def f(x):
    return x*x

r = map(f,[2,4,3,2])
print(list(r))
```

返回：[4, 16, 9, 4]

### 2.filter函数
filter()也接收一个函数和一个序列。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。

示例：
```python
def is_odd(n):
    return n % 2 == 1

print(list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15])))
```

## （五）函数装饰器
### 1.函数的使用：
&nbsp;1）函数可以当做一个变量

&nbsp;2）函数的参数也可以是函数
```python
def login(username="tete",password="admin"):
    if username == 'tete' and password == 'admin':
        return "yes"
    else:
        return "登录账号错误"

def profile(token):
    if token == "yes":
        return "欢迎登录"
    else:
        return "请重新登录"

print(profile(login()))
```
输出：欢迎登录

3）函数是可以嵌套的
```python
def f3():
    def f4():
        return "hello"
    return f4()

print(f3())
```

执行过程：

![python装饰器](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/python-%E8%A3%85%E9%A5%B0%E5%99%A8.png)

### 2.函数的装饰器
1）代码的开放封闭原则：
- 封闭：已实现的功能代码尽可能的不要做修改
- 开放：对现有的功能代码可扩展

2）示例：
```python
'''需求：在调用f1 或f2 函数的时候，先打印python课程，再打印后面的内容'''

def getInfo(func):
    def inner():
        print("《python课程》")
        func()
    return inner

@getInfo
def f1():
    print("网易云课堂")


def f2():
    print("好好学习，天天向上")

f1()
```

执行顺序：

![python装饰器2](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/python-%E8%A3%85%E9%A5%B0%E5%99%A82.png)

步骤：

1.执行getInfo函数的时候，把被装饰的函数f1当做参数来传递

2.getInfo函数的返回值会重新赋值

3.一旦结合了装饰器之后，调用f1的函数其实执行的是inner函数的内部，原来的函数f1被覆盖

4.被装饰的函数f1重新赋值给装饰器的内层函数inner

3）案例1：
```python
def login(func):
    def inner(token):
        if token == 'aaaa':
            return func(token)
        else:
            return "请重新登录"
    return inner

@login
def profile(token):
    '''个人主页'''
    return "已登录"

print(profile("aaaa"))
```

4）案例2：
```python
① 根据需求完成原始代码：
import sys

'''需求：要求注册账号，然后注册的账号登录到系统后，显示出登录的昵称
1.注册的函数
2.登录的函数
3.获取昵称的函数
'''

def register():
    '''
    实现账户的注册功能
    :return:
    '''
    username = input("请输入账号：\n")
    password = input("请输入账号名称:\n")
    temp = username+"|"+password
    f=open('login.md','w')
    f.write(temp)
    f.close()


def login():
    '''
    登录的函数
    :return:
    '''
    username = input("请输入账号：\n")
    password = input("请输入账号名称:\n")
    with open("login.md","r") as f:
        info=f.read()
    info=info.split("|")
    if username == info[0] and password == info[1]:
        return True
    else:
        return False

def getNick(func):
    '''
    获取昵称
    :return:
    '''
    with open('login.md','r') as f:
        info=f.read()
    info = info.split("|")
    if func:
        print("{0}您好，欢迎您登录".format(info[0]))
    else:
        print("请重新登录")

if __name__ == '__main__':
    while True:
        t=int(input('1.注册  2.登录  3.退出系统\n'))
        if t==1:
            register()
        elif t==2:
            getNick(login())
        elif t==3:
            sys.exit(1)
        else:
            print("输入错误，请重新输入")
            continue

```

② 将重复的代码优化一下：
```python
import sys

'''需求：要求注册账号，然后注册的账号登录到系统后，显示出登录的昵称
1.注册的函数
2.登录的函数
3.获取昵称的函数
'''
def in_out():
    username = input("请输入账号：\n")
    password = input("请输入账号名称:\n")
    return username,password

def register():
    '''
    实现账户的注册功能
    :return:
    '''
    username,password = in_out()
    temp = username+"|"+password
    f=open('login.md','w')
    f.write(temp)
    f.close()


def login():
    '''
    登录的函数
    :return:
    '''
    username,password = in_out()
    with open("login.md","r") as f:
        info=f.read()
    info=info.split("|")
    if username == info[0] and password == info[1]:
        return True
    else:
        return False

def getNick(func):
    '''
    获取昵称
    :return:
    '''
    with open('login.md','r') as f:
        info=f.read()
    info = info.split("|")
    if func:
        print("{0}您好，欢迎您登录".format(info[0]))
    else:
        print("请重新登录")

if __name__ == '__main__':
    while True:
        t=int(input('1.注册  2.登录  3.退出系统\n'))
        if t==1:
            register()
        elif t==2:
            getNick(login())
        elif t==3:
            sys.exit(1)
        else:
            print("输入错误，请重新输入")
            continue
```
