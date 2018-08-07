# 异常捕获

### try

```
try:
   pass
except BaseException as e:
    print('except', e)
finally:
    pass
```

python的所有错误都继承自`BaseException`。

如果错误没有被捕获，它就会一直往上抛出，最后被Python解释器捕获。

### Log日志

python内置logging模块记录错误信息。

```
import logging
try:
    pass
except BaseException as e:
    logging.exception(e)
```

### 抛出异常

python使用`raise`关键字抛出异常。

```
raise BaseException('错误信息')
```

# 调试

### 断言

```
assert n != 0, 'n is zero'
```

断言失败会抛出`AssertionError`。

### Logging

logging添加一些配置

```
logging.baseConfig(level=logging.INFO)
```

logging有\`debug, info, waring, error等几个级别

### pdb

这种方式类似于IDE的断点调试，不再赘述

# 单元测试

### 编写单元测试

编写单元测试我们需要引入python自带的`unittest`模块。

```
import unittest

class Test(unittest.TestCase):
    def test_1(self):
        pass
```

 编写测试类需要从`unittest.TestCase`继承，以`test`开头才被认为是测试方法，不以`test`开头的方法不被认为是测试方法，测试的时候不被执行

### 运行单元测试

```
if __name__ == '__main__':
    unittest.main()
```

# 文档测试























