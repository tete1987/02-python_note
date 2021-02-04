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

![pyhton-软连接](https://github.com/tete1987/picture_resource/blob/master/pyhton-%E8%BD%AF%E8%BF%9E%E6%8E%A5.png)


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

![python-安装selenium](https://github.com/tete1987/picture_resource/blob/master/python-%E5%AE%89%E8%A3%85selenium.png)

pip install i 镜像地址 --trusted-host 镜像地址对应的host

例：

`pip3 install jupyter -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com`


国内的pip源：
- 阿里云：http://mirrors.aliyun.com/pypi/simple
- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 豆瓣：http://pypi.douban.com/simple


### 笔记链接

- [02 python基本语法](https://github.com/tete1987/03-python/blob/master/02%20python%E5%9F%BA%E6%9C%AC%E8%AF%AD%E6%B3%95.md)

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
