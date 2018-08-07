# 文件读写

### 读文件

```
f = open('path', 'r')
f.read()
```

标识符`r`表示以读的方式打开文件。

如果文件不存在就抛出`IOError`异常。

调用`read()`方法读取文件。

由于每次打开文件之后都需要调用`close()`方法去关闭文件，这种方式太麻烦，python引入了`with`来自动关闭文件。

```
with open('path', 'r') as f:
    print(f.read())
```

`read()`方法会一次性读取全部文件内容，如果文件太大就会爆掉内存。所以可以反复调用`read(size)`方法读取内容。`readline()`方法每次读取一行，`readlines()`读取所有内容并按行组装成`list`。

### 二进制文件

前面讲的是读取utf-8格式的文本文件，要读取二进制文件用`rb`模式打开文件即可：

```
with open('path', 'rb') as f:
    pass
```

### 字符编码

读取非utf-8格式的文本文件需要给`open()`函数传入`encoding`参数。

```
with open('path', 'r', encoding='gbk') as f:
    pass
```

遇到编码不规范的文件，python会抛出`UnicodeDecodeError`。遇到这种情况，`open()`函数还可以接收`errors`参数，表示遇到编码错误如何处理。

```
with open('path', 'r', encoding='gbk', errors='ignore') as f:
    pass
```

### 写文件

写文件传入的标识符是`w`或`wb`表示写文本文件或二进制文件，`a`追加模式

```
with open('path', 'w') as f:
    f.write('Hello World')
```

要写入特定编码就传入`encoding`参数即可。

> w会直接覆盖文件， a在文件末尾追加

更多信息参考[https://docs.python.org/3/library/functions.html\#open](https://docs.python.org/3/library/functions.html#open "官方文档")

# 内存读写

### StringIO

在内存中读写str。

```
from io import StringIO
f = StringIO()
f.write('hello')
print(f.getvalue)
```

`getvalue()`方法用于获得写入的str,除此之外StringIO也可以像读写文件一样操作

### BytesIO

在内存中读写二进制。

```
from io import BytesIO
f = BytesIO()
f.write('中文'.encode('utf-8'))
print(f.getvalue())
```

BytesIO和StringIO也可以像读写文件一样操作。

# 操作文件和目录

操作文件和目录的函数一部分在`os`模块中，一部分在`os.path`中。

```
os.path.abspath('.') #查看当前目录的绝对路径
os.path.join('parent', 'dir') #在目录下创建一个新目录，返回新目录的完整路径
os.mkdir('path') #创建一个新目录
os.rmdir('path') #删除一个目录
os.path.split('path') #拆分最后一个目录或文件与之前的目录
os.path.splitext('path') #获取文件的扩展名
os.rename('old', 'new') #重命名文件
os.remove('path') #删除文件
```

复制函数在`shutil`模块中`copyfile()`。

###### 过滤文件夹

```
[x for x in os.listdir('.') if os.path.isdir(x)]
```

# 序列化

python提供`pickle`模块实现序列化。

```
import pickle
pickle.dumps(object) #序列化任何对象为bytes
pickle.dump(object,file) #序列化对象写入一个file-like Object
pickle.loads(bytes) #反序列化出对象
pickle.load(file) #从file-like Object中反序列化出对象
```

# Json

python内置了`json`模块提供python对象和Json格式之间的转换。

```
import json
json.dumps(object) #将对象转换成json字符串
json.dump(object, file) #将对象转换成json字符串并写入file-like object
json.loads(json) #将json转换成object
json.load(file) #读取文件获取json并转换成对象
```

> 注意：class对象无法直接转换成json对象，必须实现一个类到dict对象的转换方法，通过dumps调用才能转换成json
>
> ```
> class Student(object):
>     def student2dict(self):
>         return {'name': self.name}
> json.dumps(student, default=student2dict)
>
> 偷懒方式
> json.dumps(student, default=lambda obj:obj.__dict__)
> ```
>
> 同理，json转换成class对象也需要先转换成dict，然后转换成对象





















































