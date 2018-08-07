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



