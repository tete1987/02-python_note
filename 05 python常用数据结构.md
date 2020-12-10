# 五、python常用数据结构
## （一）列表
### 1.定义
- Python中可以通过组合一些值得到多种复合数据类型。

- 列表是其中最常见的数据结构。

- 列表通过方括号、逗号分隔的一组值得到。

- 一个列表可以包含不同类型的元素，但通常使用时各个元素类型相同。

### 2.特性：
1）list.append(x):

在列表的末尾添加一个元素。相当于a[len(a):]=[x]

2）list.insert(i,x):在给定的位置插入一个元素。

第一个参数是要插入的元素的索引，以a.insert(0，x)插入列表头部，a.insert(len(a),x)等同于a.append(x)。

3）list.remove(x):移除列表中第一个值为x的元素。如果没有这样的元素，则抛出ValueErro异常。

4）list.pop([i]):删除列表中给定位置的元素并返回它。如果没有给定位置，a.pop()将会删除并返回列表中的最后一个元素。

5）list.sort(key=None,reverse=False):对列表中的元素进行排序（参数可用于自定义排序，解释请参考sorded()）。

6）list.reverse():反正列表中的元素。

7）list.clear():删除列表中所有的元素。相当于del.a[:]。

8）list.extend(ierable):使用可迭代对象中的所有元素来扩展列表。相当于a[len(a):]=iterable

9）list.index(x[,start[,end]]):返回列表中第一个值为x的元素的从零开始的索引。如果没有这样的元素将会抛出ValueError 异常。
可选参数start和end 是切片符号，用于将搜索限制为列表的特定子序列。返回的索引是相对于整个序列的开始计算的，而不是start参数。

10）list.count(x):返回元素x在列表中出现的次数。

11）list.copy():返回列表的一个浅拷贝，相当于a[:]

注：insert ，remove或者sort方法，只修改列表，没有打印出返回值——它们返回默认值None。这是Python中所有可变数据结构的设计原则，并非所有数据或可以排序或比较（字符串和数字等）。

示例：
```
1）append用法
list1 = [1,2,3]
list1.append(0)
list1.append(1)
print(list1)

2）pop用法
list1 = [1,2,3]
y= list1.pop()
print(list1)
print(y)

3）sort用法
list1 = [1,4,8,0]
list1.sort(reverse=true)
print(list1)
```
注：reverse是反转，先使用sort进行排序，再用reverse表明是降序排序。

### 3.列表推导式
1）概念：列表推导式提供了一个更简单的创建列表的方法。

常见的用法是把某种操作应用于序列或可迭代对象的每个元素上，然后使用其结果来创建列表，或者通过满足某些特定条件元素来创建子序列。

练习：

如果我们想生成一个平方列表，比如[1,4,9]，使用for循环应该怎么写，使用列表生成式又应该怎么写呢？

1）普通模式：
```
list_square = []
for i in range(4):
    list_square.append[i**2]
print(list_square)    
```

2）列表推导式模式：
```
list_square = [i**2 for i in range(1,4)]
print(list_square)
```


4.切片

1）要创建切片，可指定要使用的第一个元素和最后一个元素的索引。

与函数range() 一样，python在到这第二个索引之前的元素后停止。

例：
```
players = ['charles','martina','micheal','florence','eli']
print(players[0:3])
```
打印结果：
`['charles','martina','micheal']`

2）直接指定一个索引，表明从[0]开始到索引的位置，如：players[:3]，输出结果为索引值为0，1，2的值，即：['charles','martina','micheal'] 。

3）可使用负数，输出列表倒数的值，如：players[-3:] ,其结果为输出列表倒数三位，即：['micheal','florence','eli']

4）复制列表：如果什么都不写，只有“：”，则表明生成整个列表的副本。

示例：
```
my_foods =['pizza','falafei','carrot cake']
friend_food = my_foods[:]

my_foods.append('icecream')
friend_food.append('apple')

print(my_foods)
print(friend_food)
```
注：此处不可直接使用 friend_food =my_foods,这样的话表明将 my_food赋值给了 friend_food，它们就变成一样的数据了。

## （二）元组
### 1.定义
- 元组使用()进行定义
- tuple、list、range都是序列数据类型。
- 元素不可变的，可以通过解包、索引来访问。
- 
示例1(元组的定义）：
```
tuple1 = (1,2,3)
tuple2 = 1,2,3

print("tuple1元组：",tuple1)
print("tupple元组的类型是：",type(tuple1))

print("tuple2元组：",tuple2)
print("tuple2元组的类型是：",type(tuple2))
```

示例2（元组中嵌套列表）：
```
a = [1,3,5]
tuple_a = (2,5,a)
print(id(tuple_a[2]))
#修改元组中的列表的值：
tuple_a[2][2]=6
print(tuple_a)
#可以查看到虽然值变了，但在元组中的id值并没有改变
print(id(tuple_a[2]))
```

示例3（计数：元组中出现的元素个数）
```
a = (1,4,6,"a",35,"a")
print(a.count("a"))
```

示例4（返回元组中元素的索引位置）：
```
a = (1,5,3,6)
print(a.index(3))
```

## （三）集合
### 1.定义
- 集合是由不重复元素组成的无序的集
- 它的基本用法包括成员检测和消除重复元素
- 可以使用{}或者set() 函数创建集合
- 要创建一个空集合只能用set() 而不能使用{}

示例1（集合定义）：
```
a = {1}
b = set()
print(type(a))
print(type(b))
```

示例2（交集、并集、不同）:
```
a ={1,4,5,6}
b = {7,4}
print(a.union(b))
#取交集：
print(a.intersection(b))
#取a中有，b中没有的值
print(a.difference(b))
```

示例3（在集合中添加值）
```
a = {1,3,45}
b = {3,6,78,8}
a.add("f")
print(a)
```

示例4：
```
1）得到一个去重之后的集合：
print({i for i in "safdafafaekklldlldld"})

2）或第二种写法：
c = "safdafafaekklldlldld"
print(set(c))
```

## （四）字典
### 1.定义：
- 字典是以【关键字】为索引
- 关键字可以是任意不可变类型，通常是字符串或数字。如果一个元组只包含字符串、数字或元组，那么这个元组也可以用作关键字。

示例1（元组的定义）：
```
dict1 = {"a":1,"b":2}
dict2 = dict(a=1,b=2)
print(type(dict1))
print(dict1)
print(type(dict2))
print(dict2)
```

示例2（取出字典中的key值和value值）：
```
a = {"a":1,"b":2}
b = dict(a=1,b=2)
print(a.keys())
print(a.values())
```

示例3（删除字典中的某值）：
```
a = {"a":1,"b":2,"c":4}
print(a.pop("b"))
print(a)
```

示例4（随机删除一个键值）：
```
a = {"a":1,"b":3,"c":5}
print(a.popitem())
print(a)
```

示例5（将列表中的元素当做key值创建新的字典）：
```
a = {}
b = a.fromkeys([1,4,5,"f"])
print(b)
```

示例6（字典推导式）：
```
print({ i for i in range(1,5)})
```
