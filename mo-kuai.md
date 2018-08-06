模块类似于java的分包分文件处理。

任何模块代码的第一个字符串都被视为模块的文档注释。

一个标准的python模块如下：

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

' 文档注释 '

__author__ = '作者'

import sys #导入模块

def test():
    pass
    
if __name__=='__main__':
    test()
```

> 当我们在当前模块文件运行时，python解释器将\_\_name\_\_置位\_\_main\_\_，如果在其他模块运行当前文件，if判断就会失败。



