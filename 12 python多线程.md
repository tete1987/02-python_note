# 十二、python多线程
## （一）概念
1.什么是进程
- 进程是执行中的程序
- 拥有独立地址空间、内存、数据栈等
- 操作系统管理
- 派生（fork 或spawn）新进程
- 进程间通信（IPC）方式共享信息

2.什么是线程
- 同进程下执行，并共享相同的上下文
- 线程间的信息共享和通信更加容易
- 多线程并发执行
- 需要同步原语

## （二）python与线程
1.解释器主循环
- 主循环只有一个线程在执行
- 使用全局解释器锁（GIL）

2.两种线程管理：

1）_thread:提供了基本的线程和锁

2）threading：提供了更高级别、功能更全面的线程管理
- 支持同步机制
- 支持守护线程	

3. _thread 模块

<table><tbody>
    <tr>
        <th colspan="2" >函数/方法</th>
        <th colspan="2">描述</th>
    </tr>
    <tr>
        <th colspan="4">thread 模块的函数</th>
    </tr>
    <tr>
        <td colspan="2">start_new_thread(function,args,kwargs=None)</td>
        <td colspan="2">派生一个新的线程，使用给定的args 和可选的kwargs 来执行 function</td>
    </tr> 
    <tr>
        <td colspan="2">allocate_lock()</td>
        <td colspan="2">分配LockType 锁对象</td>
    </tr>
    <tr>
        <td colspan="2">exit()</td>
        <td colspan="2">给线程退出指令</td>
    </tr>
    <tr>
        <th colspan="4">LockType 锁对象的方法</th>
    </tr>
    <tr>
        <td colspan="2">acquire(wait=None)</td>
        <td colspan="2">尝试获取锁对象</td>
    </tr>
    <tr>
        <td colspan="2">locked()</td>
        <td colspan="2">如果获取了锁对象则返回True，否则，返回False</td>
    </tr>
    <tr>
        <td colspan="2">release()</td>
        <td colspan="2">释放锁</td>
    </tr>
</table>

4.threading模块

|对象 |描述|
|--|--|
|Thread| 表示一个执行线程的对象|
|Lock| 锁原语对象（和thread模块中的锁一样）|
|RLock |可重入锁对象，使单一线程可以（再次）获得已持有的锁（递归锁）|
|Condition |条件变量对象，使得一个线程等待另一个线程满足特定的“条件”，比如改变状态或某个数据值|
|Event| 条件变量的通用版本，任意数据的线程等待某个事件的发生，在该事件发生后所有线程将被激活|
|Semaphore |为线程间共享的有限资源提供了一个“计数器”，如果没有可用资源时会被阻塞|
|BoundedSemaphore |与Semaphore相似，不过它不允许超过初始值|
|Timer| 与Thread相似，不过它要在运行前等待一段时间|
|Barrier |创建一个“障碍”，必须达到指定数量的线程后才可以继续|

5.Thread类1
<table><tbody>
    <tr>
        <th colspan="2" >属性</th>
        <th colspan="2">描述</th>
    </tr>
    <tr>
        <th colspan="4">thread 对象数据属性</th>
    </tr>
    <tr>
        <td colspan="2">name</td>
        <td colspan="2">线程名</td>
    </tr> 
    <tr>
        <td colspan="2">ident</td>
        <td colspan="2">线程的标识符</td>
    </tr>
    <tr>
        <td colspan="2">deamon</td>
        <td colspan="2">布尔标志，表示这个线程是否是守护线程</td>
    </tr>
    <tr>
        <th colspan="4">thread 对象方法</th>
    </tr>
    <tr>
        <td colspan="2">__init__(group=None,target=None,name=None,args=(),kwargs={},verbose=None,deamon=None)</td>
        <td colspan="2">实例化一个线程对象，需要有一个可调用的target，以及其参数args或kwargs。还可以传递name或group参数，不过后者还未实现。此外，verbose标志也是可接受的，而deamon的值将会设定thread.deamon属性/标志</td>
    </tr>
</table>

6.Thread类2
|属性| 描述|
|--|--|
|start() |开始执行线程|
|run() |定义线程功能的方法（通常在子类中被应用开发者重写）|
|join(timeout=None)| 直至启动的线程终止之前一直挂起；除非给出了timeout（秒），否则会一直阻塞|
|getName() |返回线程名|
|setName() |设定线程名|
|isAlivel / is_alive() |布尔标志，表示这个线程是否还存活|
|isDeamon() |如果是守护线程，则返回True；否则，返回FALSE|
|setDeamon(deamonic) |把线程的守护标志设定为布尔值| |deamonic|（必须在线程start()之前调用）|


示例1（先理解线程的概念）：
```python
import _thread
import logging
from time import sleep,ctime

'''
logging.basicConfig(**kwargs)函数用于指定“要记录的日志级别”、
“日志格式”、“日志输出位置”、“日志文件的打开模式”等信息
创建一个level=logging.INFO级别的日志
'''
logging.basicConfig(level=logging.INFO)
#ctime 表示当前时间
def loop0():
    logging.info("start loop0 at"+ctime())
    sleep(4)
    logging.info("end loop0 at"+ctime())

def loop1():
    logging.info("start loop1  at" + ctime())
    sleep(2)
    logging.info("end loop1 at " + ctime())

def main():
    logging.info("start all at "+ctime())
    loop0()
    loop1()
    logging.info("end all at "+ctime())

if __name__ == '__main__':
    main()
```

示例2（添加_thread）：
```python
import _thread
import logging
from time import sleep,ctime

'''
logging.basicConfig(**kwargs)函数用于指定“要记录的日志级别”、
“日志格式”、“日志输出位置”、“日志文件的打开模式”等信息
创建一个level=logging.INFO级别的日志
'''
logging.basicConfig(level=logging.INFO)

def loop0():
    logging.info("start loop0 at"+ctime())
    sleep(4)
    logging.info("end loop0 at"+ctime())


def loop1():
    logging.info("start loop1  at" + ctime())
    sleep(2)
    logging.info("end loop1 at " + ctime())

def main():
    logging.info("start all at "+ctime())
    _thread.start_new_thread(loop0,())
    _thread.start_new_thread(loop1,())
    sleep(6) #所有线程的总和
    logging.info("end all at "+ctime())

if __name__ == '__main__':
    main()

```
示例3（加锁,优化代码，使其自动判断子线程所需时间，并释放锁）：
```python
import _thread
import logging
from time import sleep,ctime

'''
logging.basicConfig(**kwargs)函数用于指定“要记录的日志级别”、
“日志格式”、“日志输出位置”、“日志文件的打开模式”等信息
创建一个level=logging.INFO级别的日志
'''
logging.basicConfig(level=logging.INFO)

def loop(nloop,nsec,lock):
    #需要对nloop转格式
    logging.info("start loop"+str(nloop)+" at "+ctime())
    sleep(nsec)
    logging.info("end loop"+str(nloop)+ " at "+ctime())
    lock.release()

loops=[2,4]
def main():
    logging.info("start all at "+ctime())
    locks = []
    nloops = range(len(loops))
    for i in nloops:
        lock = _thread.allocate_lock()
        lock.acquire()
        locks.append(lock)
    for i in nloops:
        _thread.start_new_thread(loop,(i,loops[i],locks[i]))
    for i in nloops:
        while locks[i].locked():pass

    logging.info("end all at "+ctime())


if __name__ == '__main__':
    main()
```

示例4（优化代码，增加 threading 方法）：
```python
import _thread
import threading
import logging
from time import sleep,ctime

'''
logging.basicConfig(**kwargs)函数用于指定“要记录的日志级别”、
“日志格式”、“日志输出位置”、“日志文件的打开模式”等信息
创建一个level=logging.INFO级别的日志
'''
logging.basicConfig(level=logging.INFO)
def loop(nloop,nsec):
    #需要对nloop转格式
    logging.info("start loop"+str(nloop)+" at "+ctime())
    sleep(nsec)
    logging.info("end loop"+str(nloop)+ " at "+ctime())

loops=[2,4]
def main():
    logging.info("start all at "+ctime())
    threads = []
    nloops = range(len(loops))
    for i in nloops:
        t = threading.Thread(target=loop,args=(i,loops[i]))
        threads.append(t)
    for i in nloops:
        threads[i].start()
    for i in nloops:
        #如果有线程在时会阻塞主线程
        threads[i].join()

    logging.info("end all at "+ctime())

if __name__ == '__main__':
    main()
```

示例5（继承threading类）：
```python
import _thread
import threading
import logging
from time import sleep,ctime

'''
logging.basicConfig(**kwargs)函数用于指定“要记录的日志级别”、
“日志格式”、“日志输出位置”、“日志文件的打开模式”等信息
创建一个level=logging.INFO级别的日志
'''
logging.basicConfig(level=logging.INFO)

class MyThread(threading.Thread):
    def __init__(self,func,args,name=''):
        threading.Thread.__init__(self)
        self.func =func
        self.args = args
        self.name = name
    def run(self):
        self.func(*self.args)

def loop(nloop,nsec):
    #需要对nloop转格式
    logging.info("start loop"+str(nloop)+" at "+ctime())
    sleep(nsec)
    logging.info("end loop"+str(nloop)+ " at "+ctime())

loops=[2,4]
def main():
    logging.info("start all at "+ctime())
    threads = []
    nloops = range(len(loops))
    for i in nloops:
        t = MyThread(loop,(i,loops[i]),loop.__name__)
        threads.append(t)
    for i in nloops:
        threads[i].start()
    for i in nloops:
        #如果有线程在时会阻塞主线程
        threads[i].join()

    logging.info("end all at "+ctime())


if __name__ == '__main__':
    main()
```
