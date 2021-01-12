# 六、python模块
## 1.python的程序结构
1）组成
- package
- module
- function

![python模块](https://github.com/tete1987/picture_resource/blob/master/python%E6%A8%A1%E5%9D%972.png)

## 2.定义：
模块是在代码量变得相当大了之后，为了将需要重复使用的有组织的代码放在一起，这部分代码可以被其他程序引用，从而使用该模块里的函数等功能，引用的过程叫做导入（import）

在python中，一个文件（以“py”为后缀名的文件）就叫做一个模块

导入模块的写法：
- 方法1：import module1[,module2……[,moduleN]]
- 方法2：from module import <name[,name2,……[,nameN]]>

## 3.模块分类
系统内置模块：sys，time，json等

第三方的开源模块：通过pip instal进行安装，有开源的代码

自定义模块：自己写的模块，对某段逻辑或某些函数进行封装后供其他函数调用

## 4.如何使用模块：

1）系统内置模块：python安装好之后自带的一些非常有用的模块（sys,os,time,json模块等）

注：
- 使用关键词“import+模块名称”导入某一个模块
- 同一个模块不管你执行了多少次“import”，只会被导入一次
- import 应该被放在代码的顶端
```
import sys
import time
print(sys.argv)
time.sleep(3)
print("exit")
```
注：sys.argv 显示绝对路径

2）第三方开源模块：

- 是通过包管理工具pip完成的。必须先知道该库的名称，可以在官网或者pypi上搜索，比如MySQL驱动程序，web框架Flask，科学技术Numpy等。

- NumPy（Numerical Python）是Python语言的一个扩展程序库，支持大量的维度数组与矩阵运算，此外也针对数组运算提供大量的数学函数库。
pip install numpy

- 安装完成之后，需要先做导入操作：
```
import numpy as np
a = np.arrange(15).reshape(3,5)
print(a)
```
注：生成一个3行5列的矩阵数组

3）自定义模块
- 自定义模块是自己写的模块，对某段逻辑或某些函数进行封装后供其他函数调用。
- 模块由变量、函数或类组成

举例：
- 创建一个模块 baidu.py
- 创建一个调用模块 index.py
- 注意：自己定义模块的名字一定不能和系统内置的模块重名，否则将不能导入系统的内置模块。例如：自定义了一个模块叫sys.py 后，那系统的sys模块就不能使用

示例1(模块、方法、类)：

1)变量
`name = "tom"`

2）方法：
```
def add(a,b):
    return a+b
```
    
3）类
```
class index():
    def sub(self,a,b):
        return a-b
        
print(name)
#调用方法
print(add(1,5))

#调用类
i = index()
print(i.sub(3,4))
```

示例2（调用模块）
```
1）百度模块的内容：
name = "Tom"
def add(a,b):
    return a+b
    
class index():
    def sub(self,a,b):
        return a-b
```
        

2）调用百度模块
```
import baidu
print(baidu.name)
print(baidu.add(4,5))
i = baidu.index()
print(i.sub(3,4))
```

3）导入被调用模块的函数：
```
import baidu
from baidu import name,add,index
print(name)
print(add(4,6))
i = index()
print(i.sub(4,7))
```

4）调用模块时引入所有函数
```
import baidu
from baidu import *
print(name)
print(add(4,6))
i = index()
print(i.sub(4,7))
```

5)调用模块时引入的函数或变量名称过长时可以起别名
```
import baidu
from baidu import name as n
print(n)
print(add(4,6))
i = index()
print(i.sub(4,7))
```

5.作用域：

搜索路径：

当你导入一个模块，python解析器对模块位置的搜索顺序是：

1）当前目录

2）如果不在当前目录，python则搜索在shell变量python下的每个目录

3）如果都找不到，python会查看默认路径。Unix下，默认路径一般为/user/local/lib/python

模块搜索路径存储在system模块的sys.path变量中。变量里包含当前目录，pythonpath和邮安装过程决定的默认目录。

6.使用模块的总结：

1）使用模块的好处：
- 提高代码的可维护性
一个模块编写完毕后，其他模块直接调用，不用再从零开始写代码了，节约了工作-时间。
- 避免函数名和变量名称重复，在不同的模块中可以存在相同名字的函数名和变量名（不要和系统内置的模块名称重复）

7.反射
- 根据字符串的形式去某个模块中寻找东西—— getattr()
- 根据字符串的形式去某个模块中判断东西是否存在——hasattr()，返回布尔值
- 根据字符串的形式去某个模块中设置东西——setattr()
- 根据字符串的形式去某个模块中删除东西——delattr()

1）示例1，例如一个login.py 文件中内容如下：
```python
def index():
    print("欢迎进入XXX系统")

def login():
    print("已登录系统")

def logout():
    print("已退出系统")
```


2）通过__import__ 导入目标模块，并且放在一个对象中
```python
f = __import__('login')

#通过对象找login模块中index的字符串并且调用

f.index()
```
3）使用getter获取 login 模块中的logout函数
```python
import login
f = getattr(login,"logout")
f()
```

4)根据字符串的形式去某个模块中判断东西是否存在——hasattr()，返回布尔值
```python
import login

obj = login.Person()

if hasattr(obj,'person_info'):
    f = getattr(obj,'person_info')
    f()
else:
    print("没找到")

```

5）删除不会真的删除模块中的字符串
```python
f0 = hasattr(login,"str1")
print("未删除之前：",f0)
f1 = delattr(login,"str1")
f2 = hasattr(login,"str1")
print("删除之后：",f2)
```

2）反射案例

![python反射](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/python%E5%8F%8D%E5%B0%84.png)

