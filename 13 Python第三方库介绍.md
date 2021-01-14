# 十三、Python第三方库
## （一）pytest
1.安装：
```pip install pytest```


## （二）request
1.安装：
```pip install request```

2.导入并使用，示例：
```python
import request
r = request.get("http://www.baidu.com")
r.status_code
#返回编码
r.encoding
#返回结果
r.text
```

在pycharm中也可查看是否导入成功：

![pytest](https://github.com/tete1987/picture_resource/blob/master/python%E5%9B%BE/pytest1.png)

示例：
```python
import requests
r = requests.get("http://www.baidu.com")
print(r.status_code)
print(r.encoding)
print(r.text)
```

如果用post，则需要传入参数：
```python
import requests

r = requests.post('http://httpbin.org/post',data= {'key':'value'})
print(r.status_code)
print(r.encoding)
print(r.text)
```
