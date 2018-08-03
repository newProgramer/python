# 切片

```
list = [0,1,2,3,4,5,6,7,8,9]
list[0:3] #获取索引为0,1,2的元素
list[:3] #上面的简写
list[1:3] #获取索引为1,2的元素
list[-1] #获取最后一个元素
list[-3:-1] #获取最后三个元素
list[-3:] #上面的简写
list[:5:2] #前5个数，每2个取一个
list[:] #原样复制一个list
```

tuple也可以用切片操作，只是操作的结果仍是tuple

字符串也可以看做list使用切片操作，其结果仍是字符串

# 迭代

python的迭代是通过`for...in`操作来完成的

```
dict={'key1':'value1', 'key2':'value2'}
for key in dict:
    pass
```

如果要迭代dict的value可以使用`for value in dict.values()`,

如果要同时迭代key,value可以使用`for k,v in dict.items()`

由于字符串也可以看做list，因此也可以用于迭代，例如：

```
for ch in 'abc':
    pass
```

###### 判断是否是可迭代对象

```
from collections import Iterable
isinstance('abc', Iterable)
```

### 带索引的迭代

python内置的`enumerate`函数可以把一个list变成索引-元素对，例如：

```
for index, value in enumerate('abc'):
    pass
```

# 列表生成式

是python内置的简单却又强大的用来创建list的生成式。

```
range(1,6) #生成[1,2,3,4,5]
[x * x for x in range(1,6)] #生成[1,4,9,16,25]
[x * x for x in range(1,6) if x%2 == 0] #生成[4,16]
[m + n for m in 'AB' for n in 'XY'] #两次循环生成['AX', 'AY', 'BX', 'BY']
```

列表生成式可以使用两个变量来生成list：

```
dict = {'a':'x', 'b':'y'}
[k + ':' + v for k, v in dict.items()] #生成['a:x', 'b:y']
```

将list中的所有字符串变成小写

```
L = ['A', 'B', 'C']
[s.lower() for s in L] #生成['a', 'b', 'c']
```

# 生成器

在循环的过程中不断推算出后续元素，用多少推算多少，不必生成完整的list，从而节省大量空间。

```
g = (x*x for x in range(10))
print(next(g)) #打印生成器的下一个元素
for n in g: #使用迭代器遍历g的元素
    pass
```

每次调用`next(g)`的时候，就计算出`g`的下一个元素的值，直到计算到最后一个元素没有更多的元素时，抛出`StopIteration`的错误。for循环迭代不需要关心`StopIteration`错误。

generator如果推算的算法比较复杂还可以使用函数实现，例如斐波那契数列，除第一个数和第二个数外，任意一个数都可以由前两个数相加得到：

1,1,2,3,5,8,13,21...

```
def fib(max):
   n,a,b = 0,0,1
   while n < max:
       print(b)
       a,b = b, a+b
       n = n + 1
   return 'done'
```

将上述函数改造成generator只需要把`print(b)`改为`yield b`就行了。

```
def fib(max):
   n,a,b = 0,0,1
   while n < max:
       yield b
       a,b = b, a+b
       n = n + 1
   return 'done'
```

> 注意：generator函数不再是顺序执行到return返回，而是每次调用`next()`的时候执行，遇到`yield`语句返回，再次执行时从上次返回的`yield`语句处继续执行
>
> 用`for`循环调用generator时，发现拿不到generator的`return`语句的返回值。如果想要拿到返回值，必须捕获`StopIteration`错误，返回值包含在`StopIteration`的`value`中





































