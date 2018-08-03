# 函数定义

python使用`def`定义函数，例如：

```
def func1(param):
    pass

def func2(param):
    return param
```

> 没有return语句python函数也会返回结果，只不过会返回`None`。return None可以简写为return

### 返回多个值

python函数可以返回多个值，例如：

```
def func():
    x=y=1
    return x,y
x,y = func()
```

> 实际上python返回的是一个tuple

# 参数

### 普通参数

```
def func(param1, param2):
    pass
```

### 默认参数

```
def func(param=2):
    pass
```

> 默认参数必须指向不变对象！

### 可变参数

可变参数允许传入0个或任意个参数，这些参数在调用函数的时候会自动组装为一个Tuple

```
def func(*params):
    pass
```

### 关键字参数

关键字参数允许传入0个或任意个含有参数名的参数，这些关键字参数在函数内部自动组装成一个dict。

```
def person(name, **kw):
   print('name:',name, 'other:',kw)

person('yang', age=30)
输出：name:yang other:{'age':30}
```

### 命名关键字参数

命名关键字参数可以限制传入参数的名字。

命名关键字参数使用`*`分隔符，分隔符后面的参数被视为命名关键字参数。

```
def func(name, *, age, sex):
    pass
```

如果和可变参数同时使用，就不需要`*`分隔符了，可变参数之后的参数默认视为命名关键字参数

```
def func(name, *args, age, sex):
    pass
```

命名关键字参数也可以有默认值

```
def func(name, *, age=18, sex):
    pass
```

### 参数组合

python中的这五种参数可以组合使用，但是参数定义的顺序必须是：`必选参数、默认参数、可变参数、命名关键字参数、关键字参数`

```
def func(name, age=18, *args, sex, **kw):
    pass
```



