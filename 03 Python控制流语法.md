# 三、Python控制流语法
## （一）分支结构
### 1.概念：
- 一条一条语句顺序执行叫做顺序结构
- 分支结构就是在某个判断条件后，选择一条分支去执行

![python分支结构1](https://github.com/tete1987/picture_resource/blob/master/python%E5%88%86%E6%94%AF%E7%BB%93%E6%9E%841.png)

## （二）python的分支结构
### 1.关键字
### 1）if   elif  else
```
if 判断条件1：
   执行语句1 ……
else：
   执行语句2……
```

![python分支结构2](https://github.com/tete1987/picture_resource/blob/master/python%E5%88%86%E6%94%AF%E7%BB%93%E6%9E%842.png)


示例：
```
a = 1
if a == 0:
   print("a=0")
else:
   print("a不等于0")
```

2）缩进:如果if条件成立的情况下需要执行多条语句，只要保持多条语句具有相同的缩进就可以了。

3）多重分支
```
if 判断条件1：
    执行语句1……
elif 判断条件2：
    执行语句2……
elif判断条件3：
    执行语句3……
```

示例：
```
a = 9 
if a == 0:
   print("a=0")
elif a == 1:
   print("a=1")
elif a == 2:
    print("a=2")
else:
    print("a不等于0，1，2")
```

4）分支嵌套：
```
if 判断条件1：                               
   if 判断条件2：
       执行语句2……
    else：
       执行语句3……
else：
   执行语句4……     
```
![python分支结构3](https://github.com/tete1987/picture_resource/blob/master/python%E5%88%86%E6%94%AF%E7%BB%93%E6%9E%843.png)

练习题：分别使用分支嵌套以及多重分支去实现分段函数求值。

分段函数求值：
```
3*x-5（x>1）
f(x)=x+2(-1<=x<=1)
5*x+3(x<-1)
```
解题思路：
```
x>1 时执行 3*x-5
-1<=x<=1  时执行 x+2
x<-1时执行 5*x+3
```
实战：

1）写法1：
```
x=9
if x > 1:
    y = 3*x-5
elif -1 <= x <= 1:
    y = x +2
else:
    y = 5*x +3
   
print(y)  
```

2）写法2：
```
x=0
if x > 1:
    y = 3*x -5
    print(y)
else:
    if x < -1:
       y = 5*x +3
    else:
       y = x+2
print(y)          
```

python之禅中有这么一句话“Flat is better than nasted”。之所以提倡代码“扁平化”是因为嵌套层次多了之后会严重的影响代码的可读性。所以能使用扁平化的结构时不要使用嵌套。

## （三）循环结构
### 1.概念：
- 循环语句允许我们执行一个语句或语句组多次。
- python提供了for循环和while循环
- 下图是大多数变成语言中的循环语句的一般形式。
- 
![python分支结构4](https://github.com/tete1987/picture_resource/blob/master/python%E5%88%86%E6%94%AF%E7%BB%93%E6%9E%844.png)

### 2. for-in 循环
如果明确的知道循环执行的次数或者要对一个容器进行迭代（后面会讲到），那么我们推荐使用for-in 循环。

1）range函数
- range可以用来产生一个不变的数值系列，而且这个序列通常都是用在循环中的
- range(101)可以产生一个0-100的整数序列。
- range（1，100）可以产生一个1-99的整数序列。
- range（1，100，2）可以产生一个1-99的奇数序列，其中的2 是步长。

练习题：

1.计算1-100求和
```
result = 0
for i in ragne(1,101):
    print(i)
    result = result + i
print(result)    
```


![python-debug](https://github.com/tete1987/picture_resource/blob/master/python-debug.png)

2.加入分支结构实现1-100之间的偶数求和
```
result = 0
for i in range(1,101):

    if i % 2 == 0:
        print(i)
        result = result + i

print(result)
```

3.使用python实现1-100之间的偶数求和
```
result = 0
for i in range(1,100,2):
    print(i)
    result = result +i
print(result)
```

### 3. while 循环
如果要构造不知道具体循环次数的循环结构，我们推荐使用while循环。while循环通过一个能够产生或转换出bool值的表达式来控制循环，表达式的值为true循环继续，表达式的值为false循环结束。

while循环使用else语句：
```
count = 0
while count <5:a print(count,"小于5")
    count = count +1 
else:
    print(count,"大于或等于5")

```
示例：
```
a = 1
while a ==1:
    print("a=1")
    a = a+1
else:
    print("a != 1")
    print(a)
```
结果：
```
a=1
a != 1
2
```

1）break 和continue 语句
- break语句：可以跳出for和while的循环。如果你从for 或 while循环中终止，任何对应的循环else块将不执行。
- continue语句：被用来告诉pyhton跳过当前循环中的剩余语句，然后继续进行下一轮循环。

练习题：

1.猜数字游戏
- 计算机出一个1-100之间的随机数由人来猜
- 计算机根据人猜的数字分别给出“大一点、小一点、猜对了”等提示

解题思路：

1.先定义一个变量与计算机的随机数进行比对大小

2.将该变量变成人为可输入模式。
```

import random 

comuter_number = random.randint(1,100)

while True:
    person_number = int(input("请输入一个随机数"))
    if person_number > comuter_number:
        print("小一点")
    elif person_number < comuter_number:
        print("大一点")
    else:
        print("猜对啦")
        break

```
