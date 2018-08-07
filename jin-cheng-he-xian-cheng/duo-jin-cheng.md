# 多进程

在linux系统中有一个`fork()`函数，调用一次返回两次，因为操作系统把父进程复制一份称为子进程，分别在父进程和子进程中返回。父进程返回子进程PID，子进程永远返回0。

python的`os`模块封装了常见的系统调用。

```
import os
pid = os.fork()
if pid == 0:
    print('I am child process ')
else:
    print('I am create child process')
```

> 注意： 由于Windows没有fork调用，以上代码无法再Windows环境下运行

### multiprocessing

由于python是跨平台的，自然提供了一个跨平台的多进程支持。`multiprocessing`模块就是跨平台的多进程支持模块。

`multiprocessing`模块提供了一个`Process`类来代表一个进程对象。

```
from multiprocessing import Process
import os

# 子进程要执行的代码
def run_proc(name):
    print('Run child process %s (%s)...' % (name, os.getpid()))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Process(target=run_proc, args=('test',)) #创建进程实例
    print('Child process will start.')
    p.start() #启动进程
    p.join() #等待子进程结束后再继续运行
    print('Child process end.')
```

### Pool

创建大量子进程使用进程池的方式。

```
pool = Pool(4) 创建进程池实例，最多同时跑4个进程
for i in range(5):
    pool.apply_async(子进程执行方法, args(i,))
p.close() #调用join之前必须调用close，调用close之后就不能添加新的Process了
p.join() #对pool调用join方法会等待所有子进程执行完成
```

pool的大小默认是cpu的核数。

