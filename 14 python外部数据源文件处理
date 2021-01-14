## 十四、python外部数据源文件处理
1.简介：

Yaml是一个可读性高，用来表达数据序列化的格式，常常作为配置文件使用。

Json是一个轻量级的数据交换语言，该语言以易于让人阅读的文字为基础，用来传输由属性值或者序列性的值组成的数据对象。
Excel有直观的界面、出色的计算功能和图表工具是一款电子制表软件。

## （一）Yaml
1.Yaml的读写

1）PyYaml的常用方法：https://pypi.org/project/PyYAML/
- yaml.load：将yaml格式转换为python格式
- yaml.dump：将python格式转换为yaml

2）yaml.load 将yaml格式转换为python格式

示例1：
```PYTHON
#1)直接打印时会有红字提醒，如果想去掉红字，可以加一个Loader，返回列表格式
print(yaml.load("""
- Hesperiidea
- Papilionidea
""",Loader=yaml.FullLoader))
```

示例2：
```PYTHON
#2）如果想返回字典，则使用以下方式：
print(yaml.load("""
a: 1
""",Loader=yaml.FullLoader))
```

示例3（打印文件中的内容）：
```PYTHON
先创建一个demo.yaml文件
-
  - Hello
-
  - World
  - a: 1
    b: 2
```

打印demo.yaml文件里的内容
```PYTHON
print(yaml.load(open("demo.yaml"),Loader=yaml.FullLoader))
```

3)yaml.dump ,将python格式转换为yaml

示例1：
```PYTHON
print(yaml.dump({'a':[1,2]}))
```

示例2（使用yaml.dump 写入一个文件）：
```PYTHON
with open("demo1.yml","w") as f:
    yaml.dump(data={'a':[1,2],'b':3},stream=f)
```

## （二）Json

1.json库:http://docs.python.org/3/library/json.html

## （三）Excel

1.相关介绍：http://www.python-excel.org/

2.格式：
- xlrd
- xlwt
- Xlutils
- operpyxl:http://openpyxl.readthedocs.io/en/stable

![json](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/json.png)

示例：
```python
from openpyxl import Workbook
from openpyxl import load_workbook
from openpyxl import Workbook
from openpyxl.utils import get_column_letter

wb = Workbook()

dest_filename = 'empty_book.xlsx'

ws1 = wb.active
#表的sheet页签名称
ws1.title = "range names"

for row in range(1, 40):
    ws1.append(range(600))
#创建第二个页签，名称是pi
ws2 = wb.create_sheet(title="Pi")

ws2['F5'] = 3.14

ws3 = wb.create_sheet(title="Data")
for row in range(10, 20):
    for col in range(27, 54):
       _ = ws3.cell(column=col, row=row, value="{0}".format(get_column_letter(col)))
print(ws3['AA10'].value)

wb.save(filename = dest_filename)


wb = load_workbook(filename = 'empty_book.xlsx')
sheet_ranges = wb['range names']
print(sheet_ranges['D18'].value)
for i in range(1,3):
    print(sheet_ranges.cell(column=1,row=i).value)


```
