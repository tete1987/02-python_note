# 03-python知识
## 一、python语言基础
### （一）Python历史

![python历史](https://github.com/tete1987/picture_resource/blob/master/python%E5%8E%86%E5%8F%B2.png)

### （二）Python的安装
1.官方地址下载python安装包：https://www.python.org

python安装文档（Windows系统）：https://testing-studio.com/t/topic/57/4

2.安装完成之后python会默认启动比较老的2.x版本，可使用更改链接的方式自动执行最新3.x版本。

在cmd中输入：

`ln -f /user/local/bin/python3.8 /user/local/bin/python`



3.mac或linux环境修改环境变量：
```
cd user/local/bin
PATH
vim ~/.bash_profile
```

在文件中增加：
export PATH=$PATH:/user/local/bin

4.IDE：Pycharm

1）官方地址下载pyhcharm安装包：https://www.jetbrains.com/pycharm/download

5.pip依赖管理

1）pip介绍：

- pip是python中的标准管理器。它允许你安装和管理不输入python标准库的其他软件包。

- python3的3.4版本及python2的2.7.9版本开始，pip被直接包括在python的安装包内。

- pypi托管了大量非常流行的库（www.pypi.org）。

2）安装包

pip install 报名==版本号

例：pip install selenium==2.39.0



pip install i 镜像地址 --trusted-host 镜像地址对应的host

例：

`pip3 install jupyter -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com`


国内的pip源：
- 阿里云：http://mirrors.aliyun.com/pypi/simple
- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 豆瓣：http://pypi.douban.com/simple

##  二、python基本语法
### （一）变量
1.参考文档

python官方文档：https://docs.python.org/3/tutorial/index.html

2.概念：
在程序设计中，变量是一种存储数据的载体。计算机中的变量是实际存在的数据或者说是存储数据的一块内存空间，变量的值可以被读取和修改，这是所有计算和控制的基础。

3.命名规则：

1）硬性规则：
- 变量名由字母（广义的Unicode字符，不包括特殊字符）、数字和下划线构成，数字不能开头。
- 大小写敏感
- 不要跟关键字（有特殊含义的单词）和系统保留字（如函数、模块等的名字）冲突。

2）PEP8 要求：
- 用小写字母拼写，多个单词用下划线连接。
- 受保护的实例属性用单个下划线开头。
- 私有的实例属性用两个下划线开头。

### （二）数字

1.int：整型

2.float：浮点型

3.complex：复杂型

举例：
```
int_a = 1
float_a = 2.3
complex_a = 3k

print(type(int_a))
print(type(float_a))
print(type(complex_a))
```

（三）字符串

1. \:转义符

例：
```
a = 'stringdikdkld\\n'
print(a)
print("-----")
```
由于“\”做了转义，所以结果是：
```
stringdikdkld\n
-----
```

2. r:忽略转义符的作用
```
a = r'stringdikdkld\\n'
print(a)
print("-----")
```
由于“r”做了忽略转义符处理，所以结果是：
```
stringdikdkld

-----
```

3.  `+ `以及空格: 多个字符串连接

1）举例1：
```
a = "aaaaa"
b = "bbbbb"
print(a+b)
```
"+"号可以将两个变量连接起来显示，所以结果是：
`aaaaabbbbb`

2）举例2：
`print("ccccc" "ddddd")`

空格也可以连接字符串，但是必须把字符串写全，不可用于变量，所以结果是：
`cccccddddd`

4. f+{}/format ：引用语法

1）用法1：
```
a = "aaaaa"
b = f"bbbbb{a}"
print(b)
```
结果：
`bbbbbaaaaa`


2）用法2：
```
a = "aaaaa"
b = "bbbbb{}"
print(b.format(a))
```
结果：
`bbbbbaaaaa`


3）多个引用
```
a = "aaaaaa"
b = "bbbbbb"
c = "cccccc"
d = "ddddd{}{}{}"
print(d.format(a,b,c))
```
结果：
`dddddaaaaaabbbbbbcccccc`

4）有多个引用时可使用变量进行赋值
```
a = "aaaaaa"
b = "bbbbbb"
c = "cccccc"
d = "ddddd{}{}{}"
print(d.format(x=a,y=b,z=c))
```
结果：
`dddddaaaaaabbbbbbcccccc`

### （四）列表
1.定义

list(列表)是python中使用最频繁的数据类型，在其他语言中通常就做数组。

2.索引

列表的索引从0开始，索引就是数据在列表中的位置编号，索引又称为下标。
```
list_a = [1,2,3,"ddd"."s"]
print(list_a[0])
print(list_a[1])
print(list_a[2])
print(list_a[-1])
```
注： -1 是倒数第一个元素。


### 笔记链接


- [03 Python控制流语法](https://github.com/tete1987/03-python/blob/master/03%20Python%E6%8E%A7%E5%88%B6%E6%B5%81%E8%AF%AD%E6%B3%95.md)

- [04 python函数](https://github.com/tete1987/03-python/blob/master/04%20python%E5%87%BD%E6%95%B0.md)

- [05 python常用数据结构](https://github.com/tete1987/03-python/blob/master/05%20python%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84.md)

- [06 python模块](https://github.com/tete1987/03-python/blob/master/06%20python%E6%A8%A1%E5%9D%97.md)
- [07 python输入与输出](https://github.com/tete1987/03-python/blob/master/07%20python%E8%BE%93%E5%85%A5%E4%B8%8E%E8%BE%93%E5%87%BA.md)
- [08 python错误与异常](https://github.com/tete1987/03-python/blob/master/08%20python%E9%94%99%E8%AF%AF%E4%B8%8E%E5%BC%82%E5%B8%B8.md)
- [09 面向对象编程](https://github.com/tete1987/03-python/blob/master/09%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%BC%96%E7%A8%8B.md)
- [10 Python脚本编写实战](https://github.com/tete1987/03-python/blob/master/10%20Python%E8%84%9A%E6%9C%AC%E7%BC%96%E5%86%99%E5%AE%9E%E6%88%98.md)
- [11 python标准库](https://github.com/tete1987/03-python/blob/master/11%20python%E6%A0%87%E5%87%86%E5%BA%93.md)
- [12 python多线程](https://github.com/tete1987/03-python/blob/master/12%20python%E5%A4%9A%E7%BA%BF%E7%A8%8B.md)
- [13 Python第三方库介绍](https://github.com/tete1987/03-python/blob/master/13%20Python%E7%AC%AC%E4%B8%89%E6%96%B9%E5%BA%93%E4%BB%8B%E7%BB%8D.md)
- [14 python外部数据源文件处理](https://github.com/tete1987/03-python/blob/master/14%20python%E5%A4%96%E9%83%A8%E6%95%B0%E6%8D%AE%E6%BA%90%E6%96%87%E4%BB%B6%E5%A4%84%E7%90%86.md)
- [15 pip依赖管理与虚拟环境](https://github.com/tete1987/03-python_note/blob/master/15%20pip%E4%BE%9D%E8%B5%96%E7%AE%A1%E7%90%86%E4%B8%8E%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83.md)
- [16 Unittest测试框架](https://github.com/tete1987/03-python_note/blob/master/16%20Unittest%E6%B5%8B%E8%AF%95%E6%A1%86%E6%9E%B6.md)
- [17 pytest测试框架](https://github.com/tete1987/03-python_note/blob/master/17%20pytest%E6%B5%8B%E8%AF%95%E6%A1%86%E6%9E%B6.md)
- [18 参数化用例](https://github.com/tete1987/03-python_note/blob/master/18%20%E5%8F%82%E6%95%B0%E5%8C%96%E7%94%A8%E4%BE%8B.md)
- [19 Python数据驱动](https://github.com/tete1987/03-python_note/blob/master/19%20Python%E6%95%B0%E6%8D%AE%E9%A9%B1%E5%8A%A8.md)
- [20 Allure测试框架](https://github.com/tete1987/03-python_note/blob/master/20%20Allure%E6%B5%8B%E8%AF%95%E6%A1%86%E6%9E%B6.md)
