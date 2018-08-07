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

