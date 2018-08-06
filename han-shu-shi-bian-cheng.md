# 高阶函数

### 变量可以指向函数

```
abs(-10)  # 10
x = abs
x(-10)  # 10
```

> 变量可以指向函数，函数也可以当做变量名，但是因此函数便不可以使用了

### 传入函数

既然变量可以指向函数，函数的参数能接收变量，那么一个函数就能作为另一个函数的参数，这种函数称之为高阶函数。

```
def calculator(x,y,f):
    return f(x,y)
def add(x, y):
    return x + y

calculator(1,2,add) # 3
```

### Map/Reduce

map/reduce简单来说就是由master分发任务，map组合形成key-value，reduce负责接收具有相同key的key-value对进行处理。

#### map

map\(\)函数接收两个参数，一个是函数，一个是`Iterable`，`map`将传入的函数依次作用到序列的每个元素，并返回新的`Iterable`。例如：

```
def func(x):
    return x*x
list(map(func, [1,2,3]))  # [1,4,9]
```

#### reduce

`reduce`把一个函数作用在一个序列`[x1,x2,x3]`上，这个函数必须接收两个参数，`reduce`把结果继续和序列的下一个元素做累积运算。例如：

```
reduce(func, [x1,x2,x3]) <=> func(func(x1,x2),x3)
```

### filter

python内建的`filter()`函数用于`筛选`序列。

`filter()`函数也是接收一个函数和一个序列，根据函数返回值是`True or False`判断保留哪些元素。例如：

```
def odd(n):
    return n%2 == 1
list(filter(odd, [1,2,3,4,5]))  # [1,3,5]
```

### sorted

排序函数`sorted()`可以用来对list进行排序。

```
sorted([10,-1,3]) # [-1,3,10]
```

`sorted()`函数也是一个高阶函数，可以传入一个`key`函数来实现自定义排序。

```
sorted([1,-10,3], key=abs) # [1,3,-10] 
```

如果要进行反向排序，可以传入`reverse=True`

```
sorted([1,-10,3], key=abs, reverse=True) # [-10,3,1] 
```

# 返回函数

函数也可以作为返回值被函数返回，并在后续代码中根据需要再进行计算。这种程序结构称为`闭包`

```
def lazy_sum(x,y):
    def sum():
        return x+y
    return sum
f = lazy_sum(1,2)
f()  # 3
```

> 注意：调用`lazy_sum()`时，每次返回的都是一个新函数，即使传入相同的参数，多次调用的结果互不影响。

### 闭包

返回的函数并不会立即执行，而是直到调用的时候才执行。

> 注意：返回闭包时返回函数不要饮用任何循环变量，或者后续会发生变化的变量。

若是一定要引用循环变量的话可以采用如下方法。

```
def count():
    def f(j)
        def g():
            return j*j
        return g
    fs = []
    for i in range(1,4):
        fs.append(f(i))
    return fs
```

# 匿名函数

```
list(map(lambda x: x * x, [1,2,3])) # [1,4,9]
```

关键字`lambda`表示匿名函数，冒号前面的`x`表示函数参数。

匿名函数只能有一个表达式，不用写`return`，返回值就是该表达式的结果。

匿名函数也是一个函数对象，也可以赋值给函数变量，再利用变量来调用函数：

```
f = lambda x:x*x
f(2) # 4
```

# 装饰器

在代码运行期间动态添加功能的方式，称之为“装饰器（Decorator）”

本质上，decorator就是一个返回函数的高阶函数。

```
def log(func):
    def wrapper(*args, **kw):
        print('call %s():', %func.__name__)
        return func(*args, **kw)
    return wrapper
```

上面的函数接收一个函数作为参数，并返回一个函数。我们借助Python的@语法，并把decorator置于函数的定义处：

```
@log
def now():
    print('2018-08-06')
<==>
now = log(now)

# call now():
# 2018-08-06
```

# 偏函数

`functools.partial`的作用就是，把一个函数的某些参数给固定住（即设置默认值），返回一个新的函数，调用这个函数就更简单了。并且固定的参数还可以继续传入其他值。

```
int2 = functools.partial(int, base=2)
<==>
def int2(x, base=2):
    return int(x, base)
```

> 创建偏函数的时候也可以传入函数对象、\*args和\*\*kw这3个参数













